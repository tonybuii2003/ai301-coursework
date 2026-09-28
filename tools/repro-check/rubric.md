# Rubric: is this reproduction package ready to post?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| `environment-grounded` | The repro report's environment record, read together with any version, commit, runtime, dependency, OS/platform, or configuration details in the reproduction steps and artifacts. | Pass when the recorded environment identifies the material conditions needed to interpret and rerun the attempted reproduction. Fail when missing or ambiguous environment information could reasonably change the observed behavior or prevent another contributor from knowing what was tested. | required |
| `rerunnable` | The repro report's reproduction procedure, including commands, inputs, setup/preconditions, referenced files or tests, and any artifacts needed to interpret those actions. | Pass when another contributor could perform the same attempted reproduction from the recorded evidence without having to invent a material action, input, or precondition. The procedure may be short or long; judge whether the experiment can actually be rerun, not its number of steps or formatting. | required |
| `target-behavior` | The issue's described expected/problem behavior read against the repro report's observed result and its direct artifacts, especially output excerpts, tracebacks, logs, screenshots, responses, or test results. | Pass when the artifacts demonstrate the same behavior the issue describes, or, for a cannot-reproduce result, demonstrate that the attempted target behavior did not occur under the recorded conditions. Fail when the evidence instead demonstrates an adjacent, setup, dependency, permission, network, or otherwise different failure and presents it as the target issue. | required |
| `honest-outcome` | The repro report's stated conclusion read against its commands, observations, and artifacts. | Pass when the conclusion is no stronger than the evidence supports: a reproduced result is supported by evidence of the target behavior, and a cannot-reproduce result accurately reports that the attempted reproduction did not produce it. Fail when the report claims reproduction without supporting evidence, treats a different failure as reproduction, or turns a cannot-reproduce result into an unsupported claim that the issue is fixed, invalid, or nonexistent. | required |
| `repo-conventions` | The claim comment and repro report read against applicable repository-specific requirements in the repo-facts block and the contribution/conventions evidence identified by `references/evidence-guide.md`, including any AI/tool-use disclosure requirement. | Pass when the comments comply with every applicable repository convention evidenced in the package. If the repository requires disclosure of AI or tool assistance, the applicable comment must actually make that disclosure. Pass when no relevant special convention is evidenced. Fail when an evidenced requirement applies but the submitted comment violates or omits it. | required |

## Verdict rule

The package is `ready` only when every required check passes.
The package is `hold` when any required check fails or is `unclear`.

In the final JSON verdict, write `accept` for `ready` and `reject` for `hold`.

Preferred checks, if added later, never change the verdict.