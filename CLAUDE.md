# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

デジスク研修DS実践コース用のPython開発環境。uv パッケージマネージャーを使用し、pandas, scikit-learn, matplotlib 等のデータ分析ライブラリを統合。Windows 11 + VS Code 環境で動作。

## Common Commands

```bash
# Package management (uv)
uv add <package>              # Add a dependency
uv add --dev <package>        # Add dev dependency
uv sync                       # Install dependencies from pyproject.toml
uv run python <script>        # Run a Python script

# Code quality (ruff)
uv run ruff check .           # Run linter
uv run ruff format .          # Format code

# Jupyter
uv run jupyter lab --no-browser

# Testing
uv run pytest

# Cleanup (remove Python cache files)
find . -type d -name "__pycache__" -exec rm -rf {} + 2>/dev/null; find . -type f -name "*.pyc" -delete 2>/dev/null
```

## Project Structure

- `main.py` - Entry point
- `notebooks/` - Jupyter notebooks (研修演習用)
- `inputs/` - Input data files (master, meta, option, 仕様書)
- `.claude/` - Claude Code project settings

## Configuration Files

- `pyproject.toml` - Python dependencies and ruff configuration
- `.claude/settings.json` - Claude Code permissions
- `.claude/mcp.json` - MCP server configurations

## MCP Servers Available

| Server | Purpose |
|--------|---------|
| textlint | Japanese text proofreading |
| context7 | Latest library documentation lookup |
| playwright | Browser automation |
| sequential-thinking | Complex task decomposition |

## Code Style

- Python 3.11 compatible
- Line length: 120 characters
- Uses ruff for linting and formatting
- Lint rules: E, F, I, W (with F401/F403 ignored)
- Indent: 4 spaces
- isort: first-party = ["src"]

## Permission Policy

Development commands are auto-approved via `Bash(*)`. The following are explicitly DENIED:

| Category | Denied Patterns |
|----------|----------------|
| Filesystem destruction | `rm -rf /`, `dd`, `mkfs` |
| Destructive git | `push --force`, `push -f`, `reset --hard` |
| Docker destruction | `docker rm`, `docker system prune`, `docker rmi` |
| Network commands | `curl`, `wget` (requires confirmation each time) |

MCP tools (textlint, context7, playwright, sequential-thinking) are also auto-approved.
