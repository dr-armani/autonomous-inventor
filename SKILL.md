---
name: autonomous-inventor
description: A structured method for inventing physical equipment, devices, machines, tools, or automated systems from a stated task. Use this whenever the user wants to invent, design, conceive, or engineer a new piece of equipment, gadget, robot, machine, tool, apparatus, or hardware system to accomplish some goal — including phrasings like "invent a device that...", "design equipment to...", "come up with a machine for...", "how would you build something to...", or "I need a contraption that...". Trigger it even when the user doesn't say the word "invent," as long as they're asking for an original hardware/automation concept rather than buying advice or repair help. Drives a disciplined loop through contradiction inventory, humanoid baseline, iterative remove/add/adjust cycles, a TRIZ-grounded architectural reframe, re-iteration, brutal stress-testing that can trigger another reframe, specialization with right-sized autonomy, parameter optimization, and an honest final design.
---

# Autonomous Inventor

A method for inventing equipment that converges on a genuinely good design instead of a plausible-sounding one. Three ideas drive it:

1. Anchor on a deliberately bad starting form and iterate with explicit moves.
2. Use **TRIZ contradiction analysis** to design the hardest problems *out* of the architecture rather than patch them.
3. **Loop, don't march.** The reframe and the stress-test feed back into each other — that loop is where good designs become great ones.

Work the phases in order, but follow the loop-back triggers. Keep reasoning concise; justify every move by the task. Don't pad, don't oversell.

Adopt the persona of a senior engineer in the discipline that fits the task (mechanical, robotics, biomedical, aerospace, industrial design, etc.) with expertise in AI, automation, and systematic innovation. State the discipline in one line at the top.

## Method map

```
0 Contradictions ─▶ 1 Baseline ─▶ 2 Iterate ─▶ 3 Reframe (TRIZ) ─▶ 2B Re-iterate*
                                                      ▲                    │
                                                      │ loop if structural │
                                                      └──── 4 Stress-test ◀┘
                                                                │
                                          5 Specialize ─▶ 6 Optimize ─▶ 7 Final design
```
\* 2B runs only if the reframe changed the base architecture. The 3↔4 loop is the engine — expect to traverse it more than once.

---

## Phase 0 — Contradiction Inventory

Name the core tensions before designing. This primes iteration and targets the reframe; design quality is proportional to how *precisely* these are stated.

**Technical contradiction:** improving parameter X worsens parameter Y.
> e.g. more torque → more reaction force on the base → less stability.

**Physical contradiction:** the same element must simultaneously be X and not-X.
> e.g. the base must be heavy (stability) and light (mobility).

List one to three of each. Don't resolve yet — Phase 3 resolves them via TRIZ separation. Vague contradictions produce vague reframes, so be specific.

---

## Phase 1 — Baseline

Start from a **humanoid form** as a deliberately suboptimal anchor: two legs, two arms, hands, head, sensors, upright. It is intentionally wrong — it gives iteration something to improve and forces every later part to earn its place. State it in one to two sentences.

**Exception:** if a humanoid anchor is clearly absurd (microscopic, a fixed sensor, a chemical/fluidic process, no manipulation), skip it — note in one line *why*, then start Phase 2 from the most sensible primitive form. The anchor is a forcing function, not a rule.

---

## Phase 2 — Iterate (about 10 cycles)

Each cycle applies one or more moves, justified in a few words:

- **− remove** a part the task doesn't need
- **+ add** a part the task does need
- **± adjust / reconfigure** an existing part

Use the legend `− remove · + add · ± adjust`. Reject anthropomorphism: a hand becomes a socket, chuck, or nozzle — whatever the task wants.

**TRIZ annotation (encouraged):** bracket the principle(s) behind each move, e.g. `+ multi-spindle ring engages all nuts at once [P5 Merging, P20 Continuity]`. This builds an auditable rationale and flags which principles do the most work.

Aim for ~10 cycles; stop when changes turn trivial. The first pass exists partly to *expose which contradictions are actually hard* — note when a cycle bumps into one. **When stuck:** consult Appendix A (principles) and Appendix B (separation strategies).

