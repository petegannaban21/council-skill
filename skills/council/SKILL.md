---
name: council
description: Use before a consequential, risky, or hard-to-reverse decision — five independent perspectives (contrarian, first-principles, expansionist, outsider, executor) generated via parallel isolated subagents, then synthesized by a chairman into one recommended next step. Also invoke on explicit request ("council this", "run the council", "/council"). Skip for routine or easily-reversible work — this is a deliberation tool, not a formality to run on everything.
---

# Council

Five independent takes on a decision, then one clear call. The point is genuine independence — each persona reasons from a cold brief with no visibility into the others — followed by a synthesis that actually weighs the disagreement instead of averaging it away.

## When to run it

Run unprompted for decisions that are genuinely consequential: hard to reverse, spend real money or time, change an architecture/convention going forward, or touch shared/production state. Also run whenever explicitly asked ("council this", "run the council", "/council"), even for smaller things.

Don't run it for: routine edits, anything already fully specified by the user, easily-reversible changes, or work that's simply large but not actually risky. If unsure whether something qualifies, that uncertainty itself is usually reason enough to run it — but don't let this become a ritual applied to everything, that defeats the purpose and just adds latency.

## Steps

1. **Write the brief.** One neutral paragraph stating the decision or action under consideration, plus the relevant constraints (budget, timeline, prior commitments, what's already been ruled out). Neutral phrasing matters — don't lead toward the answer you expect or want.

2. **Dispatch five agents in parallel** as the **"decision-council"** team, all in a single message so they run concurrently (`run_in_background: false` on each, per persona prompt below). Each agent gets *only* the brief plus its own persona instructions — no mention that four other perspectives exist, no shared context between them. That isolation is what makes them independent instead of performative. Cap each response to roughly 100–150 words: a verdict plus the top reasons, not an essay.

   - **Contrarian** — "Find everything that could fail. Assume this goes wrong: what breaks, what's the failure mode, what hidden cost or risk is being underweighted? Be specific, not generically cautious."
   - **First-principles thinker** — "List the assumptions this decision rests on and challenge each one. Which are load-bearing facts, and which are unexamined habit or precedent? Would reasoning from scratch reach the same conclusion?"
   - **Expansionist** — "Find the upside being left on the table. What bigger opportunity, second-order benefit, or bolder version of this is available that a safe/default choice is missing?"
   - **Outsider** — "You know nothing about this industry or codebase. Read the brief cold and ask the naive questions an expert would filter out. What jargon might be hiding a bad assumption? What would a newcomer find strange here?"
   - **Executor** — "Skip the analysis. Given the brief, what is the single next concrete action to take, right now? One sentence, one action."

3. **Synthesize as chairman.** Once all five return, compare them: where they agree, where they conflict, which risk is most likely or severe, which upside is most credible. Don't just average the opinions — weigh them against what you actually know about the situation and give one clear recommended next step, naming the trade-off it accepts.

4. **Report compactly.** One line per persona (their core point, attributed by role) plus the chairman's verdict. Not the full agent transcripts — this should read as a tight decision memo, not a wall of text.

5. **File the full memo.** Write the complete writeup — all five perspectives in full plus the chairman's synthesis and recommended next step — to `docs/council/[Decision Title]-council.md` in the current project repo (create `docs/council/` if it doesn't exist). The chat reply stays compact per step 4; the file is the durable record.
