# Issue Selection Rubric

Use only evidence contained in the provided issue bundle.
Do not browse the repository, issue, pull requests, or any other external
source.

Grade each check as:

- `P` / `pass`: the pass condition is supported by the bundle.
- `F` / `fail`: the pass condition is contradicted by the bundle.
- `?` / `unknown`: the bundle does not contain enough evidence to decide.

## Checks

| Check | Pass condition | Fail condition | Weight |
|---|---|---|---|
| `unclaimed` | No assignee and no evidence that another contributor is already actively implementing the issue. There is no open linked PR or PR explicitly referenced in the issue/comments as implementing the requested work. | The issue has an assignee, an open PR addressing it, or a comment clearly indicating that another contributor is actively implementing it. A PR mentioned in the comments counts even if repository metadata says it is not formally linked. | required |
| `tractable` | The requested change is sufficiently concrete and bounded to plausibly implement and validate as a focused contribution. The issue identifies a bug, behavior, feature, or expected change with enough information to determine what work is needed. | The request is fundamentally ambiguous, extremely broad/open-ended, requires unresolved product/design decisions, or does not provide enough direction to identify a plausible implementation. | required |
| `maintained` | The repository shows credible evidence of active maintenance and a reasonable path for contributions to receive attention. Recent substantive repository activity and/or recent maintainer engagement support this. | The repository appears effectively inactive or abandoned, or available evidence indicates contributions are unlikely to receive maintainer attention. Repository activity consisting only of automation should not by itself establish active human maintenance. | required |
| `contribution-policy` | The repository's stated contribution policy permits the intended contribution workflow, or the bundle contains no policy restricting it. | The repository explicitly prohibits or materially restricts the contribution method required by this task, such as prohibiting AI-generated contributions when the workflow would produce an AI-generated contribution. | required |
| `tractable` | The issue describes a concrete technical problem or requested behavior and provides enough direction for a contributor to identify a plausible implementation path. The work may be technically difficult, involve multiple components, require performance/concurrency work, or have several possible implementation approaches. | The issue is too underspecified to identify what behavior should change, depends on unresolved product/design decisions before implementation can begin, or is an open-ended request without a concrete technical objective. | required |
| `policy-compatible` | The repository has no stated AI/tooling restriction, or its policy explicitly permits the contribution workflow represented by this evaluation. | The repository's policy requires contributor actions, understanding, verification, or authorship that cannot be satisfied by an autonomous issue-solving workflow. | required |

## Check interpretation

### `unclaimed`

The purpose of this check is to avoid duplicating work.

Fail if any of the following are present:

- the issue has an assignee;
- an open linked PR addresses the issue;
- the comments reference an open PR implementing the issue;
- someone explicitly says they are currently working on the issue or will
  imminently submit the implementation.

A PR does not need to appear in the bundle's `linked PRs` metadata to count.
If the issue thread explicitly identifies a PR as implementing the requested
change, treat the work as claimed.

Historical discussion, abandoned attempts, or someone merely expressing
interest do not automatically fail this check unless the bundle indicates
the work is still active.

### `tractable`

Judge the implementation task, not whether the issue description is long.

Pass when the requested outcome is concrete enough that a contributor could
reasonably identify the relevant change and how to verify it.

Examples that normally pass:

- correcting an incorrect variable or API reference;
- changing a specific platform guard;
- restoring a documented compatibility behavior;
- adding a bounded CLI option with clearly described semantics;
- adding a regression or integration test for a defined behavior.

Fail when substantial specification or design work must happen before an
implementation can reasonably begin.

Do not fail merely because tests are required or because the contributor
must inspect an unfamiliar codebase.

### `maintained`

Evaluate whether the project currently appears maintained enough for a new
contribution to have a realistic path to review.

Strong positive evidence includes:

- recent human-authored or human-reviewed development activity;
- recent releases;
- recent maintainer responses to issues or pull requests.

Automation-only commits are weak evidence and should not by themselves prove
active maintenance.

If the latest repository activity is very old relative to the bundle's
capture date and there is no meaningful recent maintainer engagement, fail.

When maintainer-response samples are provided, recent responses within about
7 days are positive evidence. Very old responses or samples with no
maintainer response are negative evidence.

Use `?` rather than inventing activity when the bundle does not provide
enough evidence to determine maintenance status.

### `contribution-policy`

Check the repository's stated contribution policy for restrictions that
would make this contribution inappropriate.

Pass when:

- the bundle reports no relevant restriction; or
- AI/tool-assisted contributions are explicitly allowed under conditions
  that can reasonably be followed, such as requiring the contributor to
  understand and take responsibility for the change.

Fail when:

- the repository explicitly prohibits the type of contribution this
  workflow would produce; or
- complying with the stated policy is incompatible with the intended
  contribution workflow.

Do not fail merely because a repository mentions AI. Distinguish between
a complete prohibition and policies that permit assistive AI use subject
to contributor understanding or responsibility.

### `tractable`

This check measures whether the issue is actionable, not whether it is easy,
small, or suitable for a beginner.

Pass when the bundle provides both:

1. a concrete problem or desired behavior; and
2. enough technical direction to identify at least one plausible
   implementation path.

An issue can pass even when:

- the implementation is technically difficult;
- several files or components may need changes;
- performance optimization is required;
- concurrency, threading, or multiprocessing is involved;
- multiple possible fixes are proposed;
- investigation is still required to determine which proposed fix is best.

Concrete suspected causes, affected components, proposed fixes, reproduction
steps, expected behavior, or acceptance criteria are evidence of tractability.

Fail only when the contributor cannot reasonably determine what should be
implemented from the bundle without first resolving substantial product,
requirements, or design ambiguity.

Do not infer that an issue is untractable merely from its apparent engineering
difficulty or implementation size.

### `policy-compatible`

Evaluate whether the repository's stated contribution policy is compatible
with the contribution workflow being evaluated.

Pass when:

- the bundle reports no relevant AI/tooling restriction; or
- the stated policy permits the workflow without requirements that depend
  on personal human understanding, authorship, verification, or
  responsibility beyond submitting a technically correct change.

Fail when the policy explicitly requires the contributor to personally
understand, test, explain, author, or take responsibility for AI-assisted
changes in a way that an autonomous contribution workflow cannot itself
satisfy.

Do not treat every mention of AI as a failure. Apply the actual requirements
stated in the bundle.

## Verdict rule

- `accept` only if every `required` check passes.
- `reject` if any `required` check fails.
- If a required check is `?`, conservatively `reject`.
- `preferred` checks, if added later, never change the verdict.
