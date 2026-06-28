# .github

Org defaults for **JorisJonkers-dev**: reusable workflows, starter workflow
templates, and community-health files shared across every repository.

## Auto-add issues & PRs to the Planboard

Every issue and pull request opened in a JorisJonkers-dev repo is automatically
added to the shared Project (v2) board. The design has three independent
levers:

1. **Credential = GitHub App** (no PATs). A short-lived (~1h) installation
   token is minted per run via `actions/create-github-app-token`, matching the
   house pattern of minting short-lived scoped tokens rather than storing
   long-lived secrets.
2. **Logic = one reusable workflow**, here: `.github/workflows/add-to-project.yml`
   (`workflow_call`). Single source of truth.
3. **Distribution = starter template + backfill.** A small per-repo *caller*
   wires the triggers and calls the reusable workflow. New repos inherit it;
   existing repos get a one-time backfill PR. (The caller starter template is
   added in a follow-up PR, pinned by commit SHA to this reusable workflow on
   `main`.)

```
any repo: issue/PR opened
        │ on: issues / pull_request
        ▼
  caller workflow (per repo)  ──workflow_call──▶  reusable workflow (.github)
                                                    1. mint App token (owner: JorisJonkers-dev)
                                                    2. actions/add-to-project
                                                          ▼
                                                  Planboard Project (v2)
```

### Required secrets

Set once at the account level (Settings → Secrets and variables → Actions),
visible to all repositories so callers can use `secrets: inherit`:

| Secret | Value |
|---|---|
| `PLANBOARD_APP_ID` | the GitHub App's numeric App ID |
| `PLANBOARD_APP_PRIVATE_KEY` | full contents of the App's `.pem` (incl. BEGIN/END lines) |

### App permissions

- **Projects: Read and write** — the critical one; the default `GITHUB_TOKEN`
  is repo-scoped and cannot write Projects.
- **Metadata: Read-only** — mandatory minimum.
- Installed on **all repositories** so new repos are covered automatically.

> The Planboard is an **org** project
> (`https://github.com/orgs/JorisJonkers-dev/projects/1`). `actions/add-to-project`
> accepts org project URLs; confirm the App token has rights to write the
> org-owned Project v2.

### Pinning

Third-party actions are pinned by commit SHA for supply-chain hygiene; the
caller will pin the reusable workflow by SHA too. Bumps flow through Renovate
as reviewable PRs.
