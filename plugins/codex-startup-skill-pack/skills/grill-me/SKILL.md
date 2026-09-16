---
name: grill-me
description: Use when pressure-testing a project, interrogating requirements, clarifying product behavior before implementation, validating a feature direction before coding, resolving product assumptions, or defining roles, permissions, ownership, workflows, metrics, lifecycle, success criteria, and scope.
---

# Grill Me

Turn a fuzzy project or feature direction into an explicit product contract before implementation begins. Interrogate product and architecture decisions conversationally so downstream agents do not silently invent behavior while coding.

## Non-negotiable rules

- Do not modify project files during the questioning phase.
- Do not implement features, write migrations, refactor code, change schemas or permissions, create APIs, or generate production components.
- Ask exactly one question at a time.
- Do not agree merely to keep the conversation moving. Challenge ambiguity, contradictions, and risky assumptions.
- Continue until an implementation agent should not need to make major product decisions independently.

## Understand the project first

Inspect only the minimum repository context needed to ask intelligent questions. Use this order:

1. `AGENTS.md`
2. Project context files directly relevant to the request
3. Focused repository searches
4. Targeted file reads

Do not recursively read the entire repository. Treat existing code as evidence, not necessarily as the product specification.

If current behavior conflicts with the user's desired behavior:

1. Surface the conflict.
2. Briefly explain the current behavior and its evidence.
3. Ask which behavior should be authoritative.

## Run the interrogation

Start with the question whose answer removes the greatest amount of uncertainty. After every answer:

1. Decide whether it is specific enough to become a requirement.
2. Challenge vague or contradictory language.
3. Compare it with earlier answers and relevant existing behavior.
4. Track confirmed decisions, assumptions, preferences, and unresolved questions separately.
5. Ask the next single, highest-value question.

Do not ask low-value questions merely to be exhaustive. Prioritize answers that materially affect architecture, data models, workflows, permissions, business rules, or implementation scope.

Treat phrases such as “obviously,” “normally,” “probably,” “admins can handle it,” “we can figure that out later,” “it should just work,” “same as before,” and “whatever makes sense” as possible hidden requirements. Clarify them whenever they could alter implementation.

## Pressure-test the product model

Cover the areas relevant to the project, adapting the order to the user's answers.

### Target user and journey

Clarify the primary user, their problem, excluded users, primary journey, and definition of success.

### Roles and permissions

Identify member, admin, owner, reviewer or approver, and any additional roles. Replace vague statements such as “admins can manage projects” with explicit permissions for viewing, creating, editing, approving, rejecting, archiving, deleting, assigning, and transferring each important object.

### Ownership and accountability

Define what ownership means, who owns each object, whether ownership can change or be shared, who is accountable for progress, and what happens when an owner becomes inactive.

### Lifecycle

Treat lifecycle behavior as a state machine where appropriate. For each meaningful state, define:

- Meaning
- Entry and exit criteria
- Actors permitted to enter it
- Valid next states
- Prohibited transitions
- Reversibility

### Dashboard metrics

For each important metric, determine its exact definition, calculation, source, time period, audience, purpose, and intended decision or action. Challenge vanity metrics and ambiguous measurements.

### Workflows

Trace important actions end to end: starting conditions, actors, actions, handoffs, approvals, failures, and completion conditions.

### Business rules and success criteria

Identify invariants that must hold regardless of UI. Define what makes the feature successful, when each workflow is complete, the measurable outcome, and the acceptance criteria implementation will need.

### Scope

Separate:

- In scope now
- Explicitly out of scope
- Future considerations that should not unnecessarily shape today's architecture

## Stop condition

Do not stop after an arbitrary number of questions. Stop only when the important ambiguities have been resolved and downstream planning can proceed without silently choosing product behavior.

## Produce the product contract

When questioning is complete, present these sections in order:

1. **Product Definition** — primary user, core problem, primary journey, and success definition.
2. **Roles & Responsibilities** — purpose, responsibilities, allowed actions, and prohibited actions for every role.
3. **Ownership Model** — owner, accountability, contributors, transfers, and inactive-owner behavior.
4. **Lifecycle** — every status, its definition, entry and exit criteria, permitted actor, and next states; include a concise state flow when useful.
5. **Dashboard Metrics** — name, definition, calculation, source, period, audience, and intended decision; flag poorly defined metrics.
6. **Permissions Matrix** — a concise role-by-action matrix.
7. **Core Workflows** — agreed end-to-end flows.
8. **Business Rules** — application invariants and enforceable rules.
9. **Scope** — in scope now, explicitly out of scope, and future considerations.
10. **Confirmed Decisions** — a numbered list precise enough to become implementation requirements.
11. **Remaining Open Questions** — only unresolved questions that materially affect implementation.
12. **Contradictions / Risks** — conflicts, ownership or permission gaps, workflow gaps, unclear metrics, risky assumptions, and inconsistencies with existing behavior.
13. **Implementation Readiness** — finish with exactly one of the following status lines:

```text
READY FOR IMPLEMENTATION
```

or:

```text
NOT READY FOR IMPLEMENTATION
```

If not ready, state the specific unresolved decisions blocking implementation. If ready, give a high-level recommended implementation sequence without beginning implementation.

The final product contract governs downstream planning. If later work conflicts with a confirmed decision, escalate the conflict instead of inventing new behavior.
