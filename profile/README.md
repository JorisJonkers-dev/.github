# JorisJonkers-dev

Self-hosted platform and agent stack powering **[jorisjonkers.dev](https://jorisjonkers.dev)**.
Source-available — © Joris Jonkers Both. All rights reserved.

### Platform & deploy
- **deploy-config-schema** — typed deployment schema + compiler (Kubernetes / Traefik / VSO / Gatus / Flux)
- **platform-blueprints** — reusable platform packs (edge, observability, NVIDIA, Flux core)
- **nix-platform** — parameterized Nix modules & host profiles
- **github-workflows** · **gradle-conventions** · **openapi-client-gradle** · **repo-template** — shared CI & scaffolding

### Libraries
- **kotlin-spring-commons** · **vue-web-commons** · **authz-model** · **api-contract-checks**

### Apps
- **agents-api** · **agents-ui** — agent platform
- **auth-api** · **auth-ui** — authentication
- **knowledge** — knowledge base & MCP endpoint
- **home-portal** — landing portal
