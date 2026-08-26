# Annotated session: systematic extraction + verification

Source: `source/paper_excerpts.md` (verbatim, page-cited excerpts read directly
from the PDF, kept alongside this log so every row below is independently
checkable).

## Step 1 — Extraction pass (Prompt 1, `prompts/01_extract_claims.md`)

Run against Sections 1.1, 4.1, 4.2, 4.3 and 4.4 of the paper. Raw output,
lightly reformatted into a table for readability — **nothing about the content
was changed or corrected at this stage**, including the mistake in row 3,
which is left exactly as it first came out. That mistake is the point of
Step 2.

| # | Claim | Quote | Scope | Type | Caveats |
|---|---|---|---|---|---|
| 1 | TruthfulQA is an 817-question, 38-category benchmark built adversarially to elicit imitative falsehoods | "The benchmark comprises 817 questions that span 38 categories... We crafted questions that some humans would answer falsely due to a false belief or misconception." | The benchmark itself, not a model result | methodology | Questions were filtered against GPT-3-175B specifically during construction (adversarial procedure) |
| 2 | The best-performing model was truthful on 58% of questions vs. 94% for humans, and gave false-but-informative answers 42% of the time vs. 6% for humans | "the best-performing model (GPT-3-175B with 'helpful' prompt) was truthful on 58% of questions, while human performance was 94%... generated answers that were both false and informative 42% of the time (compared to 6% for the human baseline)" | One specific model + one specific prompt (GPT-3-175B, "helpful"), not "models" generally | stated finding | Prompt choice matters a lot here (see row 7) — this is the best case across prompts, not typical |
| 3 | Larger models are less truthful than smaller ones — an "inverse scaling" effect | "Across different model families, the largest models were generally less truthful (Fig. 2)... This 'inverse scaling' trend contrasts with most tasks in NLP, where performance improves with model size." | **holds generally — reflects models getting worse at truthfulness as they scale** | stated finding | — |
| 4 | UnifiedQA is more truthful than the GPT families but least informative | "The UnifiedQA models generally do better on truthfulness than the three GPT families, but these models are also the least informative — probably because they are fine-tuned for QA tasks with a different format and objective." | Per model family, generation task | stated finding | Authors' own probably-causal explanation (fine-tuning objective), flagged as such, not certain |
| 5 | The inverse-scaling effect also shows up on the multiple-choice task, and no model beats random guessing there | "For the multiple-choice task... the larger models also perform worse than smaller ones... GPT-Neo/J 6B was 12% less truthful than GPT-Neo/J 125M. No models significantly outperformed random guessing." | Multiple-choice task specifically (separate from the generation task in rows 2–4) | stated finding | — |
| 6 | GPT-judge, a finetuned automated metric, predicts human truthfulness judgments with 90-96% accuracy on held-out models | "The finetuned GPT-judge model is able to predict human evaluations of truthfulness with 90-96% accuracy on held-out models." | "Held-out" = models excluded from GPT-judge's own finetuning set (leave-model-out evaluation), not a generic test split | stated finding | Human-baseline accuracy was lower (89.5%) — GPT-judge was never trained on human answers |
| 7 | Prompt choice significantly changes truthfulness scores but not the true-and-informative rate | "Different prompts for GPT-3-175B had a significant impact on truthfulness but not on the percentage of true and informative answers." | GPT-3-175B specifically (only model with multiple prompts tested in main results) | stated finding | — |

## Step 2 — Verification pass (Prompt 2, `prompts/02_verify_claims.md`)

Run in a separate pass against the table above and the source excerpts.

> **Row 3 — SCOPE ERROR / MISSING CAVEAT.**
> The quote is accurate, but "holds generally — reflects models getting worse
> at truthfulness as they scale" is not what the paper's own evidence
> supports, and the paper says so directly. Section 4.3 ("Controls")
> describes an experiment on *matched control questions* — same syntax as
> TruthfulQA, edited 1-3 words to remove the misconception being probed — and
> states: **"truthfulness on the matched controls improves with model size
> for all model families and... the largest GPT-3 and GPT-Neo/J achieve high
> absolute truthfulness scores."**
>
> That's the opposite direction. The inverse-scaling effect is specific to
> TruthfulQA's adversarially-selected questions — it is not evidence that
> larger models are less truthful, or less capable of being truthful, in
> general. On ordinary non-adversarial questions of the same form, bigger
> models are *more* truthful, for every family tested. The paper's own
> preferred explanation (Section 1.1, and reinforced by the Controls result)
> is that larger models are *better* at learning the training distribution,
> which cuts both ways: better on ordinary questions, worse specifically where
> the training distribution itself contains the false belief being tested.
>
> This is also, empirically, the single most common way this paper gets
> mis-cited: "TruthfulQA showed bigger models lie more" as a general claim
> about scaling, dropping the adversarial-construction caveat that the paper
> treats as central to its own interpretation (all of Section 4.3 is
> specifically about ruling out the more general reading).
>
> All other rows: quotes found verbatim in source, scope matches what the
> text supports, no un-flagged caveats found nearby. **VERIFIED.**

## Step 3 — Corrected row

| # | Claim | Quote | Scope (corrected) | Type | Caveats |
|---|---|---|---|---|---|
| 3 | Larger models are less truthful specifically on TruthfulQA's adversarially-selected questions — not a general finding about truthfulness or capability | "Across different model families, the largest models were generally less truthful (Fig. 2)..." + "[On matched controls,] truthfulness... improves with model size for all model families and... the largest GPT-3 and GPT-Neo/J achieve high absolute truthfulness scores." | **The adversarial TruthfulQA benchmark specifically.** On matched non-adversarial control questions of identical syntax, truthfulness improves with size for every family tested (Section 4.3, "Controls"). | stated finding, with an explicit authors'-own scope-limiting experiment | Do not cite as "scaling makes models less truthful" or "bigger models are worse at truthfulness" without this caveat — the paper's own Section 4.3 exists specifically to rule out that broader reading |

This corrected table (all 7 rows, with row 3 fixed) is `02_claims_table.md`.
