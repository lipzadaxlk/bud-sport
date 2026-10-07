# Tells catalog: AI defaults by domain

> **Last reviewed: 2026-10-07.** Tells migrate with each model generation; review about every six months.
> **Golden rule:** every item is a *default*, not a crime. If the user asked for it, it stays. If the axis is free, do not spend that freedom on an item from this list, and replace it with a choice **drawn from the subject**, never with another item from this list.

## Design / UI

**First wave (2023-2025)**
- Purple, indigo or blue gradient on white; gradient-filled headline text. (Traceable origin: indigo was the demo color across Tailwind UI.)
- Inter, Roboto, Arial or the system font. Once those are banned: Space Grotesk, Geist.
- Centered hero + pill badge + two CTAs + a "Trusted by" logo row + three feature cards with an icon on top.
- Everything `rounded-2xl` with the same soft shadow; cards nested in cards.
- Decorative glassmorphism or backdrop blur; neon glow on dark; cyan on near-black.
- Emoji used as icons; a large icon above every heading.
- Bento grid of identical cards.
- Fade-and-slide-up on every section; identical hover zoom on every image; bouncy easing.
- The "hero metric" template (big number, small label, supporting stats, gradient accent); decorative sparklines.
- Everything centered; uniform 24-32px spacing; every button styled as primary.
- Filler copy ("Elevate your workflow", "Unlock...") and invented metrics.
- Thick colored border on one side of cards and alerts; modal overuse.

**Second wave (2025-2026)**, what appears once the first wave is banned
- Warm cream background (around #F4F1EA) + high-contrast serif + terracotta accent (around #D97757).
- Near-black with a single acid-green or vermilion accent.
- "Newspaper cosplay": hairlines, zero radius, dense columns.
- Generic SaaS card kit.
- "Template chrome": letter-spaced ALL-CAPS eyebrow above every heading; metadata joined by middle dots (A · B · C); "WORD - fragment" with a dash; #0B0B0B or #111 instead of black; monospace in small labels; "→" at the end of every link and button.
- 01 / 02 / 03 numbering where nothing is sequential.
- One word of the headline set in italics or another color.
- Light or dark theme chosen by product category instead of context of use.

## Writing (English)

**Vocabulary measured above human rates**
delve, tapestry, testament, underscore(s), pivotal, crucial, landscape, intricate, interplay, meticulous, vibrant, enduring, garner, bolster, boasts, showcase/showcasing, foster, highlight(ing), enhance, emphasizing, align with, seamless, robust, leverage, camaraderie, sentence-initial "Additionally".

**Structures**
- Negative parallelism / epanorthosis: "it's not X, it's Y", "not just X but Y", "Not X. Y."
- The rule of three everywhere (three adjectives, three benefits).
- Em dashes where a comma or parentheses would do.
- "serves as / functions as / stands as" instead of "is".
- Inflated significance ("a pivotal moment", "a broader trend", "legacy").
- Vague attribution ("experts say").
- Openers like "In today's fast-paced world"; formula conclusions ("Despite challenges, the future looks bright"); a tidy recap at the end.
- Stacked hedging.
- Bold overuse, Title Case headings, lists with inline bold headers, emoji bullets, tables where prose fits, brochure tone.

**Character names**
Elara Voss, Elena Vasquez, Marcus Chen, Amara Okafor, Aris Thorne, Lena Petrova, "Dr. Sarah Chen", Elias, Mara; lighthouse keepers, clockmakers, librarians.

**Other languages.** Every language has its own list (in Portuguese, for example: "mergulhar em", "tapeçaria", "jornada", "alavancar", "no cenário atual", "vale ressaltar"). Apply the same structures section, and add your language's words here.

## Code and architecture

- Helpers or abstractions for a single use; design for hypothetical requirements; unrequested "flexibility"; extra files.
- Manager / Service / Handler classes for everything; interfaces with a single implementation.
- Blanket try/except; silent fallbacks; redundant validation of internal data (validate at the boundary only).
- Comments narrating the obvious; docstrings added to code that was not changed.
- The most popular library by reflex (unneeded NumPy in up to 48% of cases in one study; Python chosen by default where it does not fit).
- Copy-paste instead of reuse (duplicated blocks grew about 8x in 2024 in one large code analysis).
- Logic that only passes the test, with hard-coded values.
- The same folder tree for every project size (`src/components`, `utils/`, `services/`, `types/`).
- Template READMEs: Features / Installation / Usage / Contributing / License, with emoji.
- "Improvements" outside the requested scope.

## Ideas, products and names

- "Sitcom ideas" (Paul Graham's term): plausible ideas nobody actually wants, such as a social network for pet owners or a marketplace for X.
- "AI for X", "Uber for X", "all-in-one platform", "copilot for...", gamified productivity.
- A digital or app solution by reflex, even for a physical or social problem.
- Name suffixes: -ly, -ify, -io, -ara/-ora, -base, -hub; ".ai" by default.
- Name words: Nexus, Lumina, Aura, Synapse, Nova, Spark, Flow, Pulse, Vertex, Zenith, Echo.
- Taglines built on "Empower / Unlock / Elevate / Transform your...".
- Metaphors: time as a river or a weaver; "journey"; "ecosystem".
