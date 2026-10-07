---
name: bud-sport
description: Use whenever you create something with room for choice - UI and web design, landing pages, copy and microcopy, product or project names, slogans, feature ideas, plans, new architecture, stories, characters, palettes. Breaks the "median output" that aligned language models produce by reflex (purple gradient + Inter + three cards, "it's not X, it's Y", names ending in -ify, needless abstraction) with an evidence-based process - verbalized sampling, forced divergence, a counterfactual genericness test, a tells catalog and memory across projects. Skip it for bug fixes, mechanical refactors, or when the user explicitly asked for something conventional.
---

# bud-sport

A *bud sport* is a branch that grows different from the rest of its tree while staying a healthy part of the same plant. Growers notice it, keep it, and propagate it. That is the job of this skill: step away from the model's default, keep the quality, and remember what worked.

## Why this exists

Aligned models collapse toward the **mode** of their output distribution.

- In *Artificial Hivemind* (NeurIPS 2025, 70+ models), 79% of open-ended prompts produced near-identical answers inside one model, and different models were 71-82% similar to each other. Asked for a metaphor for "time", 25 models x 50 samples landed on two ideas.
- Human preference data rewards what feels familiar (typicality bias), and preference tuning sharpens it.
- Within a model family, the larger model is often the *less* diverse one.

Numbers and sources: [evidence.md](evidence.md).

## What does not work

- **Banning the default on its own.** The model moves to the next default (ban Inter, get Space Grotesk; ban purple, get cream and terracotta). Every ban needs a **positive choice drawn from the subject**.
- **"Be creative", personas ("think like Steve Jobs"), temperature, longer reasoning.** Small or no measurable effect.
- **SCAMPER, TRIZ or Design Thinking as a recipe.** They do not beat a direct instruction to diverge. Use them only as mutation operators.
- **Asking yourself "is this original?".** Model judges drift toward the mode too. Use self-review only for objective checks (does it contain tell X? does it break accessibility?).

## The process

Scale it to the task. Small (a name, a headline): steps 1, 2, 3 and 7 in a few lines. Large (a site, a product, an architecture): all eight.

1. **Anchor in the subject.** In 2-4 lines: what it is, who it is for, the main job the person needs done, and the domain's own vocabulary, materials, era or craft. Distinctiveness comes from here, not from a trending style.
2. **Generate a distribution, not an answer** (verbalized sampling). List **5-10 clearly different directions**, each with an **estimated probability** that a typical model would produce it. The probabilities matter: a plain list stays collapsed.
3. **Drop the high-probability ones** (around 0.10 and above). The first idea is the median idea. From the tail, pick the one that **best serves the goal**, not the strangest.
4. **Counterfactual test.** Would this direction fit a neighboring brief (another product, another audience) just as well? If yes, it is a default in disguise. Go back to step 3 and say what changed and why.
5. **Forced, verifiable divergence.** Make the chosen direction more specific and bolder on **one axis only** (one memorable move, everything else disciplined). Write down what became bolder. Models skip this step about 15% of the time; do not skip it.
6. **Build with the quality floor intact.** Accessibility, usability, security and the repository's conventions are not creative axes (see Guardrails).
7. **Sweep against the tells catalog** ([tells.md](tells.md), the section for the domain). For each hit, replace it with a positive choice from step 1, never with another catalog item. Calibrate, do not zero out: an em dash or a list of three is sometimes the right call.
8. **Memory across projects.** Before step 2, read the repertoire of past choices. After delivering, append what this one used (typefaces, palette, layout structure, concept, names). Default file: `~/.bud-sport/REPERTOIRE.md`; create it from [repertoire-template.md](repertoire-template.md) if it does not exist. Do not reuse another project's combination without a reason that comes from the subject.

Show the user only the summary: the directions considered (one line each, with probability), the one chosen, and why. Do not dump the whole process.

## By domain

**Design and UI.** Concept or metaphor **before** typeface and color; every choice should be defensible in one sentence *for this brief*. Before writing code, fix: a palette of 4-6 named hex colors, type roles (one or two families), an ASCII layout, and the one bold move. Pick light or dark from the **context of use** (who, where, under what light), not from the product category. Motion: one orchestrated moment, animating only `transform` and `opacity`, not a fade on every section. Keep marketing surfaces (strong art direction) apart from product surfaces (sober, proven components).

**Copy.** Use the product's and the audience's own words and concrete verbs. A button says exactly what happens ("Save changes", never "Submit"). An error message states the problem and the fix, without apologizing. Cut the vocabulary and structures listed in the writing section of the catalog.

**Names.** Build the distribution from the domain's vocabulary (craft, material, the audience's slang, place, history), not from suffixes. Check the names section of the catalog. Search whether the name is already taken before presenting it as final.

**Ideas and products.** Start from an **observed problem**, not from "generate ideas". Distrust every idea that turns into "an app / platform / AI for X": models drift to digital solutions even when the problem is physical or social. Use analogies only from **distant** domains; the effect grows with semantic distance.

**Code and architecture.** Here originality means **fit**, not novelty. The anti-default move is to **remove** reflexes: no abstraction for a single use, no design for hypothetical requirements, no blanket try/except, no comments narrating the obvious, no most-popular library by reflex (choose by fit), no copy-paste where reuse belongs. Follow the repository's conventions. Boring technology is a virtue.

## Guardrails: when not to be original

- **The user's explicit request always wins**, including a "banned" look or a deliberately conventional result.
- **Accessibility is the floor**: contrast 4.5:1 for body text and 3:1 for large text and UI shapes, visible focus, `prefers-reduced-motion`, adequate touch targets, semantic HTML.
- **Interaction mechanics stay conventional** (Jakob's law): navigation, forms, checkout, links, scrolling, universal icons. Spend originality on identity, not on mechanics.
- **Security and standards**: never invent cryptography, authentication, sanitization or parsers for standard formats.
- **Regulated or high-trust contexts** (health, finance, government, technical documentation): clarity and predictability beat surprise.
- **Novelty costs feasibility**: every tail idea passes a "does it work and serve the goal?" filter before it is delivered.

## Pairs well with

Optional, none required: Anthropic's `frontend-design` skill, the official GSAP skills (`greensock/gsap-skills`), shadcn's skill and MCP for product UI, and any single style preset. Do not stack several style presets at once.

## Maintenance

Tells shift with each model generation ("delve" dropped sharply in 2025; purple gave way to terracotta). [tells.md](tells.md) carries a review date. Revisit it about every six months.
