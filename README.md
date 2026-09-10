# Target Six

A single-file practice app for Florida's **FAST Grade 6** assessments — Mathematics and ELA Reading — built to match the published test blueprint rather than approximate it.

No build step, no dependencies, no tracking. Open `index.html` in a browser and it works, including offline.

**Live:** https://jimbodakilla.github.io/kissandtell/

---

## What it does

**Mathematics — 46 benchmarks, generated, not stored.**
Every one of the 39 Grade 6 B.E.S.T. benchmark groupings, plus 6 Grade 7 benchmarks in an *Above Grade* deck. Problems are built from parameters at run time, so they never repeat — 685 distinct question wordings, tens of thousands of distinct problems. Each item ships with a worked solution and, where a wrong answer matches a known misconception, a targeted explanation of that specific trap.

**ELA Reading — 12 original passages, 169 questions.**
Prose fiction, a sonnet, a ballad, a drama scene, a myth retelling, memoir, informational science, argument, and paired cross-genre sets. Plus a regenerating vocabulary engine covering Greek and Latin roots, affixes, context clues and connotation.

**Both subjects run the real item formats.** Plain multiple choice is a minority of the actual FAST paper, so this implements the rest: multiselect (no partial credit), two-part evidence-based items, categorisation tables, inline "complete the statement" dropdowns, numeric response, click-to-plot number lines, an inequality graph builder, and a coordinate grid.

---

## Built to the published blueprint

| Grade 6 ELA Reading | Share of test |
|---|---|
| Reading Prose and Poetry (`R.1.1`–`R.1.4`) | 25–35% |
| Reading Informational Text (`R.2.1`–`R.2.4`) | 25–35% |
| Reading Across Genres & Vocabulary (`R.3.1`, `R.3.3`, `R.3.4`, `V.1.2`, `V.1.3`) | 35–50% |

36–40 items, up to 90 minutes, computer adaptive.

| Grade 6 Mathematics | Share of test |
|---|---|
| Number Sense and Operations | 33–42% |
| Algebraic Reasoning | 25–36% |
| Geometric Reasoning, Data Analysis and Probability | 25–36% |

39 benchmark groupings. A four-function calculator and a reference sheet are provided on the real test — the reference sheet is reproduced in the app, including what it *doesn't* give you (no triangle, parallelogram, trapezoid or surface-area formula).

---

## The five-day plan

The Reading side opens on a guided five-day run-up:

1. **Formats and vocabulary** — meet every question format once, explained as you go
2. **Prose and poetry** — `R.1.1`–`R.1.4`
3. **Informational text** — `R.2.1`–`R.2.4`
4. **Across genres and rhetoric** — `R.3.1`, `R.3.3`, `R.3.4`
5. **Full mock, then repair** — 36 items, 90 minutes, no feedback → review every miss → **fresh questions on those exact skills**

That last step is the point. A worked solution isn't teaching until it has been re-tested. Missed skills return once inside the same session and again a day later; a correct re-test pushes the next visit out further.

## Other features

- **Mock papers** for both subjects, timed, no feedback until the end, reported by reporting category with seconds-per-question
- **Tiered difficulty** (I / II / III) with a mastery ladder, and a control to start at Tier III for students already working above grade level
- **Coach view** — a parent-facing panel showing recurring error patterns, skills that are slow rather than wrong, and what's due for review
- **Light and dark themes**, keyboard navigation, progress saved in `localStorage`

## Adapting it

The "Target Six" deck points at six specific benchmarks from one student's item analysis. To aim it at your own student, edit the `SIX` array near the top of the script:

```js
const SIX=['MA.6.NSO.1.1','MA.6.NSO.4.2','MA.6.AR.1.3',
           'MA.6.AR.1.2','MA.6.GR.2.2','MA.6.DP.1.3'];
```

Passages live in the `PASSAGES` array and follow a documented shape — adding your own needs no engine changes.

## Accuracy

Every generated item is verified before it reaches a student: a validation gate rejects malformed items, and a separate check re-evaluates each printed expression and compares it against its own stored answer key. That second check exists because structural validation alone once passed a generator that printed `8 − (−5)` and keyed the answer as `3`.

## Licence

MIT. The passages and questions are original work.
