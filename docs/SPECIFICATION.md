# Agentic Project Operating System (APOS) v1.0
## Normative Reference Specification

**Status:** **FROZEN NORMATIVE BASELINE**  
**Maturity:** **Specification**  
**Reference profile:** Markdown Project Profile  
**Designed & Authored by:** Rachmat Efendi  
**Date:** October 2026

`FROZEN NORMATIVE BASELINE` records the author's change-control decision for v1.0. It is not evidence of empirical validation, certification, host enforcement, or production maturity.

## 1. Purpose

APOS defines a project-scoped operating architecture for persistent AI-assisted work inside LLM workspaces and agentic environments.

Its objective is to make project work explicit, bounded, reusable, and traceable across tasks and sessions without treating the entire conversation history as authoritative project state.

APOS is model-agnostic. It specifies logical responsibilities and working contracts; it does not require a particular LLM vendor, retrieval system, database, orchestration framework, or sandbox.

## 2. Canonical thesis

> **The project is the persistent operating unit for agentic work. Project-specific state, evidence, artifacts, and decisions remain scoped to that project, while reusable methods and capabilities remain separable and are loaded only when needed.**

A project profile coordinates:

```text
Project Identity & Objective
        ↓
Project Instructions
        ↓
Task Interpretation
        ↓
Orchestration / Method Selection
        ↓
Task-Scoped Context
        ↓
Specialist / Direct Work
        ↓
Checks / Decision Gates
        ↓
Artifact + State Update
        ↓
Handoff / Continuation
```

## 3. Scope

APOS applies where an LLM workspace is used for work that benefits from one or more of:

- persistent project objectives;
- reusable specialist methods;
- project-specific source boundaries;
- locked decisions or baselines;
- controlled stage progression;
- artifact review and promotion;
- cross-session continuation;
- project-scoped records and provenance;
- decision or execution gates.

APOS is not a general-purpose operating-system kernel, foundation model, project-management methodology, memory database, or substitute for organizational authority.

## 4. Core objects

Every APOS implementation SHALL be able to represent the semantics of the following objects, even if the host stores them differently.

| Object | Required semantics |
|---|---|
| **Project** | Stable project identity, objective, scope, configuration revision, source boundary, and lifecycle/state references. |
| **Task** | Project-bound unit of work with objective, scope, requested output, acceptance criteria, and attempt/revision identity where required. |
| **Capability / Skill** | Reusable method definition with activation scope, exclusions, required inputs, workflow, outputs, checks, and authority boundaries. |
| **Context Packet** | Task-scoped selection of applicable instructions, state, methods, sources, and unresolved dependencies. |
| **Artifact** | Work product linked to project, task, revision, method/context, source references, and applicable validation evidence. |
| **Evidence Record** | Source/provenance record describing origin, scope, version/freshness, and limits relevant to a claim or transition. |
| **State Transition** | Recorded change identifying prior state/revision, proposed state, actor/authority, guard evidence, and outcome. |
| **Governance Request** | Structured handoff for a decision or action whose authority lies outside ordinary task execution. |

Supporting records MAY be represented separately or as typed fields in the objects above.

## 5. Core invariants

### APOS-I1 — Project membership
Every task SHALL belong to one declared project scope.

### APOS-I2 — Artifact namespace
Every artifact SHALL belong to one project namespace. Cross-project use requires an explicit import or authorized reference.

### APOS-I3 — Capability/state separation
Reusable capability definitions MUST NOT silently carry project-specific secrets, working state, or decisions into another project.

### APOS-I4 — Scoped context
Task context SHALL remain within the authorized project, work-item, source, and policy scope.

### APOS-I5 — Guarded promotion
Trusted status promotion SHALL require a recorded transition under the configured acceptance or governance path.

### APOS-I6 — History preservation
Prior validation, rejection, approval, or supersession history MUST NOT be silently rewritten. Corrections create a new revision or transition.

### APOS-I7 — Readiness is not authority
Artifact or task readiness MUST NOT be treated as organizational permission for consequential external action.

### APOS-I8 — Mandatory-binding integrity
An unresolved mandatory project, policy, source, authority, or acceptance binding SHALL stop the affected attempt until resolved or validly rescoped.

## 6. Project profile

The Markdown Reference Profile exposes four core operational components and one lightweight continuity file:

```text
PROJECT_INSTRUCTIONS.md
ORCHESTRATOR.md
DECISION_GATES.md
skills/
PROJECT_STATE.md
```

