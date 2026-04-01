# CLAUDE.md

This repo is **rofl-tools**, a collection of utilities with a focus on quick Docker deploys.

## Repo Structure

```
rofl-tools/
  docker-deploys/          # Library of single-command dockerized environments
    kali-opencode-web/     # Kali Linux + OpenCode web IDE
      docker-compose.yml   # Compose file (inline Dockerfile)
      INSTRUCTIONS.md      # System prompt for OpenCode inside the container
      README.md            # Deploy-specific docs
    README.md              # Docker deploys overview and usage guide
  CLAUDE.md                # This file
  README.md                # Repo overview
```

## How Docker Deploys Work

Each subdirectory under `docker-deploys/` is a self-contained environment. Users just `cd` into one and run `docker compose up -d`. The Dockerfiles are inlined in the compose files to keep each deploy as a single directory with no external build context dependencies.

## Common Tasks

### Spawning kali-opencode-web

```bash
cd docker-deploys/kali-opencode-web
docker compose up -d
# Web UI at http://localhost:4096
```

### Adding a new Docker deploy

1. Create a new directory under `docker-deploys/`
2. Add a `docker-compose.yml` with `dockerfile_inline` for self-containment
3. Add a `README.md` describing the deploy
4. Update `docker-deploys/README.md` and the root `README.md` table

### Security review checklist for new deploys

- No secrets or API keys in compose files
- Ports bound to `127.0.0.1` where possible, or documented if bound to `0.0.0.0`
- Resource limits set where appropriate
- Bind mounts scoped to the deploy directory only
