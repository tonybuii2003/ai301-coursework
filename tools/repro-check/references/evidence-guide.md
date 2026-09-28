# Evidence guide: where proof lives in a reproduction package

## Environment

**Where it lives**

In eval mode, look at the issue context for the environment or versions the
issue says are affected, then compare those with the environment recorded in
the repro report. Also use the repo-facts block when it identifies a relevant
repository version, release, commit, platform, runtime, or dependency.

In live mode, read the issue thread for the reported environment and compare it
with the environment recorded in the student's draft repro comment and the
environment actually used during reproduction.

**What good looks like**

The record identifies the material conditions under which the reproduction was
attempted. Versions or platforms that matter to the reported behavior match the
issue's target, or any difference is explicitly called out so a reader knows
what was actually tested.

## Steps

**Where it lives**

In eval mode, look at the repro report's commands, inputs, setup,
preconditions, test names, and ordered reproduction procedure. Read them
against the reproduction instructions or trigger described in the issue
context.

In live mode, use the issue's reproduction instructions together with the
commands, inputs, and procedure in the student's draft repro comment.

**What good looks like**

A stranger can start from the recorded state and reach the attempted trigger
without inventing a material command, input, configuration value, or
precondition. Exact commands and inputs should be preserved when they affect
the result.

## Behavior shown

**Where it lives**

In eval mode, find the reported target behavior in the issue context. Then
inspect the repro report's direct artifacts: terminal output, traceback, test
output, logs, screenshots, response bodies, or other captured observations.

In live mode, compare the behavior described in the GitHub issue with the
artifacts produced during reproduction and included or quoted in the student's
draft repro comment.

**What good looks like**

The artifact shows the behavior the issue actually describes. A different
setup, dependency, permission, network, or unrelated failure is not evidence
of the target bug merely because it occurred while following the reproduction
steps.

For a cannot-reproduce result, the artifact should instead show what happened
when the correct trigger was attempted under the recorded environment.

## Honesty

**Where it lives**

In eval mode, compare the repro report's conclusion with its recorded steps and
artifacts. The evidence supporting "reproduced" or "could not reproduce" lives
in the same commands, output, logs, screenshots, or test results used to show
the behavior.

In live mode, compare the conclusion in the student's draft repro comment with
the evidence actually produced during the reproduction attempt.

**What good looks like**

The conclusion says no more than the evidence establishes. "Reproduced" is
supported by evidence of the target behavior; "could not reproduce" is
supported by a valid attempt where that behavior did not occur.

A cannot-reproduce result does not by itself prove that the issue is fixed,
invalid, or nonexistent. Likewise, encountering some other error does not make
the target issue reproduced.

## Comms

**Where it lives**

In eval mode, read the claim comment and repro report against the issue context,
repo-facts block, and any contribution, comment, template, or AI/tool-use
requirements supplied in the package.

In live mode, read the GitHub issue thread and the repository's applicable
contribution documentation, templates, and AI/tool-use policy. Compare those
requirements with the student's draft claim and repro comments before posting.

**What good looks like**

The claim identifies the specific issue being investigated without promising
an unverified fix or deadline. The repro comment states the attempted
reproduction and its result specifically enough that maintainers can understand
what was tested.

Both comments follow applicable repository requirements. If the repository
requires disclosure of AI or tool assistance, the required disclosure actually
appears in the applicable comment rather than being inferred.