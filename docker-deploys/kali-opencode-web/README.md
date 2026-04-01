# kali-opencode-web

Kali Linux container with OpenCode web IDE for browser-based pentesting and development.

## What's Inside

| Category | Tools |
|----------|-------|
| Pentesting | nmap, netcat, whois, dig, dnsutils, net-tools |
| Development | Python 3, pip, Node.js, npm, git, build-essential |
| Browser automation | Playwright (headless Chromium), playwright-stealth, browser-use |
| Editors & utilities | vim, nano, tmux, jq, curl, wget |

## Quick Start

```bash
docker compose up -d
```

Then open [http://localhost:4096](http://localhost:4096) in your browser.

## Configuration

| Setting | Default | Notes |
|---------|---------|-------|
| Web UI port | `4096` | Change the port mapping in `docker-compose.yml` |
| Workspace | `./workspace` | Bind-mounted to `/root/workspace` in the container |

## Security Considerations

- The container runs as **root** — this is intentional for pentesting tooling.
- The web UI binds to `0.0.0.0` by default. To restrict access to your machine only, change the port mapping to `"127.0.0.1:4096:4096"`.
- The `./workspace` bind mount allows the container to read/write files on your host in that directory. Do not mount sensitive host paths.
- The OpenCode web UI has no built-in authentication. Do not expose it to untrusted networks.

## Files

- `docker-compose.yml` — Compose file with inline Dockerfile
- `INSTRUCTIONS.md` — System prompt loaded into OpenCode inside the container
