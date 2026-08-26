# Workshop demo: a claims log for AI-assisted paper reading

**What this is.** The worked example for a 30-minute workshop on turning ad hoc
AI paper-summarization into a small, repeatable, verifiable habit. Everything
here is real output from actually running the workflow once, on a real paper
(TruthfulQA, Lin/Hilton/Evans 2021), not a mocked-up illustration.

**The 90-second version:** ask an AI to summarize a paper and you'll usually
get something fluent and mostly right. The failure mode isn't factual
error — it's *scope creep*: a finding that holds under one specific condition
quietly becomes a finding that holds "in general." That's genuinely hard to
catch by re-reading the summary, because the summary reads perfectly
naturally either way. The fix demonstrated here is structural, not
attitudinal: extract claims with pinned quotes and explicit scope fields, then
run a second, separate, adversarial pass whose only job is to find where the
first pass over-generalized. Below, that two-pass process catches a real
scope error in row 3 of the claims table — a claim that, left as first
extracted, would have said close to the opposite of what the paper's own
Section 4.3 argues.

## Files, in the order to read them

1. **`session/00_naive_summary.md`** — the baseline. What you get today from
   "summarize this paper for me." Genuinely good, and contains one
   consequential scope error.
2. **`prompts/`** — the three-prompt library: extraction, adversarial
   verification, and a shared log template. Paper-agnostic; copy these into
   your next Claude Code session on any paper.
3. **`session/01_annotated_transcript.md`** — the actual run: extraction pass
   (with the scope error left in, as it first came out), then the
   verification pass catching and fixing it, with the reasoning shown.
4. **`session/02_claims_table.md`** — the final, corrected, shareable output.
   This is what would go in a team's shared research log.
5. **`session/03_naive_vs_systematic_diff.md`** — the naive summary and the
   verified claim side by side, with why the gap matters.
6. **`source/paper_excerpts.md`** — the verbatim, page-cited source passages
   everything above is checked against, so none of this asks you to trust the
   AI's citations either.

## Try it yourself

Pick any paper your team is reading. Paste `prompts/01_extract_claims.md`'s
prompt block plus the paper into a session. In a **separate** turn or session,
paste `prompts/02_verify_claims.md`'s prompt block plus the extraction output
and the paper. Log the result in `prompts/claims_log_template.md`'s format
somewhere the whole team can see it. Total overhead: a few minutes per paper,
once, for a claim that stays checkable for the life of the project instead of
degrading into "I think the paper said something like..." three weeks later.
