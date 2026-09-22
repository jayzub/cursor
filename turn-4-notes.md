# Turn 4 notes (do not paste into Taiga)

Continues from Model A after the Turn 3 logfile leftovers.

## What this turn is
- Variety: push back / say the leftover notes were wrong. Not “go fix these N holes I found.”
- Inferable as debugging + a bit of RCA on the code A just wrote. Do not name a category.

## In scope — verified by us
1. Weight-0 header: A’s `penalized()` uses `dist[key] > 0`, which is `sum(_penalties[key]) * weight`. With `match.distance_weights.album = 0`, Substance vs Closer has raw ~0.89 and weighted 0. Header stays `*`. Case-only is raw 0 either way. Repro: mutate `Distance._weights["album"] = 0` and `add_string`. A’s own leftover sentence is the wrong product claim.
2. Declined upgrade → `duplicate-skip`: `stages.py` sets `DuplicateAction.SKIP` when upgrade finds nothing, then `log_choice(task, True)`. A’s skip-first `log_choice` logs `duplicate-skip`. `paths_from_logfile` retries `asis` / `skip` / `duplicate-skip`. So a declined upgrade comes back. User accepted the R gate, not this retry.
3. Old library-root skip lines: A said “Delete that line by hand.” `--from-logfile` still yields `lib.directory` / common parent and `beet import` walks it. User already said they will not reimport the music folder.

## Out of scope
- Threaded race
- `None` cosmetics
- convert / full plugin suite (explicit this time — they wandered T2 and T3)
- Revert the upgrade-vs-R delete gate

## Why the shape is different
T1 = walk, don’t patch. T2 = fix my three. T3 = I ran your patch, leftovers you named are still there. T4 = I followed your leftover notes and they are wrong / unacceptable. No numbered “three things I hit.”

## Tokens
Distance vs display helper, log_choice upgrade verb, logfile read-path vs library dir, tests that fail on the current tree, import suite only. Real work, not “be exhaustive.”
