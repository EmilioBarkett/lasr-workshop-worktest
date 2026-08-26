# The catch: naive summary vs. verified claims log

## What the naive pass said

> "The most important finding is that **larger models are less truthful than
> smaller ones**. This 'inverse scaling' result holds across every model
> family tested (GPT-3, GPT-Neo/J, GPT-2), and it's the opposite of what
> you'd normally expect, since bigger models usually do better on NLP
> benchmarks. The authors argue this happens because bigger models are better
> at learning the training distribution, so they're more likely to reproduce
> the false beliefs that appear frequently in that distribution — **meaning
> scaling up model size alone won't fix truthfulness, and might make it
> worse.**"

## What the paper actually supports (verified claims log, row 3)

> Larger models are less truthful **specifically on TruthfulQA's
> adversarially-selected questions**. On matched non-adversarial control
> questions — identical syntax, no misconception being probed — "truthfulness
> on the matched controls improves with model size for all model families...
> the largest GPT-3 and GPT-Neo/J achieve high absolute truthfulness scores"
> (Section 4.3). The paper runs this experiment specifically to rule out the
> broader reading.

## Why this is the failure mode, not a nitpick

The naive summary isn't wrong about any individual number — 58%, 94%, 42%,
90-96% are all correct. It's wrong about **scope**: it silently converts "less
truthful on an adversarial benchmark built to find this exact failure" into
"less truthful in general," which licenses a much stronger and, per the
paper's own Section 4.3, false claim: "scaling up model size alone won't fix
truthfulness, and might make it worse."

That sentence would be a reasonable thing for a fellow to write in a related-
work section, cite in a talk, or build an experimental hypothesis on. It's
also close to the single most common way this paper is mis-cited in the
wild — "TruthfulQA showed bigger models lie more" gets repeated as a general
scaling fact, dropping the exact caveat the paper's authors spent a
subsection ruling in favor of the opposite direction. A reader who only sees
the naive summary has no way to notice this; a reader who sees `02_claims_table.md`
sees the correction sitting right next to the citation, because the workflow
made it structurally impossible to state the claim without also stating its
scope.

This is what "calibration" cashes out to in practice: not being more
suspicious of AI output in general, but having a specific, repeatable place
where scope-widening gets caught before it becomes a sentence in your paper.
