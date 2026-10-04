# Minimal APOS Flow

This is an illustrative flow, not a host test result.

## Project setup

The project contains:

```text
PROJECT_INSTRUCTIONS.md
ORCHESTRATOR.md
DECISION_GATES.md
PROJECT_STATE.md
skills/
  research-review.md  ← included at examples/skills/research-review.md
```

## Request

> Review the attached materials and produce a one-page recommendation.

## Expected route

```text
PROJECT_INSTRUCTIONS
        ↓
ORCHESTRATOR
        ↓
research-review skill
        ↓
one-page recommendation
```

No formal gate is required merely because a specialist skill was used.

If the user then says:

> Publish this externally.

the configured execution/publication gate becomes relevant. This example uses the included synthetic skill [`examples/skills/research-review.md`](skills/research-review.md):

```text
recommendation
    ↓
DECISION_GATES
    ↓
required human/owner approval?
    ├── yes + present → CONTINUE*
    └── missing       → HOLD / ESCALATE
```

`CONTINUE` here means only that the next already-authorized project step may proceed. It does not itself authorize external publication or any other external action.

The point is simple: **skills define how to work; gates define when work may move into a controlled decision or action.**
