# Prompt 2 — Adversarial verification pass

Run this in a **separate turn** (fresh context if possible), with the claims log
from Prompt 1 and the same source text. Don't run it in the same breath as the
extraction — you want a genuinely adversarial second look, not the same pass
re-confirming itself.

```
Here is a claims log extracted from a paper, and the paper's source text. For
each entry, act as an adversarial reviewer, not the original extractor. Your job
is to find where this is wrong, not to confirm it looks fine.

For each entry, check:
1. Does the quote actually appear in the source text (verbatim or near-verbatim)?
   Flag if not found.
2. Does the "Claim" line match the actual scope of the quote — or does it
   silently generalize a specific/conditional finding into a general one? Watch
   for words like "models," "results," or "generally" replacing a named subset
   (one model, one dataset, one condition).
3. Is there a caveat, exception, or qualifying sentence elsewhere in the source
   (nearby paragraphs, footnotes, table notes) that changes how this claim should
   be read, that the extraction missed?
4. Rate each entry: VERIFIED / SCOPE ERROR / MISSING CAVEAT / NOT FOUND IN SOURCE.

Be adversarial. If everything comes back VERIFIED, treat that as a signal to
re-check your own strictness, not as confirmation the log is perfect.
```

**Why a separate pass matters:** a single model asked to "extract and check your
work" in one go tends to rubber-stamp its own first answer — it already committed
to a framing in the extraction step. A second pass, run separately, with an
explicitly adversarial instruction, is what actually catches the scope errors.
This is the same reason a second reviewer catches things an author doesn't.