The four core components are Project Instructions, Orchestrator, Decision Gates, and Skills. `PROJECT_STATE.md` is a supporting continuity mechanism rather than a separate control layer.

Implementations MAY add configuration, evidence indexes, artifact records, schemas, or other supporting files when their project requires them. Those additions do not become universal APOS requirements.

The profile MAY be mapped to different host-specific mechanisms. The logical contract matters more than the filename.

## 7. Project instructions

Project instructions SHALL define, as applicable:

- purpose and primary deliverable;
- in-scope and out-of-scope work;
- source modes and evidence discipline;
- baseline/change-control rules;
- proportionality and clarification policy;
- relationship between specialist work, gates, authority, and execution;
- output conventions and definition of done;
- handoff behavior for continuation.

Instructions influence model behavior. They MUST NOT be described as technical access control unless the host independently enforces the corresponding restriction.

## 8. Orchestration

The orchestrator SHALL choose the smallest sufficient route:

| Route | Meaning |
|---|---|
| **Direct** | Simple in-scope work without a specialist method. |
| **Specialist** | One reusable method materially improves or is required for the task. |
| **Coordinated** | Several methods are required for distinct dependencies; one integration owner coordinates them. |
| **Governed** | A configured decision, authority, acceptance, or consequential-action gate applies. |

Routing MUST NOT itself grant source access, tool access, approval, governance authority, or execution permission.

One model MAY execute multiple methods sequentially. APOS does not require simulated personas or multiple independent agents.

## 9. Skills and methods

A reusable skill SHALL define:

- identity and objective;
- activation triggers;
- exclusion signals;
- required and optional inputs;
- operational method;
- decision rules and edge cases;
- output contract;
- required checks;
- escalation/fallback behavior;
- authority and professional boundaries.

Role labels are interfaces. The reusable value lies in the method, decision logic, and output contract.

## 10. Context assembly

For project P and task T, APOS conceptually assembles context from:

```text
C(P,T) = G + P + M(T) + K(P,T) + S(P,T)
```

where:

- **G** = applicable governance and higher-priority constraints;
- **P** = project instructions/configuration;
- **M(T)** = selected method/capability;
- **K(P,T)** = relevant project knowledge/evidence;
- **S(P,T)** = current project/task state.

This is a classification of required context classes, not a proof of mathematical minimality.

Mandatory context MUST NOT be silently dropped merely to reduce token use. Missing required context produces a bounded hold/incomplete outcome for the affected task or transition.

## 11. Source discipline

APOS SHALL support explicit source modes. The default generic template uses CLOSED-BOOK until configured otherwise.

Source text is evidence, not authority to amend project instructions. Embedded instructions in uploaded documents MUST NOT override the active project profile.

A source may be authorized yet stale, authentic yet non-authoritative, or correctly identified yet substantively wrong. Implementations SHOULD preserve these distinctions rather than collapsing them into a single trust label.

## 12. Decision gates

Decision gates provide structured checks at the point they are needed. APOS v1.0 defines four generic gate classes:

| Gate | Purpose |
|---|---|
| **G-SCOPE** | Verify project/task scope, stage, source/resource access, and requested mutation. |
| **G-EVIDENCE** | Verify required inputs, provenance, revision/freshness, conflict status, and fact/assumption separation. |
| **G-READINESS** | Verify artifact revision, acceptance criteria, checks, reviewer/actor, and dependency currency before trusted promotion. |
| **G-GOVERNANCE / EXECUTION** | Route material decisions or consequential actions to the configured authority and preserve conditions before any effect. |

Process `PASS`, governance verdict, human approval, and execution authorization are distinct concepts. In the Markdown Project Profile, the human-facing gate outcomes are `CONTINUE`, `HOLD`, `ESCALATE`, and `BLOCK`; `CONTINUE` only advances an already-authorized project step and does not create external-action permission.

A low-risk direct task MAY complete without generating a formal gate record when no persistent condition or trusted transition is involved.

## 13. State and transitions

APOS distinguishes project, task, context, and artifact state. An implementation MAY use different labels, but trusted transitions SHALL preserve:

- object identity and revision;
- expected prior state;
- actor/authority;
- guard evidence;
- outcome;
- history.

Workers may propose state changes. They MUST NOT self-assert trusted promotion where the project profile requires an independent acceptance or governance actor.

