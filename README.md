<div align="center">

# 🔧 Autonomous Inventor

**A Claude skill that invents hardware and automation designs through systematic contradiction resolution — not trial and error.**

[![License: MIT](https://img.shields.io/badge/License-MIT-black.svg)](./LICENSE)
[![Platform: Claude](https://img.shields.io/badge/Platform-Claude-orange.svg)](https://claude.ai)
[![Method: TRIZ](https://img.shields.io/badge/Method-TRIZ-blue.svg)](https://en.wikipedia.org/wiki/TRIZ)
[![Type: Skill](https://img.shields.io/badge/Type-Skill-green.svg)](https://support.claude.com/en/articles/12512148-getting-started-with-skills)

<br>

*Anchor on a bad form. Iterate. Reframe the architecture. Loop until the hard problems are designed out — not patched.*

</div>

---

## Why this exists

Most invention methods are linear: brainstorm → prototype → test → repeat. They add parts, tune parameters, and call it done.

This skill does something different. It **names the contradiction** generating the hardest problems, resolves it architecturally using TRIZ, stress-tests the result, and loops back to reframe again if a structural flaw surfaces. One good reframe eliminates clusters of problems that more iteration never could.

> *Design quality is proportional to how precisely you name the contradiction.*

---

## Method

The skill runs 7 phases across 2 feedback loops:

```
0 Contradictions → 1 Baseline → 2 Iterate → 3 Reframe (TRIZ) → 2B Re-iterate*
                                                  ▲                    │
                                                  │  loop if structural │
                                                  └──── 4 Stress-test ◀┘
                                                              │
                                      5 Specialize → 6 Optimize → 7 Final design
```

> \* Phase 2B runs only when the reframe shifts the whole architecture. The **3↔4 loop** is the engine — expect to traverse it more than once.

<br>

| Phase | Name | What happens |
|-------|------|-------------|
| **0** | Contradiction inventory | Name technical and physical contradictions *before* designing |
| **1** | Baseline | Start from a humanoid anchor — deliberately wrong, forces every part to earn its place |
| **2** | Iterate | ~10 cycles of `− remove · + add · ± adjust`, each annotated with TRIZ principles |
| **3** | Reframe | Resolve the core contradiction architecturally via TRIZ separation strategies |
| **2B** | Re-iterate | 5–10 fresh cycles on the *new* architecture (conditional) |
| **4** | Stress-test | Brutal failure-mode analysis; triggers another reframe if a structural flaw surfaces |
| **5** | Specialize | Define the bounded operating domain; mechanics solves, AI decides |
| **6** | Optimize | Tune within the fixed architecture — FMEA, efficiency, cost, manufacturability |
| **7** | Final design | Name · components · cycle · TRIZ citation log · reframe history · residual limits · niche |

---

## TRIZ integration

The skill embeds the full **TRIZ 40 Inventive Principles** and three supporting appendices:

<details>
<summary><strong>Appendix A — 40 Inventive Principles (quick reference)</strong></summary>
<br>
All 40 principles grouped by cluster (Segmentation & Structure · Dynamics & Adaptability · Geometry & Dimension · Surface & Interface · Physical & Material Effects), each with a one-line core move — designed to be scanned mid-invention.
</details>

<details>
<summary><strong>Appendix B — Separation strategies for physical contradictions</strong></summary>
<br>
When one element must simultaneously be X and not-X, separate the requirements:

- **In space** — X in one zone, not-X in another
- **In time** — X at one moment, not-X at another
- **By condition** — X in one state, not-X in another
- **By system level** — X at the part level, not-X at the system level
</details>

<details>
<summary><strong>Appendix C — Contradiction-to-principle lookup</strong></summary>
<br>
10 common mechanical/automation tensions (strength vs. weight, torque vs. reaction force, autonomy vs. safety, etc.) each mapped to the TRIZ principles most likely to resolve them.
</details>

---

## Core principles

- **Contradictions are the signal.** Where something is hard to design, a contradiction hides. Name it; don't just add parts.
- **The 3↔4 loop is where good designs become great.** One reframe is rarely enough.
- **Mechanics before AI.** Compliance, self-location, and passive alignment beat precision perception.
- **Quantify what matters** — loads, torques, tolerances, masses, cycle time, cost.
- **Honesty over salesmanship.** A design with stated limits beats one that claims everything.

---

## Worked example

**Task:** change a flat tire autonomously.

The skill identified the core contradiction: *high torque needs a heavy reaction base, but a heavy base hurts mobility.* The reframe resolved it by reacting torque **internally** through a multi-spindle nutrunner ring (TRIZ P5, P13) and re-referencing the machine off the **hub** rather than the floor — eliminating jack instability, grounded-torque dependence, and sub-millimeter sensing requirements in one move.

The result — **PitCrew-A** — uses a self-leveling LiftPod that mechanically locks before any work begins, a multi-spindle servo ring that engages all lug nuts simultaneously, and a compliance-first wrist that absorbs misalignment without precise sensing. TRIZ citation log: `P2 · P5 · P10 · P13 · P15 · P20 · P22 · P25`.

---

## Installation

**One-click install:**

1. Download [`autonomous-inventor.skill`](./autonomous-inventor.skill)
2. Open Claude → **Settings → Capabilities → Skills**
3. Upload the `.skill` file

**From source:**

Copy `SKILL.md` into your own Claude skill directory, or zip the folder and upload.

---

## Usage

Once installed, the skill triggers automatically on any request to invent or design equipment — no special syntax required.

```
"Invent a device to harvest ripe strawberries autonomously."
"Design equipment to clear snow from residential sidewalks."
"Come up with a machine that sorts recycling at the curb."
"How would you build something to inspect underwater pipelines?"
```

The skill handles the full method. You guide the domain and constraints.

---

## Repository

```
autonomous-inventor/
├── LICENSE
├── README.md
├── SKILL.md                   ← human-readable, browsable
└── autonomous-inventor.skill  ← one-click install
```

---

## License

MIT — see [LICENSE](./LICENSE).

---

<div align="center">

Built by **Daniel Armani Ph.D.**

*CEO, Texas Blockchain Center LLC*

</div>
