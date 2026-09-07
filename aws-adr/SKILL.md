---
name: aws-adr
description: Create, review, and maintain Architectural Decision Records (ADRs) using the AWS Prescriptive Guidance ADR format and lifecycle (Proposed, Accepted, Rejected, Superseded). Use when the user asks to write an ADR, record an architecture or design decision, start or update a decision log, review/accept/reject a proposed ADR, or supersede an existing ADR with a new one.
---

# AWS Architectural Decision Records (ADR)

Create and maintain ADRs that follow the AWS Prescriptive Guidance format and process: `https://docs.aws.amazon.com/prescriptive-guidance/latest/architectural-decision-records/`

An ADR is a short, immutable-once-accepted document that records one architecturally significant decision: its context, the decision itself, and its consequences. The set of ADRs in a repo forms the project's decision log.

## When to use this skill

Use it whenever the user wants to:
- Record a new architecture or design decision as an ADR.
- Scaffold or bootstrap a decision log (`docs/adr/`) for a project that doesn't have one yet.
- Move an ADR through its lifecycle: Proposed -> Accepted / Rejected, or Accepted -> Superseded.
- Review an existing ADR or the whole decision log for consistency.
- Find out whether a proposed code or architecture change conflicts with an existing accepted ADR.

Create an ADR only for decisions that are architecturally significant - per AWS's guidance (Richards and Ford), that means decisions about:
- **Structure** - architectural patterns, e.g. choosing microservices vs. a monolith.
- **Non-functional requirements** - security, availability, fault tolerance, performance.
- **Dependencies** - coupling between components or services.
- **Interfaces** - APIs and published contracts.
- **Construction techniques** - libraries, frameworks, tools, and processes.

Do not create an ADR for routine implementation detail, a single function's internals, or anything easily reversible with no cross-team impact - that belongs in code comments or a regular design note, not the decision log.

## Repo conventions

- Decision log directory: `docs/adr/` at the repo root, unless the repo already uses a different convention (check for an existing `adr/`, `docs/decisions/`, or similar directory first and follow it instead of introducing a second one).
- File name: `NNNN-short-kebab-title.md`, where `NNNN` is a zero-padded, strictly increasing sequence number (`0001-adapted-gitflow-branching.md`). Never reuse or renumber an existing ADR's number, including a rejected or superseded one.
- Index file: `docs/adr/README.md` lists every ADR with its number, title, and current status, newest first. Update this index every time an ADR is added or changes status.

If the repo has no `docs/adr/` directory yet, create it together with the index file before writing the first ADR.

## ADR fields

Use the exact section headings below, in this order, for every ADR. Full field definitions are in [references/template.md](references/template.md); a worked example from the AWS guide is in [references/example.md](references/example.md).

1. **Title** - one sentence naming the decision, not the problem.
2. **Status** - `Proposed`, `Accepted`, `Rejected`, or `Superseded by ADR-NNNN`.
3. **Date** - the date the status last changed, `YYYY-MM-DD`.
4. **Context** - the forces at play: technical, business, and team constraints that make this decision necessary. State the problem neutrally; do not argue for the answer here.
5. **Decision** - the choice made, stated actively ("We will ..."), with enough detail for someone unfamiliar with the discussion to understand what changes.
6. **Consequences** - the results of the decision, split into `Positive:` and `Negative:` bullet lists. Include trade-offs and follow-up work created by the decision, not just its benefits.
7. **Compliance** (optional) - concrete, checkable rules that follow from the decision, used during code and architecture review to verify conformance.
8. **Notes** (optional) - `Author`, `Version`, and a `Changelog` list.

If the org's documentation rules require recording rejected alternatives and the reasons they were rejected, add them as bullets inside **Context** (for example, "Considered X; rejected because Y") rather than inventing a non-standard section - this keeps the ADR compatible with the AWS format while still preserving that reasoning.

## Lifecycle and process

Full process detail (ownership, review meeting mechanics, and the supersede workflow) is in [references/process.md](references/process.md). Summary:

1. **Proposed** - the ADR owner drafts the ADR and opens it for review. An ADR in this state is a draft; content may still change freely.
2. **Review** - the team reads the ADR (10-15 minutes), then discusses comments. Either:
   - Action items are found -> ADR stays `Proposed`, owner tracks the actions, then re-schedules review, or
   - The team accepts it -> owner adds date, version, and stakeholders, sets `Accepted`, or
   - The team rejects it -> owner records the rejection reason in **Context** or **Notes** so the same option is not re-proposed later, sets `Rejected`.
3. **Accepted / Rejected are immutable.** Never edit the Decision or Consequences of an ADR once it is `Accepted` or `Rejected`. If new information requires a different decision, write a new ADR instead.
4. **Superseded** - when a new ADR replaces an accepted one, set the new ADR's Context to reference the old ADR by number, get the new ADR through the same review and acceptance steps, then change the old ADR's status to `Superseded by ADR-NNNN` and link forward to the new ADR. Never delete a superseded ADR.

## Workflow for this skill

When asked to write a new ADR:
1. Locate (or create) the decision log directory and index file per **Repo conventions**.
2. Determine the next sequence number from the highest existing `NNNN` in `docs/adr/`.
3. Ask the user for anything the Context/Decision needs that isn't already clear from the conversation - do not invent context, options, or consequences that were not discussed.
4. Write the ADR file using the field order and headings above, status `Proposed` unless the user says it is already agreed and should be recorded as `Accepted`.
5. Add or update the entry in `docs/adr/README.md`.
6. Report the new file path and number back to the user; do not mark it `Accepted` on their behalf.

When asked to accept, reject, or supersede an ADR:
1. Read the existing ADR in full first.
2. Apply only the status/date/notes changes described in **Lifecycle and process** above - never rewrite its Decision or Consequences in place.
3. Update the index file to match.
