pulled current master this morning. before we start patching I want someone to actually go through the importer and tell me what's still broken vs what's already been cleaned up.

three things I hit myself:

I run beets as a db only — write/copy/move/hardlink all off. library directory is the music folder. I pressed R on a duplicate prompt (Remove / Merge / Keep) for a multi-disc album that matched the wrong MBID and it deleted the source files. no confirm, they were just gone.

import UI is also lying to me. I'll get a 98% match and the track list is almost all ≠ because of Original vs original, 12" vs 12', Seven Or Nine vs Seven or Nine. the two tracks that actually differ disappear in that. I already looked at distance.py enough to know the matcher strips case and punctuation, so the screen is scoring a different comparison than the match.

and `beet import --from-logfile` died with `Can't mix absolute and relative paths` on a skip line whose folder name has a semicolon in it. AC; DC style. the tests only cover the happy `path; path/CD 01` split.

can you walk those three paths — match display vs distance, duplicate remove vs the write/copy/move/hardlink flags, and the logfile parser — and come back with what's still true on this checkout? run the import tests, write a small repro if you need to. don't start fixing anything. if you edit the tree I can't tell what you found. if you trip over another real bug in those same files I want that too.
