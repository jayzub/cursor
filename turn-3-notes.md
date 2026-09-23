# Turn 3 notes (do not paste into Taiga)

Continues from Model A after the Turn 2 fixes.

## What this turn is
- Not another “go fix the original three.”
- Variety: report leftovers A named and then skipped; report a hole in A’s logfile glue (`/`-only); push back on the half-done display (headers still raw).
- Inferable as debugging / RCA on the same importer+logfile path. Do not name a category.

## In scope — real, already seen
1. Skip-new logged as `duplicate-keep` (`session.py` `log_choice` order). A reproduced in T1, left in T2.
2. Merge-then-skip → library root via `commonpath`. A reproduced in T1, left in T2.
3. Windows `skip F:/Music/Artist; The Band/Album` — we reproduced empty/`commonpath` failure on master. A’s T2 writeup: glue only when the piece “doesn't start with `/`”.
4. Artist/Album header still raw `!=` (A’s own leftover). Same “screen follows the matcher” ask as T2, not a new feature.

## Out of scope
- Threaded race (already forbidden)
- `None` cosmetics (already forbidden)
- convert / plugins
- Revert the upgrade gate (user accepts it)

## Why the shape is different
T1 = walk, don’t patch. T2 = fix my three, leave the race. T3 = I tried your patch and it still drops skips / windows paths / headers. No numbered “three things I hit” clone.

## Tokens
Log_choice + merge path + windows-aware parse + header display + tests + import suite. Real work, not “be exhaustive.”
