<div align="center">

# 🔧 Autonomous Inventor

**A Claude skill that invents hardware and automation designs through systematic contradiction resolution — not trial and error.**

[![License: MIT](https://img.shields.io/badge/License-MIT-black.svg)](./LICENSE)
[![Platform: Claude](https://img.shields.io/badge/Platform-Claude-orange.svg)](https://claude.ai)
[![Method: TRIZ](https://img.shields.io/badge/Method-TRIZ-blue.svg)](https://en.wikipedia.org/wiki/TRIZ)
[![Type: Skill](https://img.shields.io/badge/Type-Skill-green.svg)](https://support.claude.com/en/articles/12580051-teach-claude-your-way-of-working-using-skills)

<br>

*Anchor on a bad form. Iterate with TRIZ. Reframe the architecture. Loop until the hard problems are designed out — not patched. Then optimize, and optionally file a patent.*

</div>

---

## Why this exists

Most invention methods are linear: brainstorm → prototype → test → repeat. They add parts, tune parameters, and call it done.

This skill does something different. It **names the contradiction** generating the hardest problems, resolves it architecturally using TRIZ, stress-tests the result, and loops back to reframe again if a structural flaw surfaces. One good reframe eliminates clusters of problems that more iteration never could.

When the design converges, it generates a **Python optimization script** for numerical trade-offs and — optionally — a complete **USPTO provisional patent application** ready to file.

> *Design quality is proportional to how precisely you name the contradiction.*

---

## Method

**9 phases · 2 feedback loops · TRIZ throughout**

```
0 Contradictions → 1 Baseline → 2 Iterate → 3 Reframe (TRIZ) → 2B Re-iterate*
                                                  ▲                    │
                                                  │  loop if structural │
                                                  └──── 4 Stress-test ◀┘
                                                              │
                               5 Specialize → 6 Optimize → 7 Final design → 8 Patent†
```

> \* Phase 2B runs only when the reframe shifts the whole architecture.
> The **3↔4 loop** is the engine — expect to traverse it more than once.
> † Phase 8 is offered after Phase 7, or run upfront if requested.

<br>

| Phase | Name | What happens |
|-------|------|-------------|
| **0** | Contradiction inventory | Name technical and physical contradictions *before* designing. Vague contradictions produce vague reframes. |
| **1** | Baseline | Humanoid anchor — deliberately wrong. Every later part must earn its place. Skipped with a reason when absurd. |
| **2** | Iterate (~10 cycles) | `− remove · + add · ± adjust`, each annotated with TRIZ principles. Exposes which contradictions are actually hard. |
| **3** | Reframe | State contradiction precisely → choose separation strategy → apply TRIZ → name what's eliminated. The multiplier step. |
| **2B** | Re-iterate (conditional) | 5–10 fresh cycles on the *new* architecture if the reframe invalidated more than half the Phase 2 decisions. |
| **4** | Stress-test | Brutal failure-mode analysis across 6 dimensions. **Triggers another reframe** if a structural flaw surfaces. |
| **5** | Specialize + autonomy | Define the bounded operating domain. Mechanics solves; AI decides. "Refuse safely" and "detect-and-escalate" are features. |
| **6** | Optimize | Tune within the fixed architecture: FMEA, efficiency, cost/weight, manufacturability, final TRIZ sweep — **plus a Python `scipy.optimize` script** for numerical trade-offs. |
| **7** | Final design | Name · components · full cycle · non-obvious moves · TRIZ citation log · reframe history · residual limits · niche |
| **8** | Provisional patent | Complete USPTO provisional application — cover sheet, background, summary, ASCII drawings with reference numerals, detailed description, claims, abstract, filing checklist. |

---

## TRIZ integration

The skill embeds the full **TRIZ 40 Inventive Principles** woven throughout every phase — not bolted on at the end.

| Where | How TRIZ is used |
|-------|-----------------|
| Phase 2 | Each `−/+/±` move annotated with principle(s) — builds auditable design rationale |
| Phase 3 | Contradiction → separation strategy → goal-to-principle lookup table |
| Phase 4 | P22 (Blessing in disguise) and P11 (Cushion in advance) as stress-test lens |
| Phase 5 | P10, P15, P24, P25 guide the mechanics-vs-AI split |
| Phase 6 | Final sweep with P2, P6, P20 to surface remaining redundancy |
| Phase 7 | TRIZ citation log in the final design output |

<details>
<summary><strong>Appendix A — 40 Inventive Principles (quick reference)</strong></summary>
<br>

All 40 principles grouped by cluster — designed to be scanned mid-invention:

**Segmentation & Structure:** Segmentation · Extraction · Local quality · Asymmetry · Merging · Universality · Nesting · Anti-weight

**Dynamics & Adaptability:** Preliminary anti-action · Preliminary action · Cushion in advance · Equipotentiality · Inversion · Spheroidality · Dynamics · Partial/excessive action

**Geometry & Dimension:** Another dimension · Mechanical vibration · Periodic action · Continuity · Skipping · Blessing in disguise · Feedback · Intermediary

**Surface & Interface:** Self-service · Copying · Cheap short-living · Mechanics substitution · Pneumatics/hydraulics · Flexible shells

**Physical & Material Effects:** Porous materials · Color changes · Homogeneity · Discarding & recovering · Parameter changes · Phase transitions · Thermal expansion · Strong oxidants · Inert atmosphere · Composite materials

Full table with core moves for each principle is in `SKILL.md`.
</details>

<details>
<summary><strong>Appendix B — Separation strategies for physical contradictions</strong></summary>
<br>

When one element must simultaneously be X and not-X:

| Strategy | How | Example |
|----------|-----|---------|
| **In space** | X in one zone, not-X in another | Hard at the contact face, soft behind it |
| **In time** | X at one moment, not-X at another | Rigid during torque, compliant during alignment |
| **By condition** | X in one state, not-X in another | Stiff under load, flexible under none |
| **By system level** | X at part level, not-X at system level | Each spindle floats; the ring is rigid |
</details>

<details>
<summary><strong>Appendix C — Contradiction-to-principle lookup (mechanical / automation)</strong></summary>
<br>

| Tension | Try first |
|---------|-----------|
| Strength vs. weight | P1, P7, P8, P40 |
| Precision vs. speed | P10, P15, P21, P28 |
| Stability vs. mobility | P5, P8, P12, P13 |
| Torque vs. reaction force | P5, P13, P14, P25 |
| Sensing reliability vs. environment | P3, P10, P15, P23 |
| Grip force vs. surface damage | P3, P9, P16, P24 |
| Complexity vs. reliability | P2, P6, P25, P27 |
| Range vs. accuracy | P15, P16, P17, P23 |
| Cost vs. performance | P6, P26, P27, P35 |
| Autonomy vs. safety | P11, P23, P24, P25 |
</details>

---

## Python optimization (Phase 6)

When the design has coupled numerical parameters, the skill generates a ready-to-run `scipy.optimize` script:

```python
# Objective function, physical constraints, and bounds
result = differential_evolution(objective, bounds, seed=42, tol=1e-8)

# Results table: parameter | optimal value | units | note
# Sensitivity block: ±10% perturbation → % impact on objective
```

Covers: motor sizing, gear ratios, beam dimensions, cost/weight/speed trade-offs, thermal margins. Multi-objective (Pareto) sweep when two objectives conflict. Skipped with a one-line reason if no meaningful numerical parameters exist.

---

## Provisional patent (Phase 8)

After Phase 7, the skill optionally generates a complete **USPTO provisional utility patent application** establishing a 12-month priority date (35 U.S.C. 111(b)):

| Section | Content |
|---------|---------|
| Cover sheet | USPTO Form SB/16 data |
| Background | Field, prior art, problem statement drawn from Phase 0 contradictions |
| Summary | Broadest inventive concept, advantages linked to Phase 3 reframe payoffs |
| Drawings | ASCII line drawings with reference numerals; draftsperson-ready descriptions |
| Detailed description | Component-by-component, operating cycle, 2–3 alternative embodiments (enables POSITA per 35 U.S.C. 112) |
| Claims | ≥1 independent + 3–5 dependent claims (apparatus and method formats) |
| Abstract | ≤150 words |
| Filing checklist | Patent Center URL, fee note, drawings spec (37 C.F.R. 1.84), 12-month non-provisional deadline |

> *This is a drafting aid, not legal advice. Review with a registered patent attorney or agent before filing.*

---

## Core principles

| Principle | Why it matters |
|-----------|---------------|
| **Contradictions are the signal** | Where something is hard to design, a contradiction hides. Name it; don't just add parts. |
| **Loop on the reframe** | The 3↔4 cycle is where good designs become great. One reframe is rarely enough. |
| **Mechanics before AI** | Compliance, self-location, and passive alignment beat precision perception. |
| **Quantify what matters** | Loads, torques, tolerances, masses, cycle time, cost. Estimates beat hand-waving; flag them. |
| **Honesty over salesmanship** | A design with stated limits beats one that claims everything. |
| **Function dictates form** | Reject anthropomorphism unless a humanoid feature genuinely earns its place. |

---

## Worked example

**Task:** change a flat tire autonomously.

**Contradiction (Phase 0):** high torque needs a heavy reaction base — but heavy hurts mobility. The base must be both heavy (stability) and light (portability).

**Reframe (Phase 3):** react torque *internally* through a multi-spindle nutrunner ring `[P5, P13]`; re-reference the whole machine off the **hub** rather than the floor `[P13]`; let mechanical compliance absorb alignment `[P10, P15]`. Eliminates jack instability, grounded-torque dependence, and sub-millimeter sensing — in one architectural move.

**Re-iterate (Phase 2B):** `+ multi-spindle ring · + hub-clamp reaction collar · + RCC wrist · − ground outriggers · − heavy ballast`

**Optimize (Phase 6):** parallel-stage the spare while lifting `[P20]`; FMEA hardens the lift lock. Python script optimizes spindle count vs. ring mass vs. motor cost via `differential_evolution` on a weighted objective (cycle time × mass × cost).

**Patent (Phase 8):** independent claim on hub-clamp reaction collar as torque reaction mechanism; ASCII figures of ring assembly and hub clamp; 4 dependent claims on spindle count, chuck geometry, RCC compliance, and autonomous control mode.

**Final design — PitCrew-A.** TRIZ citation log: `P2 · P5 · P10 · P13 · P15 · P20 · P22 · P25`

---

## Installation

**One-click:**

1. Download [`autonomous-inventor.skill`](./autonomous-inventor.skill)
2. Open Claude → **Settings → Capabilities → Skills** ([how to install](https://support.claude.com/en/articles/12512180-use-skills-in-claude))
3. Upload the file

**From source:** copy `SKILL.md` into your Claude skill directory.

---

## Usage

Triggers automatically on any request to invent or design equipment:

```
"Invent a device to harvest ripe strawberries autonomously."
"Design equipment to clear snow from residential sidewalks."
"Come up with a machine that sorts recycling at the curb."
"How would you build something to inspect underwater pipelines?"
"I need a contraption that automatically loads pallets onto trucks."
```

Add *"and file a patent"* to any prompt to run Phase 8 after the design converges.

---

## Repository

```
autonomous-inventor/
├── LICENSE
├── README.md
├── SKILL.md                   ← full method + TRIZ appendices (human-readable)
└── autonomous-inventor.skill  ← packaged for one-click install
```

---

## License

MIT — see [LICENSE](./LICENSE).

---

<div align="center">

Built by **Daniel Armani**

*CEO, Texas Blockchain Center · Author, Better Governance (Springer Nature, 2026)*

[linkedin.com/in/dr-armani](https://linkedin.com/in/dr-armani) · [github.com/dr-armani](https://github.com/dr-armani)

</div>
