# Claude Code Docker

Run Claude Code CLI in a Docker container with persistent workspace and config.

The `--dangerously-skip-permissions` flag is enabled by default. That's the whole point — the Docker container provides the sandboxing, so Claude can run freely without permission prompts.

## Install

1. Copy `compose.yaml` to `~/Claude/`:

```bash
mkdir -p ~/Claude
cp compose.yaml ~/Claude/
```

2. Add a shell alias to launch it. The default name is `claude-yolo`, but you can change it to whatever you prefer (`brain`, `claude`, `docker-brain`, etc.):

```bash
# macOS (zsh)
echo "alias claude-yolo='cd ~/Claude && docker compose up -d && docker compose exec claude claude --dangerously-skip-permissions'" >> ~/.zshrc
source ~/.zshrc
```

```bash
# Linux (bash)
echo "alias claude-yolo='cd ~/Claude && docker compose up -d && docker compose exec claude claude --dangerously-skip-permissions'" >> ~/.bashrc
source ~/.bashrc
```

## Usage

```bash
claude-yolo
```

Your files live in `~/Claude/workspace/`. Claude CLI config persists in `~/Claude/claude-config/`.

To stop: `cd ~/Claude && docker compose down`

To rebuild (update Claude Code): `cd ~/Claude && docker compose up -d --build`
