# Pre-Competition Psychological Risk Profiling of Athletes

An interactive companion to the paper. Ten sports-psychology constructs are
detected in athlete text and fused, linearly and interpretably, into a 0–1 risk
index — alongside a cognitive layer (brain atlas, cognitive load, closed-loop
neurofeedback) that runs entirely on **generated signals**.

## Read this before quoting any number

**No number in this app is an accuracy.** Every score shown is *agreement with
planted labels* on a synthetic corpus. The provenance stamp that says so is not
a convention here — `ScoreSurface.__post_init__` raises if it is missing, so a
number in this project cannot be constructed without it.

**Nothing here measures anybody.** No athlete was recorded, no sensor was
attached, no headset exists. Every biosignal is produced by this project's own
simulator from a fixed seed, and `BiosignalWindow.__post_init__` refuses to
construct a window whose stamp lacks the `SIMULATED` token.

**The brain atlas is not imaging.** This project holds no neuroimaging data and
cites no neuroimaging study. Each mapping carries an `instrument_anchor` (a
reference supporting *the construct*, which says nothing about the brain) and a
`network_evidence` grade that is always `none_in_repository` or
`outside_athlete_population`. Two of the ten constructs are deliberately left
unmapped. The figure is a hypothesis map — something to disagree with.

**The neurofeedback page is a demo and an intervention.** It closes a loop
against a generated signal and trains nobody. `require_simulated()` refuses any
non-simulated source, and `simulated` is a read-only property with no setter.
Before this runs against any person it needs ethics approval, a clinician in the
loop, and the ethics and model-card documents updated first.

## The five pages

| Page | What it does |
|---|---|
| **Dashboard** | The ten construct tiles and the fused index for a committed example |
| **Signal detail** | The words behind one construct — the receipts |
| **Score my own text** | Runs a live lexicon scorer on text you paste; weaker than the replay path, and the page says by how much |
| **Brain atlas** | Construct → brain network hypothesis map, with evidence grades on the figure |
| **Cognitive load** | Narrated audio with a simulated heart-rate trace and load index moving in time with it |
| **Neurofeedback (demo)** | A closed loop: ring versus target, on a generated alpha/theta ratio |

## Two findings the app does not hide

**104 of 120 index-moving drivers had no words behind them.** Signals that moved
the number while the system could not point at any text justifying it. This is
reported rather than quietly dropped.

**Four of the ten constructs are counted as zero.** Their direction is
two-sided — high attentional focus can be good news or bad news — and a signal
whose sign is unknown cannot be added to a risk number honestly. They are
detected, displayed, and weighted zero. The policy selector lets you see what an
optimistic or pessimistic reading would cost.

**Short-window HRV moves the wrong way.** On ~12-beat windows every HRV
statistic tested reversed direction; 12 beats cannot support a spectral
estimate. HRV is therefore absent from the narrated panel's weights, and a test
pins the finding so it is not "fixed" back.

## Running it locally

```bash
pip install -r requirements.txt
streamlit run dashboard/app.py
```

Set `SRN_COGNITIVE_LAYER=0` to hide the three cognitive-layer pages. The layer is
on by default; only an explicit disabling value turns it off.

## Scope of this deployment

This is the dashboard only. Training code, the transformer stack, the evaluation
harness and the paper live in the full repository and are not deployed here —
this app replays committed fixtures so that anyone opening it sees the identical
picture.
