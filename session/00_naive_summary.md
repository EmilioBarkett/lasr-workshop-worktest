# Baseline: the naive ad hoc pass

**Prompt used (exactly what most fellows do today):**

> "Can you summarize the key results of this paper for me? [pasted PDF]"

**Output (unedited, first response, no follow-up questions asked):**

This paper introduces TruthfulQA, a benchmark of 817 questions across 38
categories designed to catch language models generating "imitative
falsehoods" — false answers that mimic human misconceptions rather than
random errors. The questions are adversarially constructed: they're chosen
specifically to be ones models tend to get wrong by parroting popular myths
(e.g. about health, law, and conspiracies).

The headline result is that today's models are much less truthful than
humans: the best model (GPT-3-175B) was truthful on only 58% of questions,
compared to 94% for a human baseline, and it produced answers that were both
false and informative — the most deceptive kind of wrong answer — 42% of the
time.

The most important finding is that **larger models are less truthful than
smaller ones**. This "inverse scaling" result holds across every model family
tested (GPT-3, GPT-Neo/J, GPT-2), and it's the opposite of what you'd normally
expect, since bigger models usually do better on NLP benchmarks. The authors
argue this happens because bigger models are better at learning the training
distribution, so they're more likely to reproduce the false beliefs that
appear frequently in that distribution — meaning scaling up model size alone
won't fix truthfulness, and might make it worse.

They also build an automated "GPT-judge" classifier that can predict human
truthfulness judgments with 90-96% accuracy, offering a cheap substitute for
human evaluation in future work.

---

**This is a genuinely good summary.** It's fluent, well-organized, and the
headline numbers (58%, 94%, 42%, 90-96%) are all correct. That's what makes it
a realistic baseline — this isn't a strawman, it's what a careful researcher
gets in ten seconds from one ad hoc prompt. The problem is in the bolded
sentence, and it's the kind of error that's invisible unless you go back to
the source — see `03_naive_vs_systematic_diff.md`.