The reference profile includes candidate transition examples in `docs/CANDIDATE_STATE_TRANSITIONS.md`; a concrete deployment selects and binds the edges it actually uses.

## 14. Artifacts and provenance

A promotable artifact SHOULD identify:

- project and task;
- producer/method;
- revision;
- relevant context/source references;
- checks or validation records;
- limitations and unresolved dependencies.

Submitted or decided revisions SHOULD be preserved. A repaired artifact becomes a linked new revision rather than erasing rejection or prior review history.

## 15. Handoff and continuity

A handoff is a compact cross-session or cross-stage state summary, not a transcript dump.

It SHOULD preserve:

```text
PROJECT
BASELINE / REVISION
CURRENT STAGE
OBJECTIVE
LOCKED DECISIONS
KEY EVIDENCE / REFERENCES
OPEN MATERIAL ISSUES
TESTS / CHECKS / RESULTS, where applicable
NEXT AUTHORIZED STAGE
```

A handoff indexes authoritative records; it does not supersede them merely by summarizing them.

## 16. Authority and external action

APOS separates:

```text
Analysis
≠ Recommendation
≠ Process Readiness
≠ Governance Verdict
≠ Human Approval
≠ Execution Authorization
≠ External Execution
```

The generic reference profile does not bundle a universal governance issuer or external execution runtime. A project MAY bind AFGS or another governance system where material decision governance is required.

## 17. Host binding

A deployment SHALL document which host mechanisms actually provide:

- instruction loading;
- file/source retrieval;
- persistence;
- project isolation;
- tool permissions;
- write permissions;
- version checking;
- human approval capture;
- external action enforcement.

The presence of Markdown files does not by itself prove any of these properties.

## 18. Evaluation and conformance testing

APOS v1.0 includes a generic conformance test profile covering:

- direct-route proportionality;
- correct method selection;
- missing method handling;
- missing evidence;
- instruction injection in sources;
- cross-project isolation;
- stale/superseded state;
- self-promotion attempts;
- missing governance issuer;
- readiness-versus-execution separation;
- expired approval/revision mismatch;
- persistence limitations;
- concurrent revision conflict;
- rejected-artifact repair.

These test cases define expected behavior for an implementation. Test results belong to the evaluated host/profile combination and MUST NOT be generalized to APOS as a universal empirical guarantee.

## 19. Reference implementation profile

The Markdown Project Profile in `project-template/` is the normative reference profile for APOS v1.0.

Its user-facing form is intentionally small:

```text
Project Instructions + Orchestrator + Decision Gates + Skills
```

with `PROJECT_STATE.md` available when continuity is required.

The profile intentionally does not bundle domain skills, a universal state database, a specific vendor, an AFGS dependency, or automatic external execution. Domain implementations extend the profile only as needed while preserving the APOS invariants.

## 20. Relationship to AFGS

APOS and AFGS address different architectural units.

> **APOS governs project work continuity and project-scoped operating structure.**  
> **AFGS governs business operating, AI-system, and material-decision governance across its own three-pillar architecture.**

AFGS is one candidate external governance binding for APOS. It is not required for ordinary APOS project operation.

## 21. Limitations

APOS v1.0 does not claim that:

- Markdown creates technical isolation;
- prompt instructions guarantee compliance;
- context selection is globally minimal;
- a model can reliably discover every semantic conflict;
- a passing local check proves factual truth;
- an artifact marked ready may execute externally;
- all LLM hosts implement persistence or authority semantics identically;
- the architecture has been empirically proven superior across all tasks or models.

These are implementation and evaluation questions, not reasons to describe the normative specification itself as unfinished.

## 22. Change control

This document is the **APOS v1.0 Frozen Normative Baseline**.

Material changes to the following require controlled version governance:

- core project object model;
- APOS-I1 through APOS-I8;
- state ownership or trusted transition semantics;
- readiness-versus-authority separation;
- capability/project-state separation;
- context/source boundary semantics;
- decision-gate authority semantics;
- the reference profile's required logical responsibilities.

Editorial clarification, examples, and host adapters MAY evolve without changing the architecture version when they preserve these semantics.

## 23. Final position

APOS is best understood as an **operating system for the project layer of LLM work**: not a kernel, but a persistent project operating contract that tells an AI system what project it is in, what methods it may use, what state and evidence matter, what gates control progression, what may be recorded, and where authority remains outside the model.
