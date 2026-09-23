# Turn 5 notes (do not paste into Taiga)

Continues from Model A after the Turn 4 leftover-note pushback.

## What this turn is
- Variety: push back on A’s “can't tell them apart” limitation, ask it to clarify that case, and clean up the logfile path it stacked. Not another “I ran your patch, leftovers you named.”
- Inferable as debugging + a bit of maintenance on the same read path. Do not name a category.

## In scope — verified by us
1. Artist-folder leftover is real. A’s `_contains_directory(path, library_dir)` is true only when `path` is the library dir or an ancestor. An artist folder is a descendant, so `skip /music/AC; DC` still comes through. `beet import` walks that folder and reimports every album under the artist. User’s library dir *is* the music folder, so this is last week’s log, not a new feature.
2. Distinguishable from a real retry: a real skip logs one album folder; a merge-then-skip commonpath of two albums under the same artist is the artist folder, which already contains >1 library album. A said they can’t tell them apart. They can, using the library they already have.
3. Logfile path is three write-side patches (`log_choice` skip-first, `_merged_items` filter, `upgrade_declined`) plus three read-side ones (`; ` glue, drive/UNC start, library-root drop). Asking to put read-side filters in one place is cleanup of code they wrote, not a feature add.

## Out of scope
- Threaded race
- `None` cosmetics
- convert / plugin suite
- Revert the R gate
- Changing what a good single-album skip line does

## Why the shape is different
T1 = walk, don’t patch. T2 = fix my three. T3 = leftovers you named are still there. T4 = your leftover notes are wrong. T5 = I don’t buy the limitation you left, and the logfile path is a pile. Clarify + push back + clean up.

## Tokens
Library query vs logged path, import walk of an artist dir, consolidating `paths_from_logfile`, tests that fail when an artist folder with two library albums is retried, import suite only. Real work, not “be exhaustive.”
