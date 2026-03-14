# CLAUDE.md — Prompt Apps

This directory is for prompt engineering experiments, Claude API apps, and AI tooling.
Global settings in `~/.claude/CLAUDE.md` apply here too.

## Purpose

Building and iterating on Claude-powered apps, prompt templates, skills, and automation tools.

## Stack

- **Python** (Anaconda) for scripts and API integrations
- **Anthropic SDK** (`@anthropic-ai/sdk` or `anthropic` Python package)
- **Node.js / HTML** for any frontend tooling
- **Claude Code skills** for reusable agent workflows

## Conventions

- Default model: `claude-sonnet-4-6`; use `claude-opus-4-6` for complex reasoning tasks
- Store API keys in `.env` files — never hardcode, never commit
- Each app or experiment gets its own subdirectory
- Use `SKILL.md` for any Claude Code skills developed here

## Common Commands

```bash
# Run a Python script
conda activate base && python script.py

# Install a Python package
conda install <package> OR pip install <package>  # within active env only

# Check installed node packages
npm list --depth=0
```
