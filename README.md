# APOS — Agentic Project Operating System v1.0

**APOS is a specification for a small set of Markdown files you place inside an LLM Project or workspace to define how the AI should work on that project.**

The practical model is simple:

```text
PROJECT
│
├── PROJECT_INSTRUCTIONS.md   → what this project is and how to work
├── ORCHESTRATOR.md           → which route or skill to use
├── DECISION_GATES.md         → when work may continue, hold, or escalate
├── skills/                   → how specialist work is performed
└── PROJECT_STATE.md          → where the project currently stands
```

**Four core parts:** Instructions + Orchestrator + Gates + Skills.  
`PROJECT_STATE.md` is a lightweight supporting file for continuity across sessions.

## What each file does

| Component | Simple meaning |
|---|---|
| **Project Instructions** | Defines the project objective, scope, source rules, working rules, and output expectations. |
| **Orchestrator** | Chooses the smallest sufficient route: direct work, one skill, several skills, or a governed path. |
| **Decision Gates** | Checks whether the AI should continue, hold for missing information, escalate for approval, or stop. |
| **Skills** | Markdown methods that define how specialized work should be done. |
| **Project State** | Keeps the current stage, locked decisions, open issues, and next step compactly available. |

## Quick start

1. Copy the contents of [`project-template/`](project-template/) into your LLM Project or workspace.
2. Edit `PROJECT_INSTRUCTIONS.md`.
3. Add the skills you actually need under `skills/`.
4. Adjust `DECISION_GATES.md` only for decisions or actions that need control.
5. Start working normally.

You do **not** need to fill every file for every task. Simple work should stay simple.

```text
simple request
    ↓
direct work
    ↓
output
```

When specialist work is needed:

```text
request
    ↓
orchestrator
    ↓
relevant skill
    ↓
output
```

When a decision gate is triggered:

```text
request
    ↓
orchestrator
    ↓
skill / analysis
    ↓
decision gate
    ├── CONTINUE*
    ├── HOLD
    ├── ESCALATE
    └── BLOCK
```

`CONTINUE` means only that the next **already-authorized project step** may proceed. It is not, by itself, permission to send, publish, sign, pay, deploy, file, or change an external system.

## Example

User:

> Review the evidence and prepare a one-page recommendation.

APOS behavior:

1. `PROJECT_INSTRUCTIONS.md` supplies the project rules.
2. `ORCHESTRATOR.md` selects the relevant review skill.
3. The skill performs the defined method.
4. `DECISION_GATES.md` is consulted only if the result is being promoted, approved, published, executed, or otherwise crosses a configured gate.
5. `PROJECT_STATE.md` is updated only if the work needs continuity.

That is APOS.

## What APOS is not

APOS is **not** a new foundation model, agent runtime, security sandbox, or project-management methodology.

Markdown instructions define intended project behavior. The actual LLM host still controls model behavior, file access, tool permissions, persistence, isolation, and external actions.

## Repository structure

```text
.
├── README.md
├── LICENSE
├── CITATION.cff
├── CHANGELOG.md
│
├── project-template/          ← copy this into your LLM Project
│   ├── PROJECT_INSTRUCTIONS.md
│   ├── ORCHESTRATOR.md
│   ├── DECISION_GATES.md
│   ├── PROJECT_STATE.md
│   └── skills/
│       └── SKILL_TEMPLATE.md
│
├── examples/
│   └── MINIMAL_FLOW.md
│
└── docs/                     ← optional: for architects/researchers
    ├── SPECIFICATION.md
    ├── ARCHITECTURE.md
    ├── CONFORMANCE.md
    └── AFGS_RELATIONSHIP.md
```

**Most users only need `project-template/`.**

## Status

**Version:** 1.0  
**Type:** Public specification baseline  
**Reference profile:** Markdown Project Profile  
**Designed and authored by:** Rachmat Efendi

APOS v1.0 is the published specification baseline. This does **not** mean that every LLM host has been tested, validated, or technically enforces every APOS rule.

For the formal architecture and invariants, see [`docs/SPECIFICATION.md`](docs/SPECIFICATION.md).

## Citation and rights

Citation metadata is in [`CITATION.cff`](CITATION.cff). Reuse terms are in [`LICENSE`](LICENSE).
