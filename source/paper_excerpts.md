# Source excerpts (verbatim, page-cited)

Paper: Lin, Hilton & Evans (2021/2022), "TruthfulQA: Measuring How Models Mimic
Human Falsehoods." arXiv:2109.07958v2.

**Note on provenance:** these excerpts were read directly from the PDF pages
(not fetched/paraphrased by an intermediate tool) so that every quote below is
independently checkable against the source. Page numbers refer to the PDF's own
pagination.

---

## Abstract (p.1)

"We propose a benchmark to measure whether a language model is truthful in
generating answers to questions. The benchmark comprises 817 questions that span
38 categories, including health, law, finance and politics. We crafted questions
that some humans would answer falsely due to a false belief or misconception. To
perform well, models must avoid generating false answers learned from imitating
human texts. We tested GPT-3, GPT-Neo/J, GPT-2 and a T5-based model. The best
model was truthful on 58% of questions, while human performance was 94%. Models
generated many false answers that mimic popular misconceptions and have the
potential to deceive humans. The largest models were generally the least
truthful. This contrasts with other NLP tasks, where performance improves with
model size. However, this result is expected if false answers are learned from
the training distribution. We suggest that scaling up models alone is less
promising for improving truthfulness than fine-tuning using training objectives
other than imitation of text from the web."

## Section 1.1, Contributions (p.2)

"Baselines have low truthfulness. We tested GPT-3 (Brown et al., 2020), GPT-Neo/J
(Wang and Komatsuzaki, 2021), and UnifiedQA (based on T5 (Khashabi et al., 2020))
under a range of model sizes and prompts. Under human evaluation, the
best-performing model (GPT-3-175B with "helpful" prompt) was truthful on 58% of
questions, while human performance was 94% (Fig. 4). This model also generated
answers that were both false and informative 42% of the time (compared to 6% for
the human baseline). Such informative answers, which often mimic popular
misconceptions, are more likely to deceive."

"Larger models are less truthful. Across different model families, the largest
models were generally less truthful (Fig. 2). This "inverse scaling" trend
contrasts with most tasks in NLP, where performance improves with model size
(Brown et al., 2020; Kaplan et al., 2020). One explanation of this result is that
larger models produce more imitative falsehoods because they are better at
learning the training distribution. Another explanation is that our questions
adversarially exploit weaknesses in larger models *not* arising from imitation of
the training distribution. We ran experiments aimed to tease apart these
explanations (Section 4.3)."

## Figure 2 caption (p.3)

"Figure 2: Larger models are less truthful. In contrast to other NLP tasks,
larger models are less truthful on TruthfulQA (top). Larger models do better on
questions that exactly match the syntax of TruthfulQA but do not probe
misconceptions (bottom). Figure 3 gives a concrete example of larger sizes being
less truthful."

(The "top" chart plots average truthfulness on the actual TruthfulQA benchmark,
declining with model size for GPT-3, GPT-Neo/J and GPT-2. The "bottom" chart
plots average truthfulness on matched *control trivia questions* — same syntax,
no misconception being probed — and rises with model size for every family
shown.)

## Section 4.2, "Larger models are less truthful" (p.6, full)

"Figure 2 shows that larger models generally do worse than smaller models in the
same family (inverse scaling). For example, the largest GPT-Neo/J is 17% less
truthful than a model 60x smaller. The UnifiedQA models generally do better on
truthfulness than the three GPT families, but these models are also the least
informative — probably because they are fine-tuned for QA tasks with a different
format and objective (Khashabi et al., 2020).

While larger models were less truthful, they were more informative. This
suggests that scaling up model size makes models more capable (in principle) of
being both truthful and informative.

For the multiple-choice task (where models choose answers rather than generating
them), the larger models also perform worse than smaller ones (Fig. 4c). For
example, GPT-Neo/J 6B was 12% less truthful than GPT-Neo/J 125M. No models
significantly outperformed random guessing. The concordance between the
generation task and the multiple-choice task suggests that the tendency of
larger models to perform worse is not an artifact of human evaluation or of the
hyperparameters we used for generating answers."

## Section 4.3, "Interpretation of results" (p.6–p.7, key passages)

"If a model returns a false answer to a question in our benchmark, this could be
because the answer is an imitative falsehood. However, it could also be caused
by the syntax or style of the question. These are "non-imitative" falsehoods, as
they are not incentivized by the model's training objective."

"**Controls.** We ran an experiment testing models on *matched control*
questions. Each question was constructed by editing 1-3 words of a question in
TruthfulQA... The edits preserve the form of the questions but turn them into
straightforward trivia or common-sense questions. If TruthfulQA questions
exploit non-imitative weaknesses, we would expect many of the matched controls to
exploit similar weaknesses. **Yet Figure 2 shows that truthfulness on the matched
controls improves with model size for all model families and that the largest
GPT-3 and GPT-Neo/J achieve high absolute truthfulness scores.**"

"**Paraphrases.** We ran an experiment testing models on paraphrases of the
TruthfulQA questions... Overall, we find that truthfulness scores for models do
not change substantially on the paraphrased questions... In particular, the
largest GPT-3 and GPT-Neo/J models still perform worse than the smaller models in
the family."

"This evidence suggests that the poor performance of models on TruthfulQA is not
explained by most questions exploiting a (non-imitative) weakness to a
particular syntax or form."

## Section 3.2 / 4.1, prompts and headline numbers (p.5–p.6)

"Different prompts for GPT-3-175B had a significant impact on truthfulness but
not on the percentage of true and informative answers (Appendix B.6)."

"The human participant produced 94% true answers (Fig. 4). 87% of their answers
were both true and informative. Across all model sizes and prompts, the best
model (GPT-3-175B with helpful prompt) produced 58% true answers and 21% true and
informative answers. This model gave false and informative answers 42% of the
time (compared to 6% for the human participant)."

## Section 8, Ethics and Impact (p.9)

"Strong performance on TruthfulQA does not imply that a model will be truthful in
a specialized domain. But poor performance does indicate a lack of robustness."

"TruthfulQA does not cover any topics with extreme specificity but instead has
shallow coverage of general-knowledge topics."
