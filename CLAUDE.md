# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What Is DAD?

**DAD** — **Dev Automation Daemon** — is a CLI tool that orchestrates the eternity family. It opens, closes, summarizes, repairs, and communicates across all projects on this machine and the Tailscale network, with local AI via Ollama model selection.

**DAD is the father of the family.** It manages sessions, monitors health, selects models, and keeps everything running smooth.

## Philosophy

Inherited from [eternity](https://github.com/doctorboyz/eternity). Read [`PHILOSOPHY.md`](PHILOSOPHY.md) first.

Key principle for DAD: **Rule 2 — AI Helps Human**. DAD automates the tedious so the human can focus on decisions. DAD never decides for you — it suggests, executes, and remembers.

## Commands

```bash
dad open <project>       # Open project in tmux session
dad close <project>      # Close project tmux session
dad done [project]       # Summarize session, save to ψ/memory/retros/
dad repair [project]     # Diagnose and fix issues
dad model [name]         # Select Ollama model
dad models               # List available Ollama models
dad status                # Show all projects and their status
dad family                # Show the eternity family tree
dad tell <project> <msg> # Send a message to another project's memory
dad health                # Run health check across all machines
dad clean                 # Run cleanup across all machines
```

## Architecture

```
dad/
├── bin/
│   └── dad.sh              # CLI entry point
├── src/
│   ├── commands/
│   │   ├── open.sh         # dad open <project>
│   │   ├── close.sh        # dad close <project>
│   │   ├── done.sh         # dad done [project]
│   │   ├── repair.sh       # dad repair [project]
│   │   ├── model.sh        # dad model [name]
│   │   ├── models.sh       # dad models
│   │   ├── status.sh       # dad status
│   │   ├── family.sh       # dad family
│   │   ├── tell.sh         # dad tell <project> <msg>
│   │   ├── health.sh       # dad health
│   │   └── clean.sh        # dad clean
│   ├── lib/
│   │   ├── config.sh       # Load project config
│   │   ├── ollama.sh       # Ollama integration
│   │   ├── tmux.sh         # Tmux session management
│   │   └── memory.sh       # Read/write ψ/ memory vault
│   └── dad.sh              # Main dispatcher
├── config/
│   └── projects.yaml       # Project registry (synced with eternity)
├── ψ/
│   ├── IDENTITY.md
│   ├── PURPOSE.md
│   └── memory/
├── PHILOSOPHY.md
├── CLAUDE.md
├── README.md
└── .gitignore
```

## Project Registry

DAD reads from `config/projects.yaml` which mirrors `eternity/inventory/projects.md`. Each project entry includes:

- name, path, github, parent, description
- tmux session name
- default Ollama model (if configured)

## Ollama Integration

DAD requires Ollama for local AI model selection. Commands that need AI (summarize, repair, tell) use the currently selected model:

```bash
dad model llama3        # Switch to llama3:8b
dad model qwen2         # Switch to qwen2:7b
dad model codellama     # Switch to codellama
dad models              # List available models
```

If Ollama is not running, `dad model` will start it.

## Machines

DAD can operate across the Tailscale network:

- **macbook** — primary dev (local)
- **macmini** — secondary compute (ssh macmini)
- **vpsdeluna** — production VPS (ssh vpsdeluna)

## Related Projects

- **eternity** (`~/eternity`) — Parent meta-repository
- **infra** (`~/infra`) — Infrastructure management (sibling)
- **S45** (`~/Desktop/S45`) — Hospital OR system
- **deluna-crm** (`~/Desktop/deluna-crm`) — Clinic management
- **deluna-mini** (`~/deluna-mini`) — Lightweight clinic