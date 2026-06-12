---
title: "Why out-of-the-box AI agents fall short on a real codebase"
toc: true
tags:
  - tools
  - tutorial
  - vcs
  - ai
  - cursor
  - claude-code
---

Earlier this year I gave a couple of internal talks at Unity about how my team could
actually get value out of AI coding agents, instead of being disappointed after the first
demo. This is the first of three posts I pulled out of those talks. I cut the
Unity-internal parts and kept what applies to anyone working on a real, messy, long-lived
codebase.

This first post has no tools in it. No config files, no screenshots, no clever prompts.
It is just the handful of things you need to understand about how these models work,
because once they click, the rest of the series follows on its own. I also wanted this
written down somewhere I can point my next team at.

## The disappointment is real, and it is not your fault

You install a shiny AI agent, point it at your repository, and ask it to fix a bug or add
a small feature. It answers fast, it sounds confident, and the result is generic at best
and wrong at worst. It does not know your code, it does not know your command-line tools,
and it has never heard of your conventions.

My setting for the whole series is a big C#/.NET codebase: the Unity Version Control
package and the apps around it. The agent knows C# in general just fine. It knows nothing
about *our* C#, our build, or the in-house CLI we use all day. So out of the box it is
basically a clever stranger.

The good news is that all of this is fixable. But to fix it you first have to understand
why it happens.

## A model is a brand-new intern, every single time

The single most useful mental model: a large language model is static and stateless.

Static means it was trained up to some cutoff date and then frozen. It is a binary that
does not change while you use it. Stateless means it remembers nothing between sessions.
Close the chat, open a new one, and yesterday never happened.

Put those together and you get an intern who is sharp, well-read, and showing up for the
very first time on every single task. No memory of your last conversation, no idea what
your team decided last week, no feel for the unwritten rules everybody else absorbed
months ago.

So you have two options. Re-explain everything by hand every time, which gets old fast.
Or write that onboarding down once, in a form the agent can pick up on demand. That second
option is the entire point of posts two and three. Everything I do later is just
onboarding a stranger efficiently.

## Context is a budget, and it gets spent badly

Whatever the agent knows for a given task has to fit in its context window. That window is
large now, but it is still finite, and you are sharing it between the system prompt, your
rules, the files you attached, and the whole back-and-forth of the conversation.

Two things go wrong as that fills up.

The first is compaction. When the window gets close to full, the agent summarises older
parts of the conversation to make room. That summary is lossy. Details you cared about get
blurred or dropped, and the agent starts answering from a fuzzy memory of what you said
rather than what you actually said. If you trigger compaction often, that is usually a
sign you poured in too much irrelevant stuff to begin with.

The second is subtler. Answer quality tends to drop as a conversation gets long, even
before the window is full. People call it context rot. Early instructions get buried,
half-relevant files distract the model, and it slowly drifts.

The practical habits that follow are boring and they work. Stay in the first half of the
window. Attach the minimum the task needs, not the whole folder. And start a fresh session
for each new task instead of carrying one giant chat across your whole day.

## It will be wrong, and it will sound certain

Two more facts to keep in mind, both a little uncomfortable.

These models are nondeterministic. Ask the exact same question twice and you can get two
different answers. That is normal, it is how sampling works, and it means you should not
expect the tool to behave like a function that returns the same thing every time.

They also hallucinate. The model will invent a method that does not exist, cite a file
that was never there, and do it with total confidence. The fix is not to hope for a better
model. The fix is to ground it: point it at real files, and ask it to show you where
something is defined rather than taking its word for it. And then review the output the way
you would review a junior's pull request, because that is exactly what it is.

There is also a small thing worth knowing about "thinking". Most current models can spend
extra reasoning before they answer, and you can ask for more of it on genuinely hard
problems. Just do not assume more thinking is always better. On a simple task it can talk
itself into overcomplicating things.

## You stopped being the typist. You are the tech lead now

This is the shift that ties it all together. The job is no longer typing syntax and
remembering boilerplate. The job is describing what you want, setting the bar for what
"done" means, and reviewing what comes back.

The mistake I see most is treating the agent like an oracle you ask questions. "How should
I do X?" gets you a generic essay. Assign a task instead. Describe the end state, list the
constraints it must respect, point at the relevant code, and say what has to be true when
it finishes (tests pass, this behaviour works, no change to that interface). You are
writing a small spec for a capable junior, not chatting with a search engine.

## The principles the rest of this series leans on

Four ideas carry through everything that follows:

- Customise it or stay generic. An agent with no setup gives you generic help. The whole
  value is in teaching it your project.
- Mind your context. Fresh sessions, minimal attachments, no dumping.
- Share what works. A prompt or workflow that helped you will help your teammate. Write it
  down where the tool and the team can both find it.
- Review everything. The agent is the junior. You are the one accountable for what ships.

## What is next

That is the theory. In [part two](/2026/02/12/teaching-the-agent-your-codebase-rules-skills-commands/)
I get practical: how I actually onboard the agent to a codebase with Rules, Commands, and
above all Skills, including the real set of `SKILL.md` files my team ships. In
[part three](/2026/03/25/ai-agents-mcp-servers-and-everyday-workflows/) I put it to work:
the Plan-then-Auto loop I run every day, connecting the agent to Jira and Confluence over
MCP, and an honest comparison of Cursor and Claude Code.

If you want to go deeper on the fundamentals above, these are the sources I lean on:

- [Building effective agents (Anthropic)][effective-agents]
- [The static, stateless, directional nature of LLMs][static-stateless]
- [How contexts fail, and how to fix them][contexts-fail]
- [Inverse scaling in test-time compute][inverse-scaling] (why thinking longer is not always better)
- [Why LLMs are non-deterministic][nondeterminism]
- [OpenAI's prompt engineering guide][prompt-guide]

[effective-agents]: https://www.anthropic.com/research/building-effective-agents
[static-stateless]: https://medium.com/@daveziegler/large-language-model-concepts-for-curious-users-the-static-stateless-and-directional-nature-of-a0f4d8ec2972
[contexts-fail]: https://www.dbreunig.com/2025/06/22/how-contexts-fail-and-how-to-fix-them.html
[inverse-scaling]: https://arxiv.org/abs/2507.14417
[nondeterminism]: https://www.hopsworks.ai/dictionary/llm-non-determinism
[prompt-guide]: https://platform.openai.com/docs/guides/prompt-engineering
