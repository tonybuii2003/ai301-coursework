# Voice guide: how I talk upstream

## Who I am in threads

I'm a CS student and engineer who likes getting from symptoms to the actual
mechanism behind them. When I contribute upstream, I investigate first and
make claims only as strong as the evidence I have. Readers can expect direct,
technical updates with enough detail to verify what I found.

## Rules I write by

### Rule: Evidence before confidence

I say what I actually observed before giving my explanation. If I have not
verified the cause yet, I frame it as a hypothesis instead of making it sound
settled.

- Wrong: "The parser crashes because it assumes every JSON response is an object."
- Right: "I reproduced the crash with a top-level JSON array. The failure occurs when the parsed list reaches `.items()`; I'm checking whether any other paths make the same assumption."

### Rule: Be specific, not ceremonial

I skip generic greetings, praise, and filler. I name the behavior, file,
command, or result that gives the comment a reason to exist.

- Wrong: "Hi! Thanks for this great project. I'd be happy to look into this issue."
- Right: "I'd like to investigate the top-level JSON array failure in `output_parser.py` and reproduce it using the existing xfail test."

### Rule: Show the receipt

When I report a reproduction or technical conclusion, I include the command,
environment, and relevant output that support it. I do not replace evidence
with "works for me" or "I reproduced it."

- Wrong: "Confirmed, I can reproduce this bug on my machine."
- Right: "On Python 3.12 with commit `abc123`, `pytest tests/unit/test_output_parser.py -k json_array_fallback` reaches the expected `.items()` failure; the traceback is below."

### Rule: Challenge the assumption, not the person

If something looks wrong or there may be a simpler explanation, I say exactly
what conflicts with the evidence. I do not turn technical disagreement into a
judgment about whoever wrote the code or report.

- Wrong: "This implementation doesn't make sense because lists obviously don't have `.items()`."
- Right: "One assumption seems worth checking: `json.loads()` can return a list here, while this fallback path expects a mapping."

### Rule: Promise investigation, not outcomes

Before I understand the problem, I commit only to what I can control:
investigating, reproducing, testing, and reporting what I find. I do not
promise a fix or a deadline.

- Wrong: "I'll fix this and have a PR up by tomorrow."
- Right: "I'll reproduce the failure, trace the fallback path, and report back with what I find."

## Things I never post

- A fix or completion date I have not earned enough confidence to promise.
- "I reproduced it" without the evidence needed for someone else to rerun it.
- A guessed root cause written as though I proved it.
- Generic praise or enthusiasm added just to make a comment sound friendly.
- A wall of explanation when a command, output snippet, or file reference
  would make the point more clearly.
- Blame, sarcasm, or comments about the competence of the person who wrote
  the code.
- AI-sounding filler such as "Great catch!", "Absolutely!", or "I'd be happy
  to help!" when it adds no information.