# ARI

**A personal AI whose memory is mine: the models are interpreters, the vault is the assistant.**

![ARI's knowledge graph: every note and link in the vault that ARI runs on](media/ari-vault-graph.jpg)

*This is ARI: the vault of notes and links the assistant thinks with. Models plug into it; extensions like a wearable display and a robot plug into it too.*

ARI is a single-user personal assistant built around one idea: the durable part of an AI assistant should be owned by the person, not by whichever model happens to be running today. Models come and go; the memory, the rules and the track record stay.

## What it does

- **One assistant, many extensions.** Chat and voice day to day; extensions such as a wearable display, a desk deck and a [hexapod robot](https://github.com/evilhobo1911/hexapod-rl) all connect to the same assistant and memory.
- **Memory with provenance and human approval.** Memories captured automatically from conversations carry a recorded source and need a human sign-off before they are filed. Ambiguous items are blocked, not guessed.
- **Coding agents measured against acceptance checks.** Each job is judged against defined checks, not the agent's own report, and the recorded verdict separates a pass, a pass with a scope violation, and a failure.
- **Model-agnostic.** ARI lives in the Obsidian vault, not in any one model. Each runtime connects to the vault directly: Hermes Agent, Claude Code and a Gemini-based runtime have all run as ARI, independently of each other.

![Wearable display: the assistant describing what the camera sees](media/wearable-assistant.jpg)

*Extension: the wearable display. The assistant looks through the camera and comments on the scene (an earlier robot build is on the monitor). This older capture also shows a context-limit warning.*

## Results

As of 2026-10-21:

| Area | Result |
|---|---|
| Coding agents | 610 jobs run; 255 have a recorded verdict and 355 have none in this snapshot. Of the 255: 65% pass, 18% pass with scope violation, 17% fail |
| Memory | 330 proposals: 259 applied, 13 rejected, 41 pending, 17 ambiguous blocked rather than guessed |
| Knowledge base | 563 notes |
| Activity | ~2,000 agent sessions and 9.5k tool calls over 90 days |
| Uptime | Gateway uptime at the 2026-10-21 snapshot: 9.5 days, 0 restarts |

The coding-agent verdict split is the point: the system reports failures and scope violations honestly rather than rounding everything up to success.

## Overview

```mermaid
flowchart LR
    S[Surfaces<br/>chat / voice / wearable / desk deck] --> R[Assistant runtime]
    R --> T[Tools]
    T --> V[(Vault: the durable memory)]
    V --> R
```

## Status and honest scope

ARI is a single-user personal system, not a product. Some components are paused: the initiative engine is unscheduled and the Gemini runtime bridge is stopped, and the numbers above come from one person's real usage, not a benchmark.

## Open-source companion

[obsidian-agent-runtime](https://github.com/evilhobo1911/obsidian-agent-runtime) is the open companion: vault search, working-context injection and Claude Code integration. ARI's approval pipeline and coding-agent harness are not included.

## Credits

Built on and with: Hermes Agent, Claude Code, Codex, Chatterbox, and Obsidian.

Source is private.