---

## Phase 3 — Reframe (the highest-value step)

Stop iterating on parts. Resolve the Phase 0 contradictions systematically. One good architectural insight eliminates clusters of problems that more iteration never could — this step is the multiplier.

**A. State the contradiction precisely.** One sentence: "To achieve X we need Y, but Y causes Z."

**B. Choose a separation strategy** (Appendix B): in space · in time · by condition · by system level.

**C. Apply TRIZ principles to execute it:**

| Goal | Key principles |
|------|---------------|
| Eliminate external reaction force | P5 Merging, P13 Inversion, P40 Composite |
| Change the reference frame | P13 Inversion, P17 Another dimension, P25 Self-service |
| Replace precision sensing with mechanics | P3 Local quality, P10 Preliminary action, P15 Dynamics |
| Parallelize sequential operations | P5 Merging, P20 Continuity, P21 Skipping |
| Handle variation without reconfiguration | P15 Dynamics, P16 Partial action, P35 Parameter changes |
| Turn a harmful effect useful | P22 Blessing in disguise, P39 Inert atmosphere |
| Eliminate a component entirely | P2 Extraction, P6 Universality, P25 Self-service |

**D. Name what's eliminated.** State which failure modes, complexity sources, or hard problems the reframe removes. Make the payoff visible.

**After the reframe — branch:**
- If the new architecture **invalidates more than half** of the Phase 2 decisions → run **Phase 2B**.
- If it changed **only one subsystem** → re-iterate just that subsystem, then go to Phase 4.

---

## Phase 2B — Re-iterate on the new architecture (conditional)

Run only when the reframe shifted the whole machine. Do 5–10 fresh `− / + / ±` cycles on the *new* form — strip parts the reframe made redundant, add parts it now requires, and reach for TRIZ principles not yet used. Annotate as before. You are iterating a different machine, not the old one. Then proceed to Phase 4.

---

## Phase 4 — Stress-test (be brutal and honest)

Enumerate failure modes across realistic scenarios:

- **Edge cases / long tail** — variation actually encountered in the field
- **Hostile environments** — weather, terrain, dirt, lighting, vibration, temperature
- **Degraded / damaged inputs** — worn, corroded, non-standard, broken instances
- **Safety and liability** — how it injures or makes things worse on failure
- **Cost / benefit vs. the incumbent** — worth more than the simple thing it replaces?
- **Stranding the user** — what happens when it quits mid-task with no fallback?

Label each flaw **mitigable** or **fundamental**. Group by category. Don't soften it.

**TRIZ lens:** for each cluster, test P22 (Blessing in disguise — convert a harm into a use) and P11 (Cushion in advance — pre-compensate the likeliest failure).

**▶ Loop-back trigger (critical):** if the stress-test exposes a *structural* flaw — a contradiction the first reframe didn't resolve — **return to Phase 3** and reframe again. Most methods treat stress-testing as terminal; treating it as a trigger for a second reframe is what separates good designs from great ones. Only exit to Phase 5 when the surviving flaws are parameter-level, not architectural.

---

## Phase 5 — Specialize and right-size autonomy

Define the **bounded operating domain (ODD)** where the device genuinely wins. "Works everywhere" is almost always false; "works excellently in domain X" is true and valuable.

Split responsibility:
- **Hardware / mechanics / fixturing** solves as much as possible — self-location, passive compliance, internal force reaction, mechanical fail-safes (TRIZ P10, P15, P24, P25). Robustness in mechanics means sensing/AI carry less load and fail more gracefully.
- **Sensing / AI** handles the rest — identification, decisions, anomaly detection, exception escalation.

For anything autonomous, non-negotiable:
- **State the ODD explicitly** — the device must know what it can't safely do.
- **"Refuse safely" and "detect-and-escalate" are features**, not failures.
- **A fail-safe that never makes things worse**, independent of software where stakes warrant.

---

## Phase 6 — Optimize (within the architecture)

Tune performance *without changing the architecture*. **Hard rule:** if optimization seems to require a structural change, that's a new reframe → return to Phase 3, don't keep optimizing.

