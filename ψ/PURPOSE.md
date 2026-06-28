# Purpose

## What

Dev Automation Daemon — CLI that orchestrates the eternity family: open/close projects, summarize sessions, repair issues, communicate across machines, and select Ollama models for local AI.

## For Whom

The human (doctorboyz/s.adisorn) and all AI agents on this machine. DAD is the father of the family — it manages, monitors, and maintains.

## Success Criteria

- [x] `dad open <project>` opens tmux sessions with correct working directory
- [x] `dad close <project>` closes tmux sessions cleanly
- [x] `dad status` shows all projects and machine connectivity
- [x] `dad family` displays the family tree
- [x] `dad model <name>` selects Ollama model
- [x] `dad models` lists available models
- [x] `dad tell <project> <msg>` sends messages between projects
- [x] `dad health` checks all machines
- [x] `dad clean` runs cleanup
- [x] `dad done` creates retrospective templates
- [ ] AI-powered repair using selected Ollama model
- [ ] AI-powered session summarization
- [ ] `dad repair` with automatic diagnosis
- [ ] Remote commands on macmini/vpsdeluna
- [ ] Scheduled health monitoring (cron/launchd)