# Claims Log: TruthfulQA (Lin, Hilton & Evans, 2021/2022)

arXiv:2109.07958v2 — https://arxiv.org/abs/2109.07958

Extracted by: (workshop demo) | Verified by: (workshop demo, adversarial pass) | Date: 2026-08-26

| # | Claim (plain language) | Quote (verbatim) | Scope | Type | Caveats | Verification status |
|---|---|---|---|---|---|---|
| 1 | TruthfulQA is an 817-question, 38-category benchmark built adversarially to elicit imitative falsehoods | "The benchmark comprises 817 questions that span 38 categories... We crafted questions that some humans would answer falsely due to a false belief or misconception." | The benchmark itself | methodology | Questions filtered against GPT-3-175B during construction | VERIFIED |
| 2 | Best-performing model (one model, one prompt) was truthful on 58% of questions vs. 94% for humans; false-and-informative 42% of the time vs. 6% for humans | "the best-performing model (GPT-3-175B with 'helpful' prompt) was truthful on 58%... while human performance was 94%... false and informative 42% of the time (compared to 6%...)" | GPT-3-175B, "helpful" prompt specifically | stated finding | Best case across prompts tested, not typical (see row 7) | VERIFIED |
| 3 | Larger models are less truthful **specifically on TruthfulQA's adversarially-selected questions** — not a general finding about truthfulness or capability | "...the largest models were generally less truthful (Fig. 2)..." + "[on matched controls] truthfulness... improves with model size for all model families... largest GPT-3 and GPT-Neo/J achieve high absolute truthfulness scores." | The adversarial benchmark only; on matched non-adversarial controls, truthfulness *improves* with size for every family (Sec. 4.3) | stated finding, with an explicit authors'-own scope-limiting experiment | Do not cite as "scaling makes models less truthful" in general | VERIFIED (corrected — see transcript row 3) |
| 4 | UnifiedQA is more truthful than the GPT families but least informative | "The UnifiedQA models generally do better on truthfulness than the three GPT families, but these models are also the least informative..." | Per model family, generation task | stated finding | Authors' probable-cause explanation (fine-tuning objective), not certain | VERIFIED |
| 5 | Inverse scaling also appears on the multiple-choice task; no model beats random guessing there | "...the larger models also perform worse than smaller ones... GPT-Neo/J 6B was 12% less truthful than GPT-Neo/J 125M. No models significantly outperformed random guessing." | Multiple-choice task specifically | stated finding | — | VERIFIED |
| 6 | GPT-judge (finetuned automated metric) predicts human truthfulness judgments with 90-96% accuracy on held-out models | "The finetuned GPT-judge model is able to predict human evaluations of truthfulness with 90-96% accuracy on held-out models." | "Held-out" = leave-model-out evaluation, not a generic test split | stated finding | Lower (89.5%) accuracy on human-baseline answers, which it never trained on | VERIFIED |
| 7 | Prompt choice significantly changes truthfulness scores but not the true-and-informative rate | "Different prompts for GPT-3-175B had a significant impact on truthfulness but not on the percentage of true and informative answers." | GPT-3-175B specifically | stated finding | — | VERIFIED |

## Notes for the team

Row 3 is load-bearing for anything in our own work that cites "TruthfulQA
shows scaling reduces truthfulness." It doesn't, in general — it shows scaling
reduces truthfulness *on an adversarially-constructed benchmark specifically
designed to target that failure mode*, and increases it on matched ordinary
questions. If our own paper cites this result, cite it with that scope, or
we're reproducing the exact oversimplification this log exists to catch.
