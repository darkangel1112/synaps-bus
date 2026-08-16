# SynapsBus

**Agent collaboration middleware** — provider-agnostic, platform-agnostic.

SynapsBus is a standalone, open-source middleware layer that enables structured communication between AI agents. It works alongside Hermes, Synaps, or any other agent framework — none are required.

## What it does

- **Direct Messages** — async 1:1 agent-to-agent messaging ("internal email")
- **Debate Rooms** — structured multi-agent discussion with rounds, moderator, and loop protection
- **Project Rooms** — persistent workflow rooms with context, status tracking, and parallel work support
- **HITL Layer** — human-in-the-loop: observe, interrupt, or inject into any room at any time
- **Web Dashboard** — live feed, trace view, agent status, full audit trail

## What it is NOT

Not an agent runtime. Not a model provider. It only handles the communication layer.

## Architecture

```
SynapsBus
├── Message Bus      ← SQLite, async, trace/span
├── Room Engine      ← Debate Room, Project Room
├── Rules Engine     ← trust, permissions, loop protection
├── Web Dashboard    ← live feed, trace view, HITL
└── Adapters         ← Hermes plugin, Synaps TS, generic HTTP
```

## Permission levels

| Level | Examples | Can open rooms |
|-------|----------|----------------|
| Owner | Human user | Yes (all) |
| CEO | Nova | Yes (all) |
| Team Lead | Prometheus, Atlasz | Yes (own team) |
| Worker | Forge, Vega, Argus, Lynx | No |

## Quick start

```bash
# Linux
./install_linux.sh

# Windows
.\install_windows.ps1

# Manual
pip install -r requirements.txt
cp .env.example .env
# Edit .env
python bus_server.py
```

## Tech stack

- Python 3.10+
- FastAPI + uvicorn
- SQLite (zero external dependencies)
- Static HTML/JS dashboard (no framework)

## License

MIT

## Spec

Full system specification: [SPEC.md](SPEC.md)
