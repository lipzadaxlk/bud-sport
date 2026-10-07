# Evidence: why outputs converge and what helps

> Research compiled 2026-10-07. All arXiv IDs below were checked against the arXiv API. **[preprint]** = not peer reviewed at the time of writing. **[unverified]** = not confirmed in a primary source.

## Mechanisms

| Finding | Number | Source |
|---|---|---|
| Preference annotators reward familiar text (typicality bias in the data itself) | α ≈ 0.57-0.65, p < 10⁻¹⁴ on HelpSteer | Zhang et al. 2025, *Verbalized Sampling* |
| RLHF reduces output diversity compared to SFT (a generalization vs. diversity trade-off) | significant across several metrics | Kirk et al., ICLR 2024 |
| Aligned models do worse than base models at randomness and creativity; better benchmark scores track with worse creativity | - | West & Potts 2025 |
| Distinct answers in 10 tries | Claude 3.5 Sonnet 1.76; Llama 3.2-1B 6.74; within a family, larger was often less diverse | NoveltyBench 2025 |
| Repetition inside one model (pairwise similarity > 0.8 over 50 samples) | 79% of open-ended prompts, even at T = 1.0 | *Artificial Hivemind*, NeurIPS 2025 |
| Similarity across different models | 71-82%; 25 models x 50 metaphors for "time" formed 2 clusters | same |
| Automatic judges lose calibration where human preferences diverge | - | same |
| LLM research ideas judged more novel than experts', yet only about 5% unique | ~200 unique out of 4,000 | Si, Yang & Hashimoto 2024 |
| Writers using an aligned model produce less diverse content as a group | - | Padmakumar & He, ICLR 2024 |
| People using ChatGPT produce less distinct ideas as a group | - | Anderson et al. 2024 |
| Temperature: weak link to novelty, moderate link to incoherence | - | Peeperkorn et al., ICCC 2024 |
| Min-p's diversity gains do not hold once hyperparameters are controlled | - | Schaeffer et al. 2025 (critique of Nguyen et al.) |
| Anthropic's own prompting guide notes the model converges on "on distribution" output, and that banning Inter leads to other common picks | - | Anthropic prompting best practices |

**Takeaway:** diversity has to come from the **process and the prompt**, not from the temperature knob (which an agent often cannot touch) and not from "thinking longer".

## Techniques ranked by evidence

| Tier | Technique | Measured effect |
|---|---|---|
| A | **Verbalized sampling**: ask for N responses with probabilities, pick from the tail | 1.6-2.1x diversity in creative writing; +25.7% in human-rated diversity; recovers 66.8% of the base model's diversity (direct prompting: 23.8%); quality and safety preserved; more capable models gain more. A list without probabilities is weaker. |
| A | **Generate many, force divergence, then elaborate** (Meincke, Mollick & Terwiesch) | cosine similarity 0.255 vs 0.243 for human groups and 0.377 for the base prompt. The model skipped the divergence step in ~15% of runs, so make it verifiable. |
| A | **In-context regeneration**: show previous answers and require something different | the only strategy close to human diversity in NoveltyBench |
| A | **Direct divergence instruction** ("leave the conventional categories") | beat SCAMPER, TRIZ, C-K and Design Thinking (IDEAFix 2026 [preprint]) |
| B | Ban list **plus a positive choice from the subject** | a one-line instruction cut "it's not X, it's Y" by 48-72% (Boggia 2026 [preprint]); a ban alone shifts to the next default |
| B | Counterfactual genericness test | cheap, works in any domain (from Anthropic's frontend-design skill) |
| B | Best-of-n with a tell detector, then a rewrite pass | cuts about two thirds of a tell; a full rewrite overcorrects below the human rate, so calibrate |
| B | Mutate an existing artifact / conceptual blending | more diversity than generating from scratch; **longer reasoning did not increase diversity** (Lluminate) |
| B | Distant-domain analogy | no significant average effect for LLMs, but the effect grows with semantic distance (2026 [preprint]) |
| C | Persona ("think like...") | 0.377 → 0.368: almost nothing |
| C | Random word prefix | modest gain that saturates |
| C | SCAMPER / TRIZ / Oblique Strategies as a recipe | do not beat a simple instruction; fine as mutation operators |
| C | LLM as originality judge | 50-53% accuracy vs 56% agreement between humans |

## Sources

**Mechanisms**
- Verbalized Sampling: https://arxiv.org/abs/2510.01171 · code: https://github.com/CHATS-lab/verbalized-sampling
- Artificial Hivemind: https://arxiv.org/abs/2510.22954
- Understanding the Effects of RLHF on LLM Generalisation and Diversity: https://arxiv.org/abs/2310.06452
- Base Models Beat Aligned Models at Randomness and Creativity: https://arxiv.org/abs/2505.00047
- NoveltyBench: https://arxiv.org/abs/2504.05228
- Is Temperature the Creativity Parameter of LLMs?: https://arxiv.org/abs/2405.00492
- Min-p sampling: https://arxiv.org/abs/2407.01082 · critique: https://arxiv.org/abs/2506.13681

**Homogenization in people**
- Doshi & Hauser, *Science Advances* 2024: https://pmc.ncbi.nlm.nih.gov/articles/PMC11244532
- Does Writing with Language Models Reduce Content Diversity?: https://arxiv.org/abs/2309.05196
- Homogenization Effects of LLMs on Human Creative Ideation: https://arxiv.org/abs/2402.01536
- Can LLMs Generate Novel Research Ideas?: https://arxiv.org/abs/2409.04109

**Techniques**
- Meincke, Mollick & Terwiesch, prompting diverse ideas: https://papers.ssrn.com/abstract=4708466
- IDEAFix: https://arxiv.org/abs/2606.00875
- Lluminate: https://www.joelsimon.net/lluminate
- Addressing LLM Diversity by Infusing Random Concepts: https://arxiv.org/abs/2601.18053
- Cross-Domain Mapping and Creativity: https://arxiv.org/abs/2603.19087

**Writing**
- Delving into LLM-assisted writing in biomedical publications: https://arxiv.org/abs/2406.07016
- Why Does ChatGPT "Delve" So Much?: https://arxiv.org/abs/2412.11385
- Artificial Epanorthosis: https://arxiv.org/abs/2607.21498
- The Ghost Couple (LLM name priors): https://arxiv.org/abs/2606.02184
- Wikipedia, Signs of AI writing: https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing

**Design**
- Anthropic, prompting best practices: https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-4-best-practices
- Anthropic, improving frontend design through skills: https://www.claude.com/blog/improving-frontend-design-through-skills
- Anthropic skills repository: https://github.com/anthropics/skills
- On the purple-gradient origin [unverified]: https://prg.sh/ramblings/Why-Your-AI-Keeps-Building-the-Same-Purple-Gradient-Website

**Code**
- A Study of LLMs' Preferences for Libraries and Programming Languages: https://arxiv.org/abs/2503.17181
- Investigating the Smells of LLM Generated Code: https://arxiv.org/abs/2510.03029
- GitClear 2025 code quality report (coverage): https://devclass.com/2025/02/20/ai-is-eroding-code-quality-states-new-in-depth-report/

**Ideas and guardrails**
- Paul Graham, How to Get Startup Ideas: https://paulgraham.com/startupideas.html
- Jakob's law: https://lawsofux.com/jakobs-law/
- Choose Boring Technology: https://mcfunley.com/choose-boring-technology
