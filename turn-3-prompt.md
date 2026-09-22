ran this against last week's import.log.

AC; DC comes through now. then I skipped a duplicate that was already in the library and the log wrote `duplicate-keep`. `--from-logfile` ignores that verb, so the album never comes back for retry. you called that in the review — "Skip new" logged as `duplicate-keep` — and then shipped without it. merge-then-skip is the same hole: the skip line picks up the old album's tracks and `commonpath` becomes the library root. I am not reimporting the whole music folder.

those two are still in the log path you were just in. fix them. I want a test where a skipped duplicate is actually logged as skip, and a test where merge-then-skip does not hand `--from-logfile` the library root.

also I grabbed a log off the windows box. line is `skip F:/Music/Artist; The Band/Album`. your note said you glue a piece back when it doesn't start with `/`. that path does not start with `/`. if that line still dies or comes back empty, the logfile fix isn't finished.

artist/album lines above the track list are still a raw `!=`. I said the screen follows the matcher. you stopped at the tracks. do the headers the same way or tell me they have to stay dumb.

upgrade staying gated with R is fine, leave it.

race and the None cosmetics still off. import suite after. no convert.
