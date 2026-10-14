# Mechanism Generator Community

Mission, timeline, and contribution standards for the [Mechanism Generator](https://github.com/Mechanismo-AI/mechanism-generator) — an open toolkit for mechanism design. New here? Read the timeline and the FAQ below first.

## Mission

Deciding the geometry of a mechanism — the linkage that moves a part through its required positions, in the right order, at the right time — is one of the oldest activities in engineering, and one of the least well served by software. The tools are closed, the methods are tribal, and the results are hard to check.

This project exists to change that:

- A **written, open task specification** — OMTS, the Open Mechanism Task Specification — that states what a mechanism must do, in terms a person can read and a program can check.
- A **search engine** that turns a specification into candidate designs: learned proposals, geometric constructions, and refinement under explicit qualification rules.
- **Verification** of lines of synchronized mechanisms against the declared timing contract, with results a human can inspect.
- **Evidence attached to every claim**: each run records what was asked, what was attempted, and what passed, so results can be checked rather than trusted.

We build for students, small labs, independent designers, and anyone who has ever needed a four-bar linkage and did not have a CAE budget.

The project is a kinematic research alpha. It is not engineering certification, and it will never pretend to be.

## Principles

1. **Fail closed.** If the tool cannot do what a document asks, it says so and stops. Unsupported features are rejected with a clear error, never silently approximated. A wrong answer that looks right is worse than no answer.
2. **Evidence before claims.** Every capability claim ships with its evaluation: the cases, the baseline, the gains and the losses. Evaluation sets are frozen before results are seen. We do not retune on data we promised to hold out, and we do not loosen a gate after looking at the results.
3. **Machines propose, people decide.** The tools produce ranked candidates and proposals. A human reviews them and makes the engineering decision. Nothing is auto-promoted, auto-released, or auto-published.
4. **No hidden data flows.** No telemetry, no automatic uploads. Sharing results is an explicit, consent-gated act with a local review step, and contributor attribution is preserved.
5. **Local-first.** The toolkit runs on an ordinary CPU. Using it requires no account, no cloud service, and no fast GPU.
6. **Reproducible by construction.** Models are hash-pinned, seeds are recorded, and run manifests capture the exact inputs. Two people running the same command should get the same numbers.
7. **Limitations stated plainly.** Documentation says what the tool does not do. Passing a frozen corpus is regression evidence, not proof of generalization; collision, dynamics, and certification are future work, and the docs never imply otherwise.

## How to contribute

- **Use it and tell us what happened.** Write an OMTS document for a mechanism you actually need, run it, and open an issue with the outcome — failures are as valuable as successes, and a well-described failed search is a real contribution.
- **Improve the specification.** OMTS is young. The spec's open questions are genuine questions; well-argued answers and counter-examples from real use carry more weight than completeness.
- **Contribute code.** Pull requests that fix a defect, add a test, or implement a spec'd feature. A failing case that the tests miss is the ideal first PR.
- **Share results.** The engine prepares an offline contribution bundle you review locally and share deliberately. Bundles are pseudonymous by default; identity is never required to contribute results.
- **Write examples and documentation.** An annotated example that teaches one idea well is worth more than a broad tutorial. Plain language beats jargon.

## Review standards

Every pull request is expected to:

- Pass CI as-is; never merge on top of a broken or skipped test.
- Come with a test that fails before the change and passes after, for anything behavioral.
- Keep scope explicit: what the change does, what it deliberately does not do, and what it rejects.
- Back any performance or success-rate claim with the evaluation that produced it, including the baseline and the losses. A PR that claims "better" without numbers will be asked for them.
- Add no telemetry, network calls, or uploads. The offline guarantees are load-bearing.
- Preserve backward compatibility of the OMTS documents and contribution schemas, or version the change explicitly.

## Community norms

- Critique claims, not people. The standard is evidence, not seniority.
- Negative results are welcome. Publishing a well-instrumented failure saves everyone time.
- Keep it plain-spoken. If a sentence needs jargon to survive, rewrite it.
- Everything in the repositories is Apache-2.0. By contributing, you agree your contribution is licensed the same way.

## Timeline

Direction of travel, not a contract. Each entry exists because its evidence shipped with it; the detailed technical history lives in the [changelog](https://github.com/Mechanismo-AI/mechanism-generator/blob/main/CHANGELOG.md).

**Where this came from**

- **August 2026 — the idea.** A private research draft: describe a mechanism task in a written, checkable specification instead of a closed tool's dialog boxes.
- **0.1.0a1 — the foundation.** The draft became the Open Mechanism Task Specification (OMTS): a document format with strict validation. The adapter refuses to guess: unsupported requests are rejected, not silently approximated.
- **0.1.0a2 — the research alpha.** A packaged search engine for planar four-bar linkages, with three Apache-2.0 learned models that propose initial geometry, and a downloader so anyone can run it on an ordinary CPU.
- **0.1.0a3 — honest sharing.** After every run, the engine prepares an offline bundle of results for review. No telemetry, no automatic uploads: sharing is an explicit human decision.
- **0.1.0a4 — orientation.** Tasks can demand not just three positions but three *directed* orientations, each with its own angular tolerance.
- **0.1.0a5 — reproducibility.** Deterministic geometric seeds alongside the learned models, and the whole training history packaged so results can be regenerated rather than trusted.
- **0.1.0a6 — direction.** Explicit input-crank direction controls (positive, negative, either) — a small feature that flushed out a lot of hidden assumptions.
- **0.1.0a7 — the first real brief.** Tolerance-aware initialization and panel screening, validated on a tabletop transfer example that had defeated the previous release. The design met its hard limits with thin margins; the project said so.
- **0.1.0a8 → a10 — geometric search.** Three optional additions that reach for analytic constructions and adaptive sampling when the learned proposals miss, each shipped only after a fresh comparison showed gains with no losses.
- **motion-v0.1.0-dev0 — six-bar, experimentally.** A separately installable experimental package for twelve-pose motion generation with a sixth bar. Marked dev0, kept out of the main engine.
- **October 2026 — OMTS v0.2, synchronization (merged to main, releasing with the next version).** The big one: verifying *lines* of mechanisms that share one shaft. Tasks declare their timing contract — anchoring, ordering and window events, applied master-phase offsets — and the verifier composes the achieved results of independently searched mechanisms into a per-combination verdict. Search tools propose offsets; a human declares them; the build record sits beside the verdict and never gates it.

**Where we are**

A working single-mechanism search engine with published, hash-pinned models; a written task specification with strict validation; a consent-gated offline review flow for sharing results; and, as of October 2026, composed-line verification for synchronized mechanisms. A kinematic research alpha — useful, inspectable, and honest about what it is not: no collision checking, no dynamics, no engineering certification.

**Where we're going**

*Near term*

- Close the remaining OMTS v0.2 open questions: deprecating `phase_relations`, path-fragment event references for collision windows, whether sweep and collision windows enter v0.2, and ordering freedom on fixed-timing tasks.
- A feasibility precheck in line results: report the spread of achieved ordering leads against the required band, so near-miss lines are visible before spending search budget.
- More mechanism families beyond the four-bar. Integration happens only behind frozen evaluations with predeclared gates — no family ships because the prototype looked promising.

*Longer term — exploring*

- Collision-body geometry and sweep/collision windows in the composed-timeline verifier.
- Dwell and handoff events, and ratioed (non-1:1) participation in verified lines.
- Both crank directions verifiable in composed lines.
- A public case-study corpus: shared, consented contribution bundles accumulating into a library of verified line designs that new searches can be measured against.

**Keeping this timeline honest**

This document is editable the same way the code is: propose a change by pull request, and a maintainer reviews it before it merges. Wikipedia-style open editing would work against this project's grain — an unsourced timeline entry is exactly the kind of claim the project refuses to make elsewhere. So the rule is simple: **every timeline claim must cite a public artifact** (a release, a merged pull request, a spec section), and proposals that cannot cite one are not merged. Future items are the exception — they are plans, labeled as plans, and never worded as promises.

## Mechanism and industrial design FAQ

You don't need a mechanical engineering degree to use this project — you need a handful of ideas and the right pictures. These are the ideas, with links to the best explanations we know of. (Suggestions for better ones are welcome; the review bar is the same as the timeline's: it has to actually be good.)

**What is a mechanism?**

The part of a machine that turns one motion into another — gears, links, cams, and ratchets, working together. The most beautiful explanations on the web are Bartosz Ciechanowski's interactive articles: [Gears](https://ciechanow.ski/gears/), which builds gear behavior up from two touching discs, and [Mechanical Watch](https://ciechanow.ski/mechanical-watch/), which assembles an entire watch movement in front of you. Neither assumes any background.

**Why does this project keep saying "four-bar"?**

The four-bar linkage is the simplest useful linkage: four rigid bars, four pivots, one input crank. Almost everything complicated in machine design starts from it, and a point on its middle bar traces a surprisingly rich curve — that's the *coupler curve* the search engine steers through your target positions. Read the [Wikipedia article](https://en.wikipedia.org/wiki/Four-bar_linkage), then watch the animated four-bar models on the same author's [Mekanizmalar YouTube channel](https://www.youtube.com/user/mekanizmalar).

**What is a "master shaft," and why do mechanisms need synchronizing?**

Many machines are really several mechanisms on one input shaft — a feeder, a gate, a press, each timed so the parts meet at the right moment. The timing is set physically by gear trains and crank keyways. This project lets you declare that timing contract in the task document and verifies the composed line against it; Ciechanowski's [Gears](https://ciechanow.ski/gears/) covers exactly the mechanism vocabulary (ratios, torque, tooth shapes) that makes such a contract realizable.

**I'm an industrial designer / maker / artist, not an engineer. Is this for me?**

Yes — browse first, compute later. [507movements.com](https://507movements.com/) animates the 1868 classic *Five Hundred and Seven Mechanical Movements*, and engineer Nguyễn Đức Thang's enormous animated catalog (introduced well in this [Make: article](https://makezine.com/article/workshop/understand-1700-mechanical-linkages-helpful-animations/)) is hypnotic mechanism browsing. When one of those motions is the one your product needs, write an OMTS document for it and let the search engine do the trigonometry.

**I want to learn this properly.**

[MIT's Introduction to Robotics](https://ocw.mit.edu/courses/2-12-introduction-to-robotics-fall-2005/) (free, includes planar and spatial kinematics) is the standard structured route; the University of Illinois' interactive [Four-Bar Linkages reference](https://dynref.engr.illinois.edu/aml.html) goes deeper on exactly the linkage family this project searches, including why some geometries can never complete a revolution.

**Why does this project talk about evidence so much?**

Because mechanism design software has a trust problem. When a tool says "here is your design," you cannot check it without redoing the work — unless the tool ships the work. That's the project's whole stance: verifiable inputs, recorded attempts, honest failure counts. See the principles at the top of this page.

## License

This repository's text is Apache-2.0, matching the [main project](https://github.com/Mechanismo-AI/mechanism-generator). See [LICENSE](LICENSE).