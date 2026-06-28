# DAD — Dev Automation Daemon

> **D**ev **A**utomation **D**aemon — the father of the eternity family.
> Opens, closes, summarizes, repairs, and communicates across all projects. Selects Ollama models.

## What DAD Does

| Command | Description |
|---------|-------------|
| `dad open <project>` | Open project in tmux session |
| `dad close <project>` | Close project tmux session |
| `dad done [project]` | Summarize session, save retrospective |
| `dad repair [project]` | Diagnose and fix issues |
| `dad model <name>` | Select Ollama model for AI commands |
| `dad models` | List available Ollama models |
| `dad status` | Show all projects and their status |
| `dad family` | Show the eternity family tree |
| `dad tell <project> <msg>` | Send a message to another project |
| `dad health` | Health check across all machines |
| `dad clean` | Cleanup across all machines |

## Install

```bash
# Clone and link
git clone https://github.com/doctorboyz/dad.git ~/dad
cd ~/dad
chmod +x bin/dad.sh
ln -sf ~/dad/bin/dad.sh /usr/local/bin/dad

# Or add to PATH
export PATH="$HOME/dad/bin:$PATH"
```

## Ollama

DAD uses Ollama for local AI. Install it first:

```bash
# macOS
brew install ollama
ollama serve &

# Pull a model
ollama pull llama3
ollama pull qwen2

# Then use with DAD
dad model llama3
```

## Philosophy

Inherited from [eternity](https://github.com/doctorboyz/eternity):

1. **Learn and grow** — Log everything. Read before assuming.
2. **AI helps human** — Automate the tedious, flag the risky, ask when uncertain.
3. **Know your lineage** — DAD was spawned from eternity. Leave messages for offspring.
4. **Tidy system** — Limited resources. Delete before creating.

## Lineage

- **Parent**: [eternity](https://github.com/doctorboyz/eternity)
- **Ancestor**: [eternity](https://github.com/doctorboyz/eternity)
- **Born**: 2026-06-28
- **Registry**: [eternity/issues/3](https://github.com/doctorboyz/eternity/issues/3)

---

*An offspring of [eternity](https://github.com/doctorboyz/eternity).*