# AWS Architectural Decision Records (ADR) Skill

An [agent skill](https://skills.sh/) that teaches Claude (or any compatible coding agent) to create and maintain Architectural Decision Records using the format and lifecycle from the [AWS Prescriptive Guidance: Architectural Decision Records](https://docs.aws.amazon.com/prescriptive-guidance/latest/architectural-decision-records/) guide.

## Install

```bash
npx skills add the-khiem7/aws-adr
```

Update later to pull the latest version from this repo:

```bash
npx skills update aws-adr -g
```

Once installed, the skill activates automatically whenever you ask your agent to write an ADR, start a decision log, or move an ADR through review, acceptance, rejection, or supersession. You can also invoke it directly with `/aws-adr` in an interactive session.

## What is an ADR

An Architectural Decision Record documents a single significant choice made about a software architecture: the context that made the decision necessary, the decision itself, and its consequences. A project's ADRs together form its decision log, a running history that lets anyone, including someone who joins the project years later, understand not just what the architecture looks like today but why it looks that way.

AWS's guidance describes an ADR as covering:

- **Structure** - architectural patterns, for example choosing microservices over a monolith.
- **Non-functional requirements** - security, high availability, fault tolerance.
- **Dependencies** - coupling between components or services.
- **Interfaces** - APIs and published contracts.
- **Construction techniques** - libraries, frameworks, tools, and processes.

Routine implementation detail, or anything easily reversible with no cross-team impact, does not need an ADR - that belongs in code comments or a regular design note instead.

## The AWS ADR format

Every ADR in this format uses the same eight sections, in the same order:

| Section      | Purpose                                                                                           |
| ------------ | ------------------------------------------------------------------------------------------------- |
| Title        | Names the decision, not the problem.                                                              |
| Status       | `Proposed`, `Accepted`, `Rejected`, or `Superseded by ADR-NNNN`.                          |
| Date         | The date the status last changed.                                                                 |
| Context      | The technical, business, and team constraints that make the decision necessary, stated neutrally. |
| Decision     | The choice made, stated as an active commitment ("We will...").                                   |
| Consequences | The results of the decision, split into`Positive:` and `Negative:` lists.                     |
| Compliance   | Optional. Concrete, checkable rules that follow from the decision.                                |
| Notes        | Optional. Author, version, and a changelog.                                                       |

An ADR moves through a small lifecycle: it starts `Proposed`, the team reviews it, and the owner then marks it `Accepted` or `Rejected`. Once accepted or rejected, an ADR is immutable - a later change in direction gets written as a brand new ADR, which, once accepted, marks the old one `Superseded` rather than editing it in place.

## Source

Built from the AWS Prescriptive Guidance ADR guide:

- [Overview and process](https://docs.aws.amazon.com/prescriptive-guidance/latest/architectural-decision-records/adr-process.html)
- [Appendix: example ADR](https://docs.aws.amazon.com/prescriptive-guidance/latest/architectural-decision-records/appendix.html)
