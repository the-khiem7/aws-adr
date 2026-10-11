<h1 align="center"><img src="assets/banner.webp" alt="aws-adr: AWS Architectural Decision Records (ADR) Skill. Record why, not just what. An agent skill for Architectural Decision Records, in the AWS Prescriptive Guidance format. A row of the four statuses, Proposed, Accepted, Rejected, and Superseded, and three example ADR cards on a timeline with the statuses Proposed, Accepted, and Superseded." width="100%"></h1>

<p align="center">
<a href="#install"><picture><source media="(prefers-color-scheme: dark)" srcset="assets/nav-install-dark.webp"><img src="assets/nav-install.webp" alt="Install" height="34"></picture></a>
<a href="#what-is-an-adr"><picture><source media="(prefers-color-scheme: dark)" srcset="assets/nav-what-dark.webp"><img src="assets/nav-what.webp" alt="What is an ADR" height="34"></picture></a>
<a href="#lifecycle"><picture><source media="(prefers-color-scheme: dark)" srcset="assets/nav-lifecycle-dark.webp"><img src="assets/nav-lifecycle.webp" alt="Lifecycle" height="34"></picture></a>
<a href="#the-aws-adr-format"><picture><source media="(prefers-color-scheme: dark)" srcset="assets/nav-format-dark.webp"><img src="assets/nav-format.webp" alt="Format" height="34"></picture></a>
</p>

**An [agent skill](https://skills.sh/) that teaches Claude (or any compatible coding agent) to create and maintain Architectural Decision Records using the format and lifecycle from the [AWS Prescriptive Guidance: Architectural Decision Records](https://docs.aws.amazon.com/prescriptive-guidance/latest/architectural-decision-records/) guide.**

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

AWS's guidance says to write an ADR for decisions about structure, non-functional requirements, dependencies, interfaces, and construction techniques, and to skip it for routine detail.

<picture><source media="(prefers-color-scheme: dark)" srcset="assets/when-to-adr-dark.webp"><img src="assets/when-to-adr.webp" alt="Two panels. Write an ADR for: Structure (architectural patterns, such as microservices over a monolith); Non-functional requirements (security, high availability, fault tolerance); Dependencies (coupling between components or services); Interfaces (APIs and published contracts); Construction techniques (libraries, frameworks, tools, and processes). Skip the ADR for: routine implementation detail, a single function's internals, and anything easily reversible with no cross-team impact. Use a code comment or a regular design note instead." width="100%"></picture>

## Lifecycle

An ADR starts as `Proposed`, the team reviews it, and the owner then marks it `Accepted` or `Rejected`. Once accepted or rejected, an ADR is immutable - a later change in direction gets written as a brand new ADR, which, once accepted, marks the old one `Superseded` rather than editing it in place.

<picture><source media="(prefers-color-scheme: dark)" srcset="assets/lifecycle-dark.webp"><img src="assets/lifecycle.webp" alt="Lifecycle flow. Proposed: the owner drafts the ADR and opens it for review. An arrow leads to Review: the team reads it for 10-15 minutes, then discusses. Review has three outcomes. Changes: the ADR stays Proposed, the owner actions each comment and reschedules, and a dashed arrow returns to Review. Agree: Accepted, where the owner adds date, version and stakeholders, and the ADR is immutable. Decline: Rejected, where the owner records the reason so it is not proposed again, and the ADR is immutable. From Accepted, when a new ADR is accepted, an arrow leads to Superseded, marked Superseded by ADR-NNNN and never deleted." width="100%"></picture>

## The AWS ADR format

Every ADR in this format uses the same eight sections, in the same order. Compliance and Notes are optional.

<picture><source media="(prefers-color-scheme: dark)" srcset="assets/anatomy-dark.webp"><img src="assets/anatomy.webp" alt="The eight ADR sections in order. 1 Title: names the decision, not the problem. 2 Status: Proposed, Accepted, Rejected, or Superseded by ADR-NNNN. 3 Date: the date the status last changed. 4 Context: the constraints that make the decision necessary, stated neutrally. 5 Decision: the choice made, as an active commitment, We will. 6 Consequences: the results of the decision, split into Positive and Negative lists. 7 Compliance, optional: concrete, checkable rules that follow from the decision. 8 Notes, optional: author, version, and a changelog." width="100%"></picture>

<details>
<summary>The eight sections as a table</summary>

| Section      | Purpose                                                                                           |
| ------------ | ------------------------------------------------------------------------------------------------- |
| Title        | Names the decision, not the problem.                                                              |
| Status       | `Proposed`, `Accepted`, `Rejected`, or `Superseded by ADR-NNNN`.                          |
| Date         | The date the status last changed.                                                                 |
| Context      | The technical, business, and team constraints that make the decision necessary, stated neutrally. |
| Decision     | The choice made, stated as an active commitment ("We will...").                                   |
| Consequences | The results of the decision, split into `Positive:` and `Negative:` lists.                     |
| Compliance   | Optional. Concrete, checkable rules that follow from the decision.                                |
| Notes        | Optional. Author, version, and a changelog.                                                       |

</details>

## Source

Built from the AWS Prescriptive Guidance ADR guide:

- [Overview and process](https://docs.aws.amazon.com/prescriptive-guidance/latest/architectural-decision-records/adr-process.html)
- [Appendix: example ADR](https://docs.aws.amazon.com/prescriptive-guidance/latest/architectural-decision-records/appendix.html)

This is an independent project and is not affiliated with or endorsed by Amazon Web Services. The visual style uses the open-source [Cloudscape](https://cloudscape.design/) design tokens. The cube mark is adapted from the AWS favicon; AWS and its marks are trademarks of Amazon.com, Inc. or its affiliates.

