# bud-sport

A *bud sport* is a branch that grows different from the rest of its tree while staying a healthy part of the same plant. Growers spot it, keep it, and graft it into new varieties. Several well-known apple cultivars started that way.

This repository is an agent skill that does the same for AI output. Language models drift to the most typical answer they can produce: the purple gradient landing page, the "it's not X, it's Y" sentence, the startup named Something-ify. `bud-sport` gives the agent a short, evidence-based process to step off that default without giving up quality, and a memory so it does not repeat itself across projects.

It works for design, copy, naming, product ideas, plans and code.

## Why the default happens

Aligned models collapse toward the mode of their output distribution, and they do it together. In *Artificial Hivemind* (NeurIPS 2025), 79% of open-ended prompts produced near-identical answers inside one model, and different models were 71-82% similar to each other. Human preference data rewards what feels familiar, and preference tuning sharpens it. Raising the temperature mostly adds incoherence, not novelty.

What does move the needle is changing the process: sampling a distribution of options with probabilities and choosing from the tail, forcing a divergence step, and checking whether an idea would fit any neighboring brief just as well. The full numbers and 30+ sources are in [`evidence.md`](skills/bud-sport/evidence.md).

## Install

**Claude Code (plugin marketplace)**

```
/plugin marketplace add lipzadaxlk/bud-sport
/plugin install bud-sport@bud-sport
```

**Any agent that supports the Agent Skills format** (Cursor, Codex, Gemini CLI and others) via the skills CLI:

```
npx skills add https://github.com/lipzadaxlk/bud-sport
```

**Manual:** copy `skills/bud-sport/` into your agent's skills folder (for Claude Code: `~/.claude/skills/bud-sport/`).

The skill triggers on its own when the agent is about to create something with room for choice. You can also call it by name.

## The eight steps

1. **Anchor in the subject.** Who it is for, the job to be done, and the domain's own vocabulary, materials and craft.
2. **Generate a distribution.** 5-10 directions, each with an estimated probability that a typical model would produce it.
3. **Drop the likely ones.** The first idea is the median idea. Pick from the tail by fit, not by strangeness.
4. **Counterfactual test.** Would this fit a neighboring brief just as well? Then it is a default in disguise.
5. **One bold move.** Push the chosen direction further on a single axis, and write down what changed.
6. **Keep the floor.** Accessibility, usability, security and repo conventions are never the creative axis.
7. **Sweep the tells catalog.** Replace each hit with a choice drawn from the subject, never with the next default.
8. **Remember.** Read and update `~/.bud-sport/REPERTOIRE.md` so the next project does not reuse this one's palette, typefaces or naming style.

Small tasks (a name, a headline) run steps 1, 2, 3 and 7 in a few lines. Large ones run all eight.

## What it looks like

Prompt: *"Suggest a name for a recipe app for college students with no time."*

| Direction | Typical-model probability | |
|---|---|---|
| Food + speed (QuickRecipes, FastFood) | 0.15 | dropped |
| Food + student (StudentBites, UniMeals) | 0.12 | dropped |
| The shared student flat as a place (Dorm Kitchen) | 0.05 | kept |
| Improvising with what's in the fridge | 0.04 | kept |
| The audience's own slang for being in a rush | 0.03 | **chosen** |

The pick came from how students actually talk about cooking in a hurry, which is something no neighboring brief could reuse.

## What it will not do

- Override you. If you ask for a conventional or "banned" look, you get it.
- Trade accessibility, standard interaction patterns or security for novelty.
- Make code clever. In code, the anti-default move is to **remove** reflexes: needless abstraction, blanket try/except, the most popular library by habit, comments that narrate the obvious.

## Files

| File | What it holds |
|---|---|
| [`SKILL.md`](skills/bud-sport/SKILL.md) | The process, per-domain rules and guardrails |
| [`tells.md`](skills/bud-sport/tells.md) | Catalog of AI defaults in design, writing, code and naming, with a review date |
| [`evidence.md`](skills/bud-sport/evidence.md) | Mechanisms, techniques ranked by evidence, and sources |
| [`repertoire-template.md`](skills/bud-sport/repertoire-template.md) | Starting point for the cross-project memory file |

## Keeping the catalog fresh

Tells move with every model generation: "delve" dropped sharply in 2025, and the purple gradient gave way to cream and terracotta. If you spot a new one, open a pull request against `tells.md` with an example and, if you have one, a source. Lists for languages other than English are welcome.

## License

[MIT](LICENSE)
