# DECISION GATES

Decision gates are **exceptions, not the default workflow**. Do not run formal gate logic for simple formatting, summarization, brainstorming, or other low-risk reversible tasks.

A gate is used only when one of the configured triggers below applies.

## Gate outcomes

- **CONTINUE** — required conditions are satisfied for the next **already-authorized project step**. `CONTINUE` is not, by itself, permission to send, publish, sign, pay, deploy, file, transfer value, or mutate an external system.
- **HOLD** — required information or a resolvable prerequisite is missing.
- **ESCALATE** — a human, owner, specialist, or external authority must decide.
- **BLOCK** — the requested path is prohibited or cannot proceed under the current rules.

## G1 — Scope Gate

Trigger when the request would:
- materially expand project scope;
- change a locked baseline;
- import unrelated project state;
- use a source/tool outside the permitted boundary.

If unresolved: `HOLD` or `ESCALATE`.

## G2 — Evidence Gate

Trigger when a material conclusion depends on evidence that is missing, stale, conflicting, or outside the allowed source set.

If the missing item can change the conclusion: `HOLD`.

Do not fill a material evidence gap by guessing.

## G3 — Readiness Gate

Trigger before an artifact is treated as:
- final;
- validated;
- approved;
- accepted;
- ready for a downstream controlled stage.

Check the acceptance criteria actually defined for that artifact or task.

A successful review means the artifact passed that review. It does not automatically create organizational approval.

## G4 — Decision / Approval Gate

Trigger when the project requires a decision from a named human, committee, professional, governance module, or other authority.

The AI may prepare the decision package. It must not invent the decision issuer or approval.

If required authority is absent: `ESCALATE`.

## G5 — Execution Gate

Trigger before consequential external action such as:
- sending or publishing externally;
- signing;
- filing;
- paying or transferring value;
- deploying to production;
- changing external systems or records.

A good analysis, completed artifact, or prior review is not automatically execution permission.

If explicit execution authority is not established: `HOLD` or `ESCALATE`.

## Project-specific gates

Add only gates that this project actually needs:

- [GATE NAME] — [TRIGGER] → [REQUIRED CONDITION / AUTHORITY]
- [GATE NAME] — [TRIGGER] → [REQUIRED CONDITION / AUTHORITY]