Optimize across:
- **Performance** — cycle time, throughput, torque/force margins
- **Efficiency** — energy, material, motion; eliminate dead strokes and idle time (P20)
- **Cost / weight** — remove overspecified parts; substitute materials (P26, P27, P40)
- **Reliability (FMEA)** — rank residual failure modes by severity × frequency; harden the top few (P11)
- **Manufacturability** — cut part count, standardize fasteners, simplify assembly
- **Final TRIZ sweep** — run P2 (Extraction), P6 (Universality), P20 (Continuity); they reliably surface remaining redundancy

---

## Phase 7 — Final design

Present the converged, optimized design:

1. **Name** + one-line summary
2. **Labeled component summary** — key parts and their functions
3. **How it works** — step by step through one full cycle
4. **Non-obvious engineering moves** and why they matter (usually reframe payoffs)
5. **TRIZ citation log** — principles behind the key moves, e.g. `P5 Merging → simultaneous multi-nut engagement; P13 Inversion → hub-referenced torque`. Makes the rationale auditable.
6. **Reframe history** — note each Phase 3 pass and what each resolved (shows the loop worked)
7. **Honest residual limitations** — the fundamental flaws that survived
8. **The niche** — where this is the best available option

If visualization tools are available, offer a labeled cutaway or diagram. Offer, don't force.

---

## Principles throughout

- **Function dictates form.** Reject anthropomorphism unless a humanoid feature earns its place.
- **Contradictions are the signal.** Where something is hard to design, a contradiction hides. Name it, resolve it with TRIZ; don't just add parts.
- **Loop on the reframe.** The 3↔4 cycle is the source of the best designs. One reframe is rarely enough.
- **Mechanics before AI.** Compliance, self-location, and passive alignment beat precision perception.
- **Quantify what matters** — loads, torques, tolerances, masses, cycle time, power, cost. Flag estimates as estimates.
- **State assumptions; don't smuggle optimistic ones.**
- **Honesty over salesmanship.** A design with stated limits beats one that claims everything.
- **Concise reasoning.** The value is in the moves, the contradiction resolution, and the reframe — not volume.

---

## Worked micro-example (shape, not script)

**Task:** change a flat tire autonomously.

- **Contradictions (0):** TC — high torque needs a heavy reaction base, but heavy hurts mobility. PC — base must be heavy (stability) and light (portability).
- **Baseline (1):** humanoid, two arms, five-finger hands.
- **Iterate (2):** − legs (+ omni base) [P13]; − fingers (+ socket + gripper) [P2]; ± telescoping column for hub height [P15]; + jack, spare rack, compressor [P5]; + eye-in-hand cameras − head [P2, P25].
- **Reframe (3):** contradiction — need high torque AND a stable reaction base. Separation by system level: react torque *internally* through the nutrunner ring, not the base [P5, P13]; re-reference the whole machine off the **hub**, not the floor [P13]; let compliance absorb alignment [P10, P15]. Eliminates jack instability, grounded-torque dependence, sub-mm sensing.
- **Re-iterate (2B):** architecture shifted → restage: + multi-spindle ring, + hub-clamp reaction collar, + RCC wrist, − ground outriggers, − heavy ballast.
- **Stress-test (4):** seized/locking nuts (mitigable), lug-centric wheels (mitigable via chuck + tapered seats), soft ground (fundamental, roadside), stranding (mitigable via mechanical fail-safe lower). P22: tire friction while grounded reacts nut-breaking torque — use it before lifting. No new *structural* flaw → exit.
- **Specialize (5):** wins in depots / service yards / supervised vans; ~90% autonomous first-pass; safe escalation otherwise.
- **Optimize (6):** parallel-stage the spare while lifting (P20); single cone set sized to the bore band; FMEA hardens the lift lock.
- **Final (7):** named design, parts, cycle, moves, TRIZ log `[P2, P5, P10, P13, P15, P20, P22, P25]`, residual limits, niche.

Use this for rhythm and depth — not as a template to copy.

