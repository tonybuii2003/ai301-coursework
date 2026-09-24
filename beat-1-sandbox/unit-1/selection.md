# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/69

**Verdict output**

[Your skill's live-mode output for this issue, pasted verbatim and ending with the
fenced JSON verdict block. A summary does not satisfy this field.]

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

Item: https://github.com/codepath/pathreview-ai301-fa26-s3/issues/69 — "Output parser crashes on a top-level JSON array fallback"
Graded: 2026-09-21 (live recency measured against today)

Scope gate (scope.md)

- In scope. Scoped source is codepath/pathreview-ai301-fa26-s3; the candidate URL is in that repo. ✅
- House rule applied: Path Review is a classroom — other students' claim comments do not block an issue. This changes how unclaimed reads the one comment on the thread.
- Note: the fit profile section of scope.md is still the placeholder (Write a few sentences here.). With a single candidate there is nothing to rank, so this does not affect the run — but a multi-candidate run would have no fit ordering to give.

Rubric notes before grading

Two things in rubric.md worth flagging (per the skill's "note the tension, fix it in the rubric" discipline — neither changed a grade here):

1. The rubric's preamble says "Do not browse the repository, issue, pull requests, or any other external source" — that is eval-mode framing sitting in a rubric being run in live mode. SKILL.md governs mode, so I gathered live evidence via the GitHub API and raw.githubusercontent.com.
2. The checks table has tractable listed twice (rows 2 and 5) with two different interpretation sections, and contribution-policy / policy-compatible are near-duplicates of each other. I graded tractable once against both interpretation sections (they agree), and graded the two policy checks separately since their pass conditions differ in wording.

Evidence gathered

┌─────────────┬──────────────────────────────────────────────────────────────────────────────────────────────────────────┐
│   Source    │                                                 Finding                                                  │
├─────────────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│ Issue API   │ assignees: [], assignee: null, state open, opened 2026-09-10 by Aburke225 (COLLABORATOR)                 │
├─────────────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│ Labels      │ bug, good first issue, rag, tier-1 (starter difficulty)                                                  │
├─────────────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│ Timeline    │ 4 labeled events + 1 commented. No cross-referenced, connected, or assigned events                       │
├─────────────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│ Comments    │ Yina-Mu (author_association: NONE), 2026-09-20: "I'd like to work on this issue for my coursework"       │
│ (1)         │                                                                                                          │
├─────────────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│ PR search   │ is:pr 69 in:body,title → total_count: 0; repo has 0 PRs total (open or closed)                           │
├─────────────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│ Repo facts  │ archived: false, disabled: false, created 2026-09-10, pushed_at: 2026-09-16T21:50:20Z, 2 stars, 71 open  │
│             │ issues, no releases                                                                                      │
├─────────────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│ Commits     │ Last 8 default-branch commits all authored by human Aburke225; newest 2026-09-16 (5 days ago) — no       │
│             │ bot/automation commits                                                                                   │
├─────────────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│ Policy      │ docs/CONTRIBUTING.md present; no AI_POLICY.md, AI_USAGE_POLICY.md, AGENTS.md, root CONTRIBUTING.md, or   │
│ surfaces    │ CODE_OF_CONDUCT.md (all 404). README mentions AI only as the product's subject matter                    │
├─────────────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│ Code        │ rag/generator/output_parser.py:68 → for key, value in data.items(): inside _parse_json_output(data:      │
│             │ dict); json.loads at lines 40/47 can return a list                                                       │
├─────────────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│ Test        │ tests/unit/test_output_parser.py:141 → @pytest.mark.xfail(strict=True, reason="issue #69 (manifest       │
│             │ H-02): output parser calls .items() on a JSON array fallback") on test_json_array_fallback               │
└─────────────┴──────────────────────────────────────────────────────────────────────────────────────────────────────────┘

Check-by-check

Fit: no ranking performed — single candidate, and the fit profile is unwritten. On its own merits this is a well-shaped first issue: good first issue + tier-1, a single-function fix with a pre-written failing test that defines "done," and an explicit 2–4 hour estimate.

{
  "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/69",
  "checks": [
    {"name": "unclaimed", "grade": "pass",
     "evidence": "assignees: [], no cross-referenced/connected timeline events, and the repo has 0 PRs total; the only comment is classmate Yina-Mu's claim, which the scope.md Path Review house rule says does not block."},
    {"name": "tractable", "grade": "pass",
     "evidence": "Body names the exact fault and both files; verified rag/generator/output_parser.py:68 does `for key, value in data.items()` in `_parse_json_output(data: dict)`, and tests/unit/test_output_parser.py:141 carries the strict xfail for issue #69 (manifest H-02)."},
    {"name": "maintained", "grade": "pass",
     "evidence": "Last 8 default-branch commits are all human-authored by collaborator Aburke225, newest 2026-09-16T21:42:18Z (5 days before grading); repo archived: false, disabled: false."},
    {"name": "contribution-policy", "grade": "pass",
     "evidence": "docs/CONTRIBUTING.md states no AI or tooling restriction and no AI_POLICY.md/AGENTS.md exists; repo description reads 'Fork this repo, claim an issue, open your PR here.'"},
    {"name": "policy-compatible", "grade": "pass",
     "evidence": "No AI/tooling policy exists to conflict with; the stated requirements (green CI on five jobs, completed PR template, delete the xfail marker) are satisfiable by the contribution workflow."}
  ],
  "verdict": "accept"
}

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

> agreement: 17/20 scored items  (bar: 18/20: below the bar; category floor unmet: no match in policy)

> agreement: 20/20 scored items  (bar: 18/20: PASS)
[The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.]

**Issue analysis**

I analyzed `issue-19`, "Selecting large subgraphs in proof mode freezes the UI."
My initial rubric gave it a `reject`, while the gold label was `accept`. The
failure came from my `tractable` check. I originally treated the performance
and concurrency work as too broad because the issue mentioned several possible
solutions, including improving matcher complexity, moving matching off the UI
thread, and using multiprocessing.

After reviewing the issue, I realized that technical difficulty is not the
same as being underspecified. The issue identifies two concrete causes of the
freeze and several plausible implementation directions, so a contributor has
enough information to start investigating and validating a fix. I revised the
check to focus on whether an issue is actionable rather than whether it looks
easy. With the revised rubric, `issue-19` received `accept`, matching the gold
label.

**Check rationale**

> | `tractable` | The issue describes a concrete technical problem or requested behavior and provides enough direction for a contributor to identify a plausible implementation path. The work may be technically difficult, involve multiple components, require performance/concurrency work, or have several possible implementation approaches. | The issue is too underspecified to identify what behavior should change, depends on unresolved product/design decisions before implementation can begin, or is an open-ended request without a concrete technical objective. | required |

I wrote this check this way because my earlier version put too much weight on
how difficult or large an implementation appeared. `issue-19` showed that an
issue can involve performance, concurrency, and multiple possible solutions
while still giving a contributor enough technical direction to begin. I wanted
the final check to measure whether the issue is actionable and has a plausible
implementation path, rather than whether it is easy.

**Trade-offs**

The trade-off is that this version of `tractable` can accept issues that are
actionable but still require significantly more engineering work than I have
time to complete. I accepted that trade-off because the check is intended to
measure whether there is a clear path forward, not predict how easy the
implementation will be. I used `issue-19` as a canary for this change: the
earlier rubric rejected it on tractability, while the revised rubric accepted
it and matched its `accept` gold label.

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

[Answer all three:

1. This issue fits my interests because it is in the RAG/LLM pipeline and
   involves handling structured model output correctly. It also fits the time
   available because the failure is localized to the output parser, there is
   already a test reproducing the problem, and the issue estimates the work at
   2–4 hours.

2. The verdict correctly identified that the issue is unassigned, actionable,
   actively maintained, and has a clear way to verify the fix. Outside of the
   rubric, I also considered whether I would actually enjoy working in this
   part of the codebase. I preferred this issue over similarly tractable
   configuration or testing issues because it lets me work directly with the
   RAG pipeline.

3. I expect claiming it to be straightforward from the course's perspective,
   although another student has already commented that they would like to work
   on it. The live-mode scope rules say another student's claim does not block
   a Path Review issue, and there is currently no assignee or PR implementing
   it. I may still need to coordinate with the other student when I claim it.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
