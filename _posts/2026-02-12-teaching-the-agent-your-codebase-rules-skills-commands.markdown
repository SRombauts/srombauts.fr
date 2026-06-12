---
title: "Teaching the agent your codebase: Rules, Skills and Commands"
toc: true
tags:
  - tools
  - tutorial
  - vcs
  - ai
  - cursor
  - claude-code
---

This is part two of three, adapted from the internal talks I gave at Unity. In
[part one](/2026/01/29/why-out-of-the-box-ai-agents-fall-short/) I argued that an AI agent
shows up like a brand-new intern on every task: sharp, but with no memory of your codebase,
your CLI, or your conventions. This post is about fixing that. It is the practical heart of
the series, and most of it is about one file: `SKILL.md`.

## You cannot retrain the model, so onboard it instead

You are not going to fine-tune a frontier model on your repository, and you should not want
to. What you can do is hand the agent the same documentation a new hire would get, and let
it read the relevant page when it needs it. That is the trick. You do not paste everything
up front. You leave the docs in the repo, written so the agent can find and load the right
one on demand.

Three kinds of docs do most of the work: Rules, Commands, and Skills.

## Rules: the constraints you are tired of repeating

Rules are short, declarative constraints. "Always do this." "Never do that." In Cursor they
live in `.cursor/rules/` and you can scope each one to a set of files with a glob, so a rule
only loads when the agent touches matching code.

A couple of real ones from our codebase: keep lines under a sensible width, and prefer our
own background-work pattern over raw `async`/`await`. Nothing fancy. The value is that the
agent reads them automatically and stops making the same mistake every file.

There is also the cross-tool version: a single `AGENTS.md` (or `CLAUDE.md`) at the repo
root, which is really just a README written for the AI. A root file is simple and every tool
reads it. Glob-scoped rules are more surgical and keep irrelevant guidance out of context.
I use both, and which one fits depends on whether the guidance is project-wide or specific
to one corner of the code.

## Skills: the part that actually changed how I work

A Skill is a how-to guide the agent loads only when it is relevant. Rules say what not to
do. Skills teach a procedure: how to add a localized string, how to review a branch, how to
cut a release. This is where I spend most of my effort, so it gets the most room here.

### What a SKILL.md actually is

A skill is a folder with one required file, `SKILL.md`, plus optional extras. The file
starts with a little YAML header and then the instructions:

```yaml
---
name: plastic-scm-cli-reference
description: >-
  Reference for our source-control CLI (cm): core concepts, object specs,
  and the scriptable commands for branches, diffs, and code review.
  Load when running cm commands or scripting a branch workflow.
---
```

The `description` is the most important line in the whole file. It is what the agent reads
to decide whether to load the skill at all. If the description is vague, the skill never
fires when you need it, no matter how good the body is. So I write it with both halves
spelled out: what the skill does, and when to reach for it.

The other habit that matters is progressive disclosure. Keep `SKILL.md` short and move the
heavy detail into separate files under a `references/` folder that the agent only opens if
it needs them. The skill stays cheap to load, and the depth is there when the task calls for
it. Folder and skill names are kebab-case, usually a verb or a short noun phrase.

### The example that sells the whole idea

My favourite skill to point at is the one wrapping our source-control CLI. Out of the box
the agent is completely fluent in `git` and has never heard of `cm`, the command-line tool
we use all day. Ask it to create a task branch and it will confidently run git commands that
do not apply here.

One skill closes that gap. It lists the concepts, the object specs, and the handful of `cm`
commands that come up in a normal branch-and-review workflow, with the quoting quirks you
hit on PowerShell. After that the agent drives our CLI instead of guessing. If you only ever
write one skill, make it the one for the tool your agent does not know.

### The catalogue my team actually ships

To show this is not a toy, here is the set we keep in the repo, grouped by what they do. I
am naming them, not pasting them, since the contents lean on internal detail.

- Codebase knowledge: `repository-architecture` (a map of where things live),
  `csharp-code-style` (our conventions, including the no-`async`/`await` rule),
  `localization-strings`, and `logging-debugging`.
- The CLI the agent does not know: `plastic-scm-cli-reference`, the example above.
- Workflow: `development-workflow`, `code-review`, `release-notes`, `unity-plugin-release`,
  and `jira-ticket-evaluation`.
- Integrations: `jira-mcp-server` and `confluence-mcp-server`, which I cover in part three.
- Meta: `agent-response-style` (how the agent should talk), `humanizer` (strip the
  AI-writing tells out of any text before it gets posted), and `skill-maintenance` (the
  conventions for editing the skills themselves).

A few are worth showing in a bit more depth. `csharp-code-style` is mostly a list of
concrete dos and don'ts, which is exactly what a code-style skill should be. The CLI
reference is the gap-filler I described above. `release-notes` is a small procedure that
turns a finished task into ship-ready text. None of them is long. They are just the things I
got tired of explaining.

### Skills travel

One nice property: the same `.claude/skills/` folder is read by Cursor too, so a single
library serves more than one agent. There is an emerging open format for these files, which
means the effort is not locked to one vendor. That alone made me comfortable investing in
them.

## Commands: a prompt you stopped retyping

Commands are reusable `/slash` workflows, a saved prompt you and your team can run by name.
A review command, a write-tests command, whatever you keep typing. They are the lightweight
end of the spectrum: less structured than a skill, but versioned and shared instead of
living in someone's head.

## The rule of thumb that decides which is which

People always ask when to use what. The heuristic I settled on:

- If you have typed roughly the same prompt twice, make it a Command.
- If the agent makes the same mistake twice, tighten a Rule (and scope it with a glob).
- If it is a real multi-step procedure, write a Skill.

The meta-point is to codify the things that work and commit them, so the next person, and
the next session, start ahead instead of from scratch.

## A couple of habits that make all of this land

Keep the context clean. A `.cursorignore` file is a `.gitignore` for the agent: keep build
output, logs, and huge generated files out of its view so it spends its attention on code
that matters.

Write tasks like small specs, not chat. Goal, constraints, the files to look at, and what
must be true at the end. And here is the part that surprised people: if you find yourself
crafting elaborate prompts to coax a good answer, that is usually a sign of missing context,
not a sign you need a cleverer prompt. The fix is a Rule or a Skill, not more incantation.

Finally, check that your work actually landed. You can ask the agent, without letting it
read anything new, how it would do some task and which rule or skill that comes from. If the
answer is sharp, your skill is discoverable. If it is vague, your description needs work. I
tune more descriptions this way than I would like to admit.

## What is next

That covers teaching the agent. In
[part three](/2026/03/25/ai-agents-mcp-servers-and-everyday-workflows/) I put it to work:
the Plan-then-Auto loop I run every day, wiring the agent up to Jira and Confluence over
MCP, and where Cursor and Claude Code each earn their place.

References I keep going back to for writing skills:

- [Skill authoring best practices (Anthropic)][skill-best-practices]
- [anthropics/skills on GitHub][anthropics-skills] (real examples and a skill creator)
- [The agentskills.io spec][skill-spec]
- ["Don't build agents, build skills instead"][skills-talk] (Anthropic)
- [Cursor's docs on Rules][cursor-rules] and [Skills][cursor-skills]

[skill-best-practices]: https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices
[anthropics-skills]: https://github.com/anthropics/skills
[skill-spec]: https://agentskills.io/
[skills-talk]: https://youtu.be/CEvIs9y1uog
[cursor-rules]: https://cursor.com/docs/context/rules
[cursor-skills]: https://cursor.com/docs/context/skills