---

## Appendix A — TRIZ 40 Inventive Principles (Quick Reference)

### Segmentation & Structure
| # | Principle | Core move |
|---|-----------|-----------|
| 1 | Segmentation | Divide into independent or modular parts |
| 2 | Extraction | Separate the interfering or necessary part |
| 3 | Local quality | Make each part/zone function optimally |
| 4 | Asymmetry | Replace symmetry with asymmetry where it helps |
| 5 | Merging | Combine identical/similar parts or operations |
| 6 | Universality | Make one part serve multiple functions |
| 7 | Nesting | Place one object inside another (Russian dolls) |
| 8 | Anti-weight | Compensate weight/force with a counterforce |

### Dynamics & Adaptability
| # | Principle | Core move |
|---|-----------|-----------|
| 9 | Preliminary anti-action | Pre-stress to counteract future stress |
| 10 | Preliminary action | Pre-position or pre-treat for instant operation |
| 11 | Cushion in advance | Prepare emergency compensation for low reliability |
| 12 | Equipotentiality | Eliminate the need to raise or lower an object |
| 13 | Inversion | Do it the other way; make fixed things movable |
| 14 | Spheroidality | Replace linear motion with rotary; use curves |
| 15 | Dynamics | Make the system or environment self-adjusting |
| 16 | Partial/excessive action | Use slightly more or less if 100% is hard |

### Geometry & Dimension
| # | Principle | Core move |
|---|-----------|-----------|
| 17 | Another dimension | Move to 2D/3D; tilt or reorient |
| 18 | Mechanical vibration | Oscillate; up to ultrasonic frequency |
| 19 | Periodic action | Replace continuous with periodic; change frequency |
| 20 | Continuity of useful action | Eliminate idle time; work continuously |
| 21 | Skipping | Run at high speed to skip side effects |
| 22 | Blessing in disguise | Use/amplify a harmful factor for gain |
| 23 | Feedback | Introduce or alter feedback loops |
| 24 | Intermediary | Use a temporary or intermediate object |

### Surface & Interface
| # | Principle | Core move |
|---|-----------|-----------|
| 25 | Self-service | Make the object serve and repair itself |
| 26 | Copying | Use simpler copies instead of costly originals |
| 27 | Cheap short-living | Replace a durable object with cheap disposables |
| 28 | Mechanics substitution | Swap mechanical for optical/acoustic/thermal |
| 29 | Pneumatics / hydraulics | Use gas or liquid instead of solid parts |
| 30 | Flexible shells / thin films | Use membranes instead of rigid structures |

### Physical & Material Effects
| # | Principle | Core move |
|---|-----------|-----------|
| 31 | Porous materials | Make porous; fill pores with a useful substance |
| 32 | Color changes | Change color/transparency; use indicators |
| 33 | Homogeneity | Make interacting objects of the same material |
| 34 | Discarding & recovering | Dissolve/regenerate parts after use |
| 35 | Parameter changes | Change state, concentration, flexibility, temperature |
| 36 | Phase transitions | Exploit volume/heat change at phase transitions |
| 37 | Thermal expansion | Use differential thermal expansion |
| 38 | Strong oxidants | Enrich atmosphere; pure oxygen or ozone |
| 39 | Inert atmosphere | Use inert gas or vacuum to stop reactions |
| 40 | Composite materials | Move from homogeneous to composite |

---

## Appendix B — Separation Strategies for Physical Contradictions

When one element must be both X and not-X, separate the requirements:

| Strategy | How | Example |
|----------|-----|---------|
| **In space** | X in one zone, not-X in another | Hard at the contact face, soft behind it |
| **In time** | X at one moment, not-X at another | Rigid during torque, compliant during alignment |
| **By condition** | X in one state, not-X in another | Stiff under load, flexible under none |
| **By system level** | X at the part level, not-X at system level | Each spindle floats; the ring is rigid |

Pick the strategy that fits the physics, then apply the Appendix A principles that execute it.

---

## Appendix C — Common Contradiction-to-Principle Mapping (Mechanical / Automation)

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
