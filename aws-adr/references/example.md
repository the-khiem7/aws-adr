# Worked example (from the AWS guide's appendix)

Source: `https://docs.aws.amazon.com/prescriptive-guidance/latest/architectural-decision-records/appendix.html`

Reproduced as-is to show the expected level of detail per section.

---

## Title

This decision defines the software development lifecycle approach for ABC application development.

## Status

Accepted

## Date

2022-03-11

## Context

ABC application is a packaged solution, which will be deployed to the customer's environment by using a deployment package. We need to have a development process that will enable us to have a controllable feature, hotfix, and release pipeline.

## Decision

We use an adapted version of the GitFlow workflow to develop ABC application.

For simplicity, we will not be using the hotfix/* and release/* branches, because ABC application will be packaged instead of being deployed to a specific environment. For this reason, there is no need for additional complexity that might prevent us from reacting quickly to fix bugs in production releases, or testing releases in a separate environment.

The following is the agreed branching strategy:
- Each repository must have a protected main branch that will be used to tag releases.
- Each repository must have a protected develop branch for all ongoing development work.

## Consequences

Positive:
- Adapted GitFlow process will enable us to control release versioning of the ABC application.

Negative:
- GitFlow is more complicated than trunk-based development or GitHub flow and has more overhead.

## Compliance

- The main and develop branches in each repository must be marked as Protected.
- Changes to the main and develop branches must be propagated by using merge requests.
- At least one approval is required for every merge request.

## Notes

- Author: Jane Doe
- Version: 0.1
- Changelog:
  - 0.1: Initial proposed version

---

## What this example shows

- State the constraint in Context before naming the chosen option (here: packaged deployment to customer environments, named before GitFlow) - reasoning first.
- Record rejected alternatives in Decision or Context, with why (here: hotfix/*, release/* branches) - reuse this "considered and rejected" pattern instead of only listing the chosen option.
- Include at least one Negative consequence even on an accepted ADR - do not drop trade-offs because the decision was approved.
- Write Compliance as mechanically checkable rules (here: branch protection, required merge-request approvals), never as prose.
