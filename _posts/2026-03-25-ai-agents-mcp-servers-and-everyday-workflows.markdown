---
title: "Putting the agent to work: Plan mode, Auto mode and MCP"
toc: true
tags:
  - tools
  - tutorial
  - vcs
  - ai
  - cursor
  - claude-code
---

This is the last of three posts in the series. It goes out alongside my second team talk,
*Working with Cursor: AI in Unity* (25 March 2026), which is where I show this part in
action. In
[part one](/2026/01/26/why-out-of-the-box-ai-agents-fall-short/) I covered the
fundamentals, and in
[part two](/2026/02/12/teaching-the-agent-your-codebase-rules-skills-commands/) I onboarded
the agent with Rules, Skills, and Commands. Now the fun part: actually using it on real
tasks, day in and day out.

## What I showed the wider Unity engineering teams

The first session was for my own team. This one was open to engineers across Unity, and it
was almost all live work on our codebase rather than slides. I gave a quick tour of the
Cursor UI and the tips that save the most time, set up the Jira and Confluence MCP servers
and queried them live, then ran a real bug fix from a Jira ticket through branch,
implementation, code review, and a generated CHANGELOG. I finished by planning a larger
change in Plan mode and walking through how I actually choose between Cursor and Claude
Code. This post keeps the parts of that demo that apply anywhere: the plan-then-auto loop,
MCP, and picking the right tool for the task.

## The one loop I run for almost everything: Plan, then Auto

If you take a single habit from this whole series, take this one. Before letting the agent
change any code, I run it in Plan mode.

In Plan mode the agent reads around, gathers context, and writes out how it intends to solve
the task, without touching a single file. It is a way to pump the brakes on an eager agent.
I get to see its plan while changing it is still free. Most of the time the plan is roughly
right and I nudge one or two things. Sometimes it has completely misunderstood the task, and
catching that on a page of text beats catching it after it has rewritten fifteen files.

Then I switch to Auto, or Agent, mode and let it implement the plan I just approved. Because
it is working from a plan I already read, the output lands much closer to what I wanted. And
it takes checkpoints as it goes, so if it does start drifting I can roll back to the last
good state instead of untangling a mess by hand.

That is the rhythm: plan, read the plan, approve, let it run, review. There is also a
read-only Ask mode for when I just want to explore the code without any risk of changes, but
the plan-then-auto loop is the workhorse.

## MCP: letting the agent reach beyond the repo

A model on its own is a text generator. What turns it into something useful is the ability
to act: read files, run commands, and call out to other systems. MCP, the Model Context
Protocol, is the standard way to plug those external systems in.

The two I rely on connect the agent to our issue tracker and our wiki. Once the Jira MCP
server is set up, I can hand the agent a ticket key and it pulls the summary, description,
and comments straight from Jira, no copy-pasting a web page into the chat. The Confluence
one does the same for documentation pages. Setup is a one-time thing per machine: an API
token of your own and a bit of configuration. I am keeping the specifics out of here since
they are tied to our internal instances, but the shape is the same for any tracker or wiki
with an MCP server.

The payoff is that the agent stops being an island. It can start a task from the actual
ticket, not from my paraphrase of it.

## A normal task, start to finish

Here is what a small bug fix or minor feature looks like once all of the above is in place.

It starts from a Jira ticket. I give the agent the key, and thanks to the MCP server it
reads the ticket itself. It creates the task branch using the CLI skill from part two, the
one that taught it our `cm` commands. Without that skill this step alone would fall apart,
which is a nice reminder that the workflow rests on the onboarding.

Then the plan-then-auto loop. The agent proposes how it will implement the change, I review
and tweak the plan, and it makes the edits across the files involved, following the code
style and patterns it learned from the Rules and Skills.

When the code is in place I run a review. There is a code-review skill that gives it a
checklist and a structure, so the feedback is consistent instead of "looks good to me". For
a finished task I also have it draft user-facing release notes with the release-notes skill,
which turns the work into ship-ready text. For a bigger feature I lean harder on Plan mode up
front, and on checkpoints throughout, but it is the same loop scaled up.

None of these steps is magic. Each one works because the agent was taught the relevant
procedure once and can now repeat it.

## Say no to slop

The agent automates the typing. It does not automate the judgement, and it never takes the
blame. So I review everything it produces with the same bar I would hold a colleague to.

In practice that means watching the diff while it works and stopping it the moment it heads
the wrong way, running a self-critique pass over the changes, and keeping a human
accountable for anything that gets merged. Functionally-correct but unmaintainable code is
still a problem, maybe a worse one, because it slips through looking finished. The quality
bar does not move just because a machine wrote the first draft.

## Cursor or Claude Code? I use both

I get asked to pick one. I do not, and I think reaching for the right one per task is the
better answer. Here is my honest read after living in both.

Cursor is a full IDE with the agent built in. The things it does well are the things you
feel constantly: Tab completion, inline edits, a clean visual diff, and fast search over a
codebase it has indexed. When I am exploring interactively or want to see changes laid out
visually, Cursor is where I am.

Claude Code runs in the terminal. That sounds like a limitation and is actually its
strength. It drops into any editor, so I can keep Rider open for its debugger and C#
refactoring and run the agent right there in the integrated terminal. It scripts well, fits
into CI, and does not ask me to switch editors to get the agent.

The cost models differ too. Cursor bills around a monthly request budget, where one request
can carry a lot. Claude Code is closer to pay-for-what-you-use on tokens, so cost tracks the
length of your sessions. On Windows I have found the terminal experience matters: native
PowerShell behaviour is not always identical across tools, and it is worth checking how each
one handles your shell.

The most underrated move is running the same task in both and comparing. Two independent
attempts catch mistakes and bias that one would sail past. They are not really competitors
in my workflow. They are a cross-check.

## Wrapping up the series

Three posts, one argument. A fresh agent is a capable stranger
([part one](/2026/01/26/why-out-of-the-box-ai-agents-fall-short/)). You onboard it with
Rules, Skills, and Commands
([part two](/2026/02/12/teaching-the-agent-your-codebase-rules-skills-commands/)). Then you
drive it with a tight plan-then-auto loop, MCP connections, and your own review on top of
everything. Do that and the disappointment from the first demo turns into a genuinely useful
teammate. Skip it and you are back to a clever stranger guessing at your codebase.

References for this part:

- [Model Context Protocol][mcp]
- [Cursor's docs on agent modes][cursor-modes] and [MCP][cursor-mcp]
- [Claude Code docs][claude-code-docs]
- [How Anthropic teams use Claude Code][anthropic-teams]

[mcp]: https://modelcontextprotocol.io/
[cursor-modes]: https://cursor.com/docs/agent/modes
[cursor-mcp]: https://cursor.com/docs/context/mcp
[claude-code-docs]: https://docs.anthropic.com/en/docs/claude-code
[anthropic-teams]: https://www.anthropic.com/news/how-anthropic-teams-use-claude-code
