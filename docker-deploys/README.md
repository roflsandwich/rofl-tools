# Docker Deploys

A library of quick, single-command dockerized instances. Each directory contains a `docker-compose.yml` and everything needed to spin up an isolated environment.

## Usage

```bash
cd docker-deploys/<deploy-name>
docker compose up -d
```

To tear down:

```bash
docker compose down -v
```

## Available Deploys

### [kali-opencode-web](kali-opencode-web/)

A Kali Linux rolling container with [OpenCode](https://opencode.ai) web IDE exposed on port `4096`. Comes pre-installed with:

- **Pentesting tools**: nmap, netcat, whois, dig, curl, wget
- **Dev tools**: Python 3, Node.js, git, build-essential
- **Browser automation**: Playwright with headless Chromium, playwright-stealth, browser-use
- **Persistent workspace**: bind-mounted `./workspace` directory survives container restarts

**Quick start:**

```bash
cd kali-opencode-web
docker compose up -d
# Open http://localhost:4096
```

**Security note:** The web UI binds to `0.0.0.0` by default (accessible on your network). To restrict to localhost only, change the port mapping in `docker-compose.yml` to `"127.0.0.1:4096:4096"`.

## Adding a New Deploy

1. Create a new directory under `docker-deploys/`
2. Add a `docker-compose.yml` (prefer `dockerfile_inline` to keep things self-contained)
3. Add a `README.md` describing the deploy, its ports, and any config
4. Update this README and the root `README.md` table
