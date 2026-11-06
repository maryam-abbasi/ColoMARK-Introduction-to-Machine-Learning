# ColoMARK — Introduction to Machine Learning

Materials for the 2.5-hour hands-on ML session, part of the **Workshop on
Machine Learning methods**, SBBS, University College
Dublin, 6 November 2026.

Session lead: Maryam Abbasi (CIAC-PLDIS, Polytechnic University of Santarém).

---

## Files

| File | Who it is for |
|---|---|
| `ColoMARK_Intro_to_ML_Student.ipynb` | Share with participants. 76 cells. Exercises left incomplete; **no answers**. |
| `ColoMARK_Intro_to_ML_Instructor.ipynb` | Yours only. 100 cells — the same sequence plus 12 facilitator notes, 11 answer keys, and the 2 `# TODO` cells completed. |
| `README.md` | This file. |

Both notebooks are shipped **without stored outputs**, so participants see the
results appear as they run the cells.

---

## Running them

### Google Colab (what the session uses)

1. Upload both `.ipynb` files to Google Drive, or to a GitHub repo.
2. From Drive: right-click → *Open with* → *Google Colaboratory*.
   From GitHub: `colab.research.google.com` → *GitHub* tab → paste the repo URL.
3. *Share* → *Anyone with the link* → **Viewer**. Participants open it and click
   *Copy to Drive* to get their own editable copy.
4. Nothing to install. Every package used is pre-installed in Colab.

### Locally (if anyone prefers)

```bash
pip install numpy pandas matplotlib scikit-learn jupyterlab
jupyter lab
```

---

## Requirements

| Package | Minimum | Verified on |
|---|---|---|
| Python | 3.9 | 3.13.18 |
| numpy | 1.24 | 2.5.3 |
| pandas | 2.0 | 3.0.5 |
| matplotlib | 3.7 | 3.11.2 |
| scikit-learn | 1.3 | 1.9.1 |

scikit-learn ≥ 1.3 is the real constraint (`OneHotEncoder(drop="if_binary")`
inside a `ColumnTransformer`). Colab's current defaults satisfy everything above.

**No internet access is needed at any point** — no downloads, no external data,
no API calls. The notebooks run offline from a clean kernel.

---

## The data

All exercises use a **synthetic** colorectal liquid-biopsy dataset generated
inside the notebook by `make_colomark_data()` — no CSV, no download, identical
numbers for everyone via `RANDOM_STATE = 42`.

240 patients, 13 candidate predictors, 26.2% cases (63 events — about 4.8 events
per predictor, deliberately realistic for this field). Built to contain the
teaching problems: missing values (`cea_ng_ml` 40, `crp_mg_l` 25), class
imbalance, three uninformative technical columns, a subgroup of "low shedder"
cancers that look like controls, and one leaky variable
(`days_to_colonoscopy`) used for the leakage demonstration in Part 6.

**It contains no real patients and no validated biomarkers.** Variable names are
realistic so the workflow feels familiar; the values are simulated. The notebooks
state this at the top, at the point of generation, and in the closing cell. No
result produced is clinical evidence.

### Optional real public dataset

If you want a real dataset for follow-up work (not for the session itself), the
**Breast Cancer Wisconsin Diagnostic** data ships with scikit-learn
(`sklearn.datasets.load_breast_cancer`) and needs no download. It fits the
workflow, but it is not a liquid-biopsy problem, it is unusually clean, it has no
missing values, and it is nearly separable — so it teaches the mechanics well and
the pitfalls badly. That is why the session does not use it. The workshop depends
on no external download.

---

## Agenda — 150 minutes

| # | Part | Min | Cumulative |
|---|---|---|---|
| 1 | Introduction — what ML can and cannot answer; prediction vs explanation | 15 | 0:15 |
| 2 | Research question and data | 20 | 0:35 |
| 3 | Hands-on workflow | 35 | 1:10 |
| 4 | Small exercise | 10 | 1:20 |
| 5 | Model evaluation | 30 | 1:50 |
| 6 | Common pitfalls | 25 | 2:15 |
| 7 | Group exercise and discussion | 15 | 2:30 |

Start 13:30 GMT, finish 16:00 GMT.

**There is no scheduled break.** Part 4 is the de facto break — participants work
alone for ~8 minutes with cameras off. If you want a hard break as well, insert 5
minutes between Parts 4 and 5 and take it out of Part 6.

---

## Facilitation notes

- **Run Part 3 as guided live-coding**, not independent work. Only two or three
  of this cohort have used ML before. You run a cell, they run it, you wait for
  the chat before moving on.
- **Nine interaction points**: seven CHAT CHECK-INs, one individual exercise
  (Part 4), one breakout (Part 7) — roughly one every 8–12 minutes. Every one has
  a suggested answer in the instructor notebook.
- **Cut order if you run late**: bootstrap CI cell (Part 5), `class_weight`
  comparison (Part 6), decision-tree overfitting demo (Part 6). Do **not** cut
  either leakage demo or Part 7.
- **Part 7 needs breakout rooms** (3–4 people per group, 8 minutes). If Teams
  breakouts are not set up, the instructor notebook has a main-room fallback.

---

## Assumptions made

Stated plainly, since not all of these were confirmed:

1. **Participants have laptops and can open Colab.** Confirmation was requested
   from Neil but is not in hand. If anyone cannot run code, they can still follow
   the screen-share — but the exercises in Parts 3, 4 and 6 lose most of their
   value. A pre-session reply from each student confirming Colab access is worth
   chasing.
2. **Python background is mixed and mostly minimal.** The Python primer is an
   optional reference section outside the 150 minutes rather than taught content,
   per the agenda. If the pre-session replies show the group is weaker than
   assumed, budget 5 extra minutes at the start of Part 3 and take it from Part 6.
3. **The notebook link is distributed before the session.** Participants opening
   Colab for the first time during Part 3 will lose that part.
4. **Teams is the platform**, with chat visible to the facilitator throughout.
   Every check-in is designed for chat rather than voice, so it works with
   cameras off and does not require anyone to screen-share on demand.

## Known limitations

- Single train/test split throughout. This is a teaching simplification and the
  notebooks say so repeatedly; it is not a validation strategy.
- Nested cross-validation is mentioned but not taught — out of scope for 150
  minutes with this audience.
- Calibration is named as a gap in the metrics discussion but not demonstrated.
  It is the most obvious candidate for a follow-up session.
- Exact third decimal places may shift with numpy/scikit-learn versions. The
  instructor answer keys quote the values obtained with the versions in the table
  above; the qualitative conclusions do not depend on them.
- The illustration prompts in the notebooks are **prompts only** — no images are
  generated or embedded, so the notebooks stay small and offline.

---

*All data is synthetic. Nothing in these materials constitutes clinical evidence
or supports any diagnostic or treatment decision.*
