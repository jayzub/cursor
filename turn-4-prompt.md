I pointed `--from-logfile` at last week's import.log like you said. I did not delete the library-root skip lines by hand — there are a lot of them — and it still wants to walk the music folder. if a logged path is the library directory, drop that line on read. I am not hand-editing that file.

your weight-0 leftover is also wrong. I have album weight at 0 because I don't want the album title swinging the match. I still need to see Substance vs Closer on the header. I just got `*` on a real album change. you wrote "If you set a distance weight to 0, that field is never marked. That's the cost of following the matcher."

no. the matcher still ran the album comparison — the raw penalty is sitting there. weight 0 means it doesn't vote. it does not mean the field wasn't compared. case-only stays `*`. a real album difference still gets `≠`. look at what distance actually recorded, not the weighted score.

and I reran after an upgrade pass that found nothing to take. those albums came back. `--from-logfile` retries `duplicate-skip`. a declined upgrade is not a skip I want retried. I said leave the R gate. I did not say change what a declined upgrade means on retry. those should stay out of `--from-logfile` the way keep does.

race and the None text still off. import suite after. no convert, and don't run the rest of the plugins this time.
