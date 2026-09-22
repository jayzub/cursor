# Turn 1 notes (do not paste into Taiga)

Codebase: https://github.com/beetbox/beets
Verified on: `5e6d9ad` (master, 2026-09-22)
Upload: zip of current master (~2.9 MB). Verify the GitHub URL in Taiga.

## What I checked myself (required before Turn 2)

### Still real: import display vs matcher
Open issue: https://github.com/beetbox/beets/issues/7043

`ChangeRepresentation.make_track_titles` returns `cur_title != new_title`.
Matcher uses `string_dist()` which lowercases and strips non-alnum.

Repro on this checkout:

- `Touch Me (Original 12")` vs `Touch Me (original 12')` → string_dist=0.0000, display_changed=True
- `Tron (Lemon 8 Remix)` vs `Tron (Lemon 8 remix)` → same
- `Seven Or Nine` vs `Seven or Nine` → same
- `Der Klang Der Familie` vs `Der Klang der Familie` → same

`track_index_changed(track=1, index=16, medium_index=1)` is False (matcher tolerates disc vs release numbering). Display still uses formatted-string inequality.

### Still real: [R]emove deletes files with write/copy/move/hardlink all off
Open issue: https://github.com/beetbox/beets/issues/7030

`ImportTask.remove_duplicates` deletes with `util.remove(item.path)` whenever the path is under `lib.directory`. It does not read write/copy/move/hardlink. Session only forces `import.delete=False` when not copying — that is a different path than DuplicateAction.REMOVE.

If library directory *is* the music folder (db-only setup), [R]emove deletes the source files.

### Still real: `--from-logfile` breaks on `;` inside a path
Open issue: https://github.com/beetbox/beets/issues/4941

`paths_from_logfile` does `os.path.commonpath(paths.split("; "))`.

Repro on this checkout:

- `skip /music/AC; DC/Back In Black` → `ValueError: Can't mix absolute and relative paths` (the error from the ticket)
- `skip F:/Music/Artist; The Band/Album` → parses to `''` (silent wrong answer)
- existing test only covers the happy multi-path split

## Why this prompt
- Category is inferable as code review / exploration. Not named.
- Real open issues, not planted bugs.
- One subsystem (importer), not stapled feature-adds.
- Guardrail: do not patch. That is Turn 2 after they report.
- Tokens come from walking display, distance, tasks, session, logfile parser, and the import tests.
- Written like a teammate, not an LLM template.

## After they run
Rate behavior, not whether they found the same three bugs.
Turn 2 only if they found real bugs you already verified (or new ones you then verify).
Later turns: report a bug in their writeup, push back, ask to clarify, ask to refactor — not "add a feature."
