# council-skill

Before you commit to a hard-to-reverse decision, get five independent takes on it — then one clear call.

The council dispatches five subagents in parallel, each with a **cold brief and no visibility into the others**. That isolation is the whole point: they can't converge on each other's framing, so you get genuine disagreement instead of five paraphrases of your own prompt. A chairman pass then weighs the conflict and names one next step.

No dependencies. No API keys. Works in any repo.

## Credit

This is a port of [Andrej Karpathy's LLM Council](https://github.com/karpathy/llm-council) idea — put a question to multiple models, let them answer independently, then have a chairman synthesize.

**The difference:** Karpathy's version gets independence from *different models* (GPT, Gemini, Claude, Grok answering the same question). This one uses **only Claude**, and gets independence from *different roles* instead — five personas with sharply opposed mandates, each in its own isolated subagent context.

Trade-off, stated plainly: you lose true cross-model diversity, and you keep whatever blind spots Claude has. You gain something that runs inside Claude Code with no multi-provider setup, no keys, no cost per extra model — and personas tuned for engineering and business decisions rather than open Q&A.

## The five perspectives

| Persona | Mandate |
|---|---|
| **Contrarian** | Assume this goes wrong. What breaks, what's the failure mode, what cost is underweighted? |
| **First-principles** | List the assumptions. Which are load-bearing facts, which are unexamined habit? |
| **Expansionist** | What upside is being left on the table? What's the bolder version? |
| **Outsider** | Knows nothing about the domain. Asks the naive question an expert filters out. |
| **Executor** | Skip the analysis. One sentence: what's the next concrete action? |

Then the **chairman** compares them — agreement, conflict, which risk is most severe, which upside is most credible — and gives one recommendation, naming the trade-off it accepts.

## Install

In Claude Code:

```
/plugin marketplace add petegannaban21/council-skill
/plugin install council@council-skill
```

Manual (no marketplace):

```
cp -r skills/council ~/.claude/skills/council
```

## Use

Ask for it explicitly:

```
council this: should we move the API off Laravel onto Go?
run the council on dropping the IP allowlist
/council
```

Or let it fire on its own — the skill description tells Claude to invoke it unprompted for decisions that are hard to reverse, spend real money or time, change a convention going forward, or touch production state.

## Output

Two things, every run:

1. **In chat** — a tight decision memo: one line per persona, plus the chairman's verdict. Not the raw transcripts.
2. **On disk** — the full writeup (all five perspectives in full + synthesis) at `docs/council/[Decision Title]-council.md` in the current repo. The chat is the summary; the file is the record.

## When not to run it

Routine edits. Anything already fully specified. Easily-reversible changes. Work that's merely large but not actually risky.

This is a deliberation tool, not a formality. Run it on everything and it becomes latency you learn to ignore.

## License

MIT
