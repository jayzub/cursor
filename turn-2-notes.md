# Turn 2 notes (do not paste into Taiga)

Continues from Model A (overall preference). Tree is still unpatched master.

## What this turn is
- Category (do not name in the prompt): Root Cause Analysis — fix the three verified bugs and add regression tests.
- Follow-up type: push back on A's plan / on A's "in fairness" hedge, then fix. Not "add a feature."

## In scope — verified by us
1. #7030 R deletes files when write/copy/move/hardlink are off (`remove_duplicates`)
2. #7043 display `!=` vs `string_dist` / `track_index_changed`
3. #4941 `--from-logfile` on `AC; DC` (`paths.split("; ")`)

## Explicitly out of scope this turn
- Threaded race (A only saw it with an injected delay; we did not verify it ourselves)
- `* None 1` / disambig `None` cosmetics
- convert, plugins, unrelated features

## Why the shape changed vs Turn 1
Turn 1 was "walk these paths, don't patch." This one is a reaction: reject the docs excuse, reject the case-change hedge, reject the race ranking, then patch the three we already reproduced. Different skeleton on purpose (feedback: no templated follow-ups, no feature-add treadmill).

## Tokens
Three real importer fixes + new tests + the import suite. That is the token burn. Do not add "be exhaustive."
