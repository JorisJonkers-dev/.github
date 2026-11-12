# Agents

Guidance for any coding agent working in this repository. It holds the org defaults: profile, issue and pull request templates, security and contribution policy, and the label taxonomy.

The repo's agent contract is [CLAUDE.md](CLAUDE.md); the estate-wide conventions are at https://github.com/JorisJonkers-dev/workspace/blob/main/CLAUDE.md.

## Build and test

Nothing builds here. Labels are defined in `labels.yml` and applied by `.github/workflows/label-sync.yml`; the org profile is `profile/README.md`. CI lints the workflows with `actionlint .github/workflows/*.yml`.
