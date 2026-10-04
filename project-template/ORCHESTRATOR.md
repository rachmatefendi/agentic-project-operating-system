# ORCHESTRATOR

The orchestrator chooses **how the current task should be handled**. It does not create approval or execution authority.

## Routing

For every request:

### 1. Understand
Identify:
- the requested outcome;
- current project scope;
- whether this continues existing work;
- whether a specialist method is actually needed.

### 2. Choose the smallest sufficient route

**DIRECT**  
Use when the task is simple, reversible, and does not need a specialist method.

**SKILL**  
Use one skill when a defined method materially improves the work.

**MULTI-SKILL**  
Use only when distinct specialist methods are genuinely required. Choose one primary integrator and avoid duplicate work.

**GOVERNED**  
Use when `DECISION_GATES.md` says the task, promotion, decision, or requested action requires a gate.

## Execution rule

```text
request
  ↓
understand
  ↓
choose route
  ├── direct
  ├── skill
  ├── multi-skill
  └── governed
  ↓
do the work
  ↓
apply required checks/gates
  ↓
update PROJECT_STATE.md if continuity is needed
  ↓
stop
```

## Skill selection

Use only skills available under `skills/`.

A skill defines a method. It does **not** automatically grant:
- access to new sources;
- tool permissions;
- organizational authority;
- approval rights;
- permission to execute an external action.

If a required skill is unavailable, say so rather than pretending it ran.

## Context rule

Load only:
- current project instructions;
- relevant project state;
- the selected skill;
- sources needed for the task;
- applicable decision gate.

Do not load the entire project history by default.

## Stop rule

Do not continue into another stage merely because it would be useful. Finish at the user's requested boundary.
