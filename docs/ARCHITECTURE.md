# APOS v1.0 — Architecture

## The simple model

APOS has four operational components:

```text
PROJECT INSTRUCTIONS
        │
        ▼
   ORCHESTRATOR
        │
        ├──────────────► SKILL(S)
        │                   │
        └──────────────► DECISION GATE
                            │
                            ▼
                         OUTPUT
```

A lightweight `PROJECT_STATE.md` supports continuity across sessions.

## Responsibilities

| Component | Owns |
|---|---|
| Project Instructions | project purpose, scope, source rules, working rules |
| Orchestrator | route and method selection |
| Skills | specialist methods |
| Decision Gates | conditions for continuation, hold, escalation, or block |
| Project State | compact durable state for continuation |
| Host | actual model, tools, file access, persistence, permissions, isolation, external execution |

## Core separation

APOS keeps these distinct:

```text
method selection ≠ authority
review ≠ approval
readiness ≠ execution permission
project state ≠ conversation history
Markdown rule ≠ host enforcement
```

## Progressive disclosure

Most users should start with the five files under `project-template/`.

The formal specification exists for architects, researchers, and implementers who need the object model, invariants, state semantics, evaluation profile, or governance integration details.
