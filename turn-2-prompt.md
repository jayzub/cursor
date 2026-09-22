ok, the three I actually hit are still real. go fix those. I don't want a fourth exploration pass.

R is the one that deleted data, so start there. write/copy/move/hardlink all off and the library dir is the music folder — R still has to leave the files on disk. I saw the note that the docs say "inside the library directory" and that's exactly my setup, so "working as documented" is not an answer. if you press R in that config the files stay. I want a test that would have failed on the tree you just reviewed.

on the track list: I read the "in fairness ≠ is accurate because the stored title will change case" bit. I don't care. if the matcher scored 0 I don't want that line lit up like a real mismatch — that's what made the two tracks that actually differ disappear. same for disc-vs-release numbering. the screen should follow what distance.py already decided, not a raw string !=.

logfile: the AC; DC skip line has to survive `beet import --from-logfile`. the current test only does the happy `path; path/CD 01` split, so add the semicolon-in-the-name case. one bad line also shouldn't abort the rest of the file if you can keep the other paths.

leave the threaded race alone. you only made that happen with an injected delay and I'm not taking a concurrency patch off a harness-only. same for the `* None 1` / `None, None` cosmetics.

regression tests for the three fixes, then run the import suite. stay in the importer — don't wander into convert or a plugin.
