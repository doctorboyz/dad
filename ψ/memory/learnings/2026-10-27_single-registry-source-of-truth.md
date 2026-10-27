# Learning: project registry must have ONE source of truth (2026-10-27)

## Problem

`dad open silicon` failed with "Unknown project" — even though silicon was registered in `config/projects.yaml` and `eternity/inventory/projects.md`. Reason: `bin/dad` hardcoded the same registry **a third time** in `project_path()` (case/esac) and `project_list()`, plus a fourth stale copy in `cmd_family()`'s tree. The hardcoded list had drifted before (it was also missing `plaud`). Related bug: the main dispatcher used `return 1` at top level — bash 3.2 rejects that ("return: can only `return` from a function or sourced script").

## Root cause

Three copies of one fact. Updating a project list in one place (YAML) silently left the others stale.

## Fix

- `project_path` / `project_list` / `cmd_family` now all parse `config/projects.yaml` via `ruby -ryaml` (ruby ships with macOS; no new deps)
- bash 3.2 compatible: no associative arrays, no `declare -A` (see [[bash-compat-and-trust-dialog]])
- dispatcher `return 1` → `exit 1`

## Rule

**Never hardcode a project in `bin/dad`.** Add it to `config/projects.yaml` only — every command reads from there. If a new project doesn't show up in `dad status`, check the YAML, not the script.

**Why:** a fact stored in N places is wrong in N−1 of them eventually.

**How to apply:** when spawning a project (see eternity's `/spawn`), the registry update step is `dad/config/projects.yaml` — nothing else in dad needs touching.