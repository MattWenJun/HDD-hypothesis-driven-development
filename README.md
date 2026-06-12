# HDD — Hypothesis-Driven Development

**English** | [中文](README.zh.md)

**A skill that stops your AI agent from confidently working on a wrong premise.**

HDD is an Agent Skill: a methodology for diagnosis, debugging, optimization,
selection, and architecture/configuration changes — any task where the result
is uncertain and needs to be *verified* rather than assumed.

Its core discipline is simple but unnatural for both humans and LLMs:

> **A hypothesis, no matter how confident, is just a hypothesis until observed
> evidence confirms it. Reasoning alone is not evidence.**

---

## Why it exists

The most expensive failure mode of a capable agent isn't getting the answer
wrong — it's spinning for a long time on top of a wrong assumption, and only
revealing it after delivery. HDD front-loads the cheap question ("is this premise
actually true?") before the expensive work begins.

It also fixes the most overlooked assumption of all: **the agent assuming its own
capability boundary without checking it.** That's why the flow opens with
*Resource Mapping* — before proposing any technical hypothesis, map what tools,
local knowledge, and external entry points you actually have.

## The flow

```
Step 0  →  HT  →  PT  →  AT Design  →  DEV  →  AT Run  →  E2E
```

- **Step 0 — Resource Mapping** — what resources can solve this? Challenge every
  assumed limitation before assuming you need a workaround.
- **HT — Hypothesis Test** — assign a prior, attack your own ground truth, and
  reach a real evidence level (V1 reproduction / V2 closed evidence chain).
  Pure reasoning is V5 — **zero** evidential weight.
- **PT — Plan Test** — validate the plan with concrete test cases.
- **AT Design** — define "what does done look like" *before* writing code.
- **DEV** — implement against the plan and acceptance tests.
- **AT Run** — execute the acceptance tests.
- **E2E** — end-to-end acceptance by the user.

With explicit back-off paths: a failed plan returns to the plan; a failed plan
caused by a bad hypothesis returns all the way to HT.

## The evidence ladder

| Level | Name | Bayesian weight |
|-------|------|-----------------|
| V1 | Live reproduction | Highest |
| V2 | Closed evidence chain | High |
| V3 | Partial chain | Medium |
| V4 | Analogy | Low |
| V5 | Pure reasoning | **Zero** |

For post-hoc diagnosis, **V2 or V1 is mandatory** before any fix.

## Install

HDD is model- and harness-agnostic. Drop it into wherever your agent loads skills:

```bash
git clone https://github.com/MattWenJun/HDD-hypothesis-driven-development.git
# then place SKILL.md into your agent's skills directory, e.g.
#   ~/.your-agent/skills/hdd/SKILL.md
```

The skill activates on diagnosis / debugging / optimization / selection /
architecture-change tasks, or manually when you say *"use HDD"* / *"verify the
hypothesis first"*. It deliberately does **not** activate for simple, certain
edits (rename a title, add an import).

> Tool names inside `SKILL.md` (read/write files, memory search, web search,
> run commands) are capability descriptions — swap them for whatever your agent
> environment actually provides.

## ⭐ Like it? Star it!

If HDD helps your agent think straight instead of guessing, give it a **star** — it helps others find it too.

## Follow Me

I write about AI, startups, and psychology.

- **WeChat public account:** MindCode
- **X:** [@moneygalaxy](https://x.com/moneygalaxy)
- **Substack:** [mindcodeplus](https://substack.com/@mindcodeplus)

## License

MIT © 2026 MattWenJun
