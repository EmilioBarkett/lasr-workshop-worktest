# Prompt 1 — Extract claims (quote-pinned)

Use this on a section, or the whole paper if it's short. Paste the paper text (or
attach the PDF) alongside it.

```
You are helping me build a traceable claims log for a paper I'm reading for
research purposes. For [SECTION NAME or "the full paper"], extract every
empirical or methodological claim the authors make — not background or
motivation, just things I could later cite as "the paper found/showed/argues X."

For each claim, output:
- Claim: one sentence, in your own words
- Quote: the exact sentence(s) from the paper this is based on — verbatim, with
  enough surrounding context to be unambiguous
- Scope: what population/condition does this claim actually hold over? (e.g. "all
  6 models" vs. "one model, under one condition"). If the text specifies a scope,
  state it explicitly. If you're not sure, say so — don't guess.
- Type: [stated finding / authors' interpretation or speculation / my inference —
  not stated in the text]
- Caveats: any limitation, exception, or qualifier the authors attach to this
  claim — even if it's in a different sentence or paragraph nearby

Rules:
- Do not paraphrase away exceptions, model names, dataset names, or numbers.
- If a claim only holds for one dataset/model/condition, do not generalize it to
  "models" or "results" in general — that's the single most common way this goes
  wrong.
- If you can't find a specific claim on something in the given text, say so rather
  than inferring one.
```

**Why it's shaped this way:** the "Scope" and "Caveats" fields exist specifically
to fight the failure mode a fast summary produces — quietly widening "this one
model, under this one condition" into "models" or "results" in general. Making
the model state scope explicitly, as a separate field, makes the generalization
a decision it has to notice, instead of a decision it can make trying to move
fast, silently, in a topic sentence.
