# .github

Org defaults and administration source for JorisJonkers-dev repositories.

## What It Is

This repository owns the org profile, default issue and pull request templates,
default security and contribution policy, label taxonomy, and owner-gated
Project #2 administration workflow.

## Automation

- `labels.yml` is the additive org label source.
- `.github/workflows/label-sync.yml` applies labels across active org repos.
- `.github/workflows/project-board-admin.yml` verifies, configures, and
  backfills Project #2 when an org-scoped Project token is available.

Project board writes are owner-gated. Configure
`ORG_AUTOMATION_APP_ID`/`ORG_AUTOMATION_APP_PRIVATE_KEY` with org Projects
write permission, or provide `ORG_PROJECT_PAT` as the fallback secret before
running the admin workflow.

The reusable auto-add implementation belongs in
`JorisJonkers-dev/github-workflows`; product repositories should call that
workflow rather than adding a second Project auto-add path here.

## Links

- [Organization profile](https://github.com/JorisJonkers-dev)
- [Project #2](https://github.com/orgs/JorisJonkers-dev/projects/2)
- [Security policy](https://github.com/JorisJonkers-dev/.github/security/policy)
- [Changelog](./CHANGELOG.md)
- [License](./LICENSE)

Copyright (c) Joris Jonkers. Source available for viewing only; use, copying,
modification, redistribution, deployment, or reuse is not licensed. See
[LICENSE](./LICENSE).
