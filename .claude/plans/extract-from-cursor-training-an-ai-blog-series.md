# Blog series plan: Customizing AI coding agents for a real codebase

## Context

This series is extracted from **two internal Unity training documents** in
`C:\UnitySrc\codice\.claude\training\`:

1. `cursor_training_slides.md` — This was my internal talk to convince the team
   to share skills on our repository. It's a deep "Coding at the Speed of Thought" slide
   deck: LLM concepts, the Rules/Skills/Commands onboarding stack, a full power-user
   feature catalogue, team heuristics, skill-authoring best practices, autonomous
   loops (Ralph Wiggum), and a large bibliography of mostly public references.
2. `cursor_demo_session.md` — This was a shorter extract toward all Unity Engineering!
   a live demo-session outline ("How We Use Cursor on Our
   Codebase") with a Cursor-promotional framing ("fight back Claude Code dominance"),
   attendee logistics, a calendar invite, and live-demo choreography.

The goal is to **extract a public blog series** from both files for `srombauts.eu`
(the personal Jekyll blog in `C:\UnitySrc\srombauts.fr`). The slides supply most of the
conceptual depth and the "why"; the demo session gives the narrative spine and the
concrete demos.

Per the author's decisions:
- It's absolutely fine, and even mandatory to frame those as being extracted from
my internal talks. I want to use that as a portfolio of my influence in my team and at Unity.
- **Angle:** *Customization how-to* — a practical guide on making AI coding agents
  genuinely useful on a real codebase (Rules / Skills / Commands / MCP), not a tool war.
- **Scope:** Mention **Unity Version Control** explicitly as the concrete setting, but
  **remove all internal-only material** — VPN requirements, internal Jira/Confluence
  instances/URLs, the "fight Claude Code dominance" framing, attendee logistics,
  calendar invite, Zoom/Google-Doc/Confluence links, Slack channels, `@unity3d.com`
  accounts, and anything Unity-confidential.
- **Format:** A **series of 3 linked posts**.

This aligns with the author's stated current focus on the About page: *"exploring how
repository instructions, Claude Code skills, and coding agents can be used effectively
on my codebases."*

This is a content task. The deliverable of the *implementation* phase is three new
Markdown posts in `_posts/`. This plan defines their structure; the actual prose is
written during implementation.

---

## VITAL: use the `humanizer` skill for all prose

**Every blog post, portfolio page, or About-page edit MUST be run through the
`humanizer` skill (`.claude/skills/humanizer/`) before it is considered done.** This is
non-negotiable for this repo: the site is a public, AI-expertise-forward portfolio, so
visibly AI-generated prose would undercut its whole point. The skill strips AI tells
(em/en dashes, rule-of-three, inflated significance, promotional language, `-ing`
padding, copula avoidance, signposting, generic upbeat conclusions, etc.) and matches
the author's first-person casual voice.

Apply it as the final pass on each of the three posts during implementation:
- Feed the draft to the humanizer along with a **voice sample** (an existing post such
  as `_posts/2022-02-22-I-joined-unity.markdown`, or the longer
  `_posts/2012-04-12-why-i-switched-from-mercurial-to-git.markdown`) so the rewrite
  matches the author's cadence, not a generic "natural" voice.
- Honor its hard constraint: the final text contains **no em dashes (—) or en dashes
  (–)**. Scan for them before saving.
- Keep the technical content intact; humanize the prose, do not gut the substance.
- The author's genuine voice does include the occasional `;)` / `:)` smiley and short
  retrospective `*edit YYYY-MM-DD: ...*` notes. Those are author voice, not AI emoji
  decoration, and may be kept sparingly.

This applies to the posts themselves, not to this plan file.

---

## House rules to follow (from `AGENTS.md`)

- Posts live in `C:\UnitySrc\srombauts.fr\_posts\` named `YYYY-MM-DD-kebab-slug.markdown`.
- Jekyll + minimal-mistakes theme. Permalinks are `/YYYY/MM/DD/slug/` (used for
  cross-links between the posts).
- Frontmatter: usually just `title` + `tags` (other fields inherited from `_config.yml`
  defaults). Add `toc: true` for long posts to get a sidebar table of contents — all
  three posts in this series are long enough to warrant it.
- Voice: **first person, casual, English**. Use `##`/`###` headings (sentence case),
  reference-style links at the bottom, optional `*edit YYYY-MM-DD: ...*` notes.
- 2-space indent, LF, UTF-8, final newline (`.editorconfig`).
- **Do not commit or push** without explicit request — a push to `master` triggers a
  live deploy.

---

## Resolved choices (confirmed by the author)

- **Tags:** use existing `tools`, `tutorial`, `vcs` **plus three new tags** `ai`,
  `cursor`, `claude-code`. (The author opted into the new tags despite the house-rule
  lean toward existing-only, because the series is explicitly about AI agents and these
  improve discoverability.) All three posts share the same six tags.
- **Dates / cadence:** the work actually happened over late January to March 2026, so
  the posts are dated to match that real timeline, staggered:
  - Post 1 → `2026-01-29`
  - Post 2 → `2026-02-12`
  - Post 3 → `2026-03-25`
- **Screenshots:** default to **text-only for the first draft** (still an open nicety,
  see below). Diagrams/screenshots can be added later under `assets/images/`.

---

## The series

A 3-part series. Each post ends with a "next up" link to the following one; posts 2 and
3 back-link to post 1 (and post 3 also links back to post 2). All three use
`toc: true`.

Each post may open with a short line noting it is adapted from internal talks I gave to
my team and to Unity engineering. This is deliberate: it doubles as a portfolio of the
influence I had on adopting these practices, so the framing is welcome rather than
something to hide.

Structure at a glance:
- **Post 1 is pure theory and fundamentals** — the problem and the mental models, with a
  reference list to point back to. No tooling mechanics.
- **Posts 2 and 3 are the practical half** — the actual customization and the demo
  workflows, drawn from the skill set I have actually shipped.
- **Depth ceiling:** nothing goes deeper than the talks covered. No codebase internals,
  no advanced workflows I did not demo. The autonomous-loop ("Ralph") material is dropped
  entirely because I never used it.

### Post 1 — *Why out-of-the-box AI agents fall short on a real codebase*
Date `2026-01-29`. **Pure theory and fundamentals.** This is the conceptual post: the
problem it identifies and the mental models that explain it, with a reference list to
point back to from the later posts (and to reuse when onboarding a future team). It
deliberately stops before any tooling mechanics; Rules/Skills/Commands/MCP are named
only as the answer the next posts will build. Drawn mostly from
`cursor_training_slides.md` section 2 (LLM concepts) and section 6 (the mindset
takeaways), with the problem framing from `cursor_demo_session.md`.

- **The problem:** a fresh AI agent doesn't know your codebase, your CLI, or your
  conventions. The result is generic help and confident wrong answers. The setting I
  keep returning to is a large C#/.NET codebase, the **Unity Version Control** package
  for the Unity Editor.
- **Static and stateless:** an LLM is effectively frozen at a training cutoff and keeps
  no memory between sessions. Every task is a brand-new intern showing up with zero
  onboarding and no recollection of yesterday. So you either re-feed context every time,
  or you automate that onboarding. That is the whole argument for the rest of the series.
- **Context is finite, and quality rots:** the context window has a budget; "compacting"
  (auto-summarizing the history when it fills) is lossy and a signal you fed too much;
  and answer quality degrades as a conversation grows ("context rot"). Practical
  fundamentals: stay in the first half of the window, be surgical about what you attach,
  start a fresh session per task.
- **Nondeterminism and hallucination:** the same prompt can give different output, and
  models produce plausible-but-wrong code. So grounding (point at real files, ask "show
  me where this is defined") and reviewing everything are not optional extras, they are
  part of the basic model of how the tool behaves.
- **A little on "thinking":** models can spend extra reasoning before answering, and you
  can ask for more of it on hard problems, but more thinking is not always better on
  simple ones. Keep this short; it is a fundamental worth naming, not a deep dive.
- **The mindset shift:** from "writing code" (typing syntax) to architecting, reviewing,
  and curating it. You act like a tech lead delegating to a junior: give a spec, set
  acceptance criteria, review the output. Assign tasks, don't treat the agent as an
  oracle you ask questions.
- **The guiding principles** that the practical posts will keep coming back to: customize
  or stay generic; context hygiene; share what works; review everything, because the
  agent is a junior dev and you are the tech lead accountable for what ships.
- **Tools and roadmap (brief):** I use both **Cursor** and **Claude Code**, and the key
  point is that the techniques port across both (and across agents generally). One or two
  sentences, then a roadmap link to posts 2 and 3.
- **References:** this is the post that carries the bibliography. Link the public sources
  for each fundamental (static/stateless, context rot, nondeterminism, thinking budgets,
  building effective agents) so the later posts can stay practical and just point back
  here.

Tags: `tools`, `tutorial`, `vcs`, `ai`, `cursor`, `claude-code`.

### Post 2 — *Teaching the agent your codebase: Rules, Skills & Commands*
Date `2026-02-12`. The customization deep-dive — the heart of the how-to. Maps to
`cursor_demo_session.md` section 3 + the Annex skill list, and to
`cursor_training_slides.md` section 3 (the onboarding stack), the team heuristics, the
prompt/task-framing takeaways (section 6), and the skill-authoring annex (Annex B).

- **The onboarding analogy:** you can't change the model's training, but you can hand it
  the docs a new hire would get. Rules, Commands, and Skills are that onboarding stack,
  and the agent **discovers** what it needs on demand instead of you pasting everything.
- **Rules** — declarative constraints scoped by file globs (`.cursor/rules/`), read
  automatically when the agent touches matching files. Concrete, non-confidential
  examples: a line-length cap; "prefer our async pattern over raw `async/await`". The
  cross-tool equivalent is `AGENTS.md` / `CLAUDE.md` repo instructions ("a README for
  the AI"). Note the trade-off the deck calls out: a single root `AGENTS.md` is simple;
  modular glob-scoped rules keep irrelevant guidance out of context. Mention project vs
  user (global) vs team rules.
- **Skills (the centerpiece of this post)** — procedural how-to guides the agent loads on
  demand. This is where the post spends most of its words.
  - **SKILL.md anatomy:** the folder-per-skill layout, the YAML frontmatter (`name` and
    especially `description`, which is what makes the skill discoverable), the body, and
    optional `references/` files and `scripts/`. Stress **progressive disclosure**: keep
    `SKILL.md` short and push detail into linked reference files the agent only loads when
    it needs them. Naming: kebab-case, gerund or noun-phrase.
  - **The hero example:** a **CLI reference skill** (`plastic-scm-cli-reference`) so the
    agent can actually drive the source-control CLI it has never seen. This is the
    cleanest illustration of why skills exist: the agent is fluent in `git` and clueless
    about `cm`, and a skill closes that gap.
  - **The real catalogue (portfolio of influence):** show that this is not a toy by
    walking the set I actually shipped, grouped, at a high level. Codebase knowledge
    (`repository-architecture`, `csharp-code-style` with its concrete "no `async/await`,
    use `ThreadWaiter`" rule, `localization-strings`, `logging-debugging`); the CLI
    reference skill above; workflow (`development-workflow`, `code-review`,
    `release-notes`, `unity-plugin-release`, `jira-ticket-evaluation`); integrations
    (`jira-mcp-server`, `confluence-mcp-server`); and meta skills about how the agent
    behaves and how skills are maintained (`agent-response-style`, `humanizer`,
    `skill-maintenance`). Name them and say what each is for in a line; do **not**
    reproduce their confidential bodies (`cm` internals, code-review REST flows,
    localization keys stay out). Pick two or three safe ones (`csharp-code-style`,
    `plastic-scm-cli-reference`, `release-notes`) to show in a little more depth.
  - **Portability:** the same `.claude/skills/` set is read by Cursor too, so one library
    serves multiple agents. Mention skill.md as an emerging open standard lightly, no
    internal links.
- **Commands** — reusable `/slash` workflows shared with the team (e.g. a review command,
  a write-tests command).
- **The heuristic that ties it together:** if you repeat a prompt twice, make it a
  **Command**; if the agent repeats a mistake twice, tighten a **Rule** (scoped by
  globs); if it's a multi-step procedure, write a **Skill**. Codify successful prompts
  and commit them so the whole team benefits.
- **Context hygiene** — `.cursorignore` (a `.gitignore` for the LLM: skip logs, build
  output, generated files), fresh sessions, surgical context (attach the minimum, point
  at exact files/snippets), and avoiding compaction.
- **Prompting like a spec, not a chat:** a short prompt-shape checklist — goal,
  constraints, context, acceptance criteria. Assign tasks, don't ask an oracle. And the
  slightly counterintuitive takeaway: if you find yourself doing elaborate "prompt
  engineering", that's usually a sign of missing context (a Rule or Skill), not a sign
  you need a cleverer prompt.
- **Checking your work landed:** you can probe what the agent has loaded ("without
  reading any more files, tell me how you'd do X and which rule/skill that comes from")
  to confirm a new skill or rule is actually discoverable.

Tags: `tools`, `tutorial`, `vcs`, `ai`, `cursor`, `claude-code`.

### Post 3 — *Putting it to work: MCP servers and everyday workflows*
Date `2026-03-25`. The agent in action + an honest tool comparison. Maps to Demos B–F
and section 4 of `cursor_demo_session.md`, plus the workflow takeaways from
`cursor_training_slides.md` (sections 4–6). The backbone is the **Plan mode → Auto mode**
loop. Stays at the depth the demos covered; no advanced modes or workflows I didn't show.

- **MCP servers** — what they are (a standard way to let the agent call external tools
  and data: ticket trackers, wikis, databases, local services). Generic Jira &
  Confluence MCP setup at a conceptual level only — **no internal URLs, tokens, or VPN
  details**. The point to make: this is how the agent stops being a text generator and
  starts being able to *act*.
- **The core loop: Plan mode → Auto mode (the spine of the post).** First run the agent
  in **Plan mode**: it gathers context and proposes a plan before touching code, which is
  how you "pump the brakes" on an eager agent and catch a wrong approach while it is still
  cheap to change. You review and refine the plan, then switch to **Auto/Agent mode** to
  implement it, with checkpoints so you can roll back if it drifts. Mention Ask mode
  (read-only exploration) in passing. Keep it to this loop; deeper modes (Debug,
  subagents, worktrees) are out of scope since the demos didn't cover them.
- **Real workflows** end-to-end, narrated on the Unity Version Control package:
  - small bug fix / minor feature starting from a ticket (agent creates a branch via the
    CLI skill, edits across files — and the honest note that it only works *because* of
    the CLI skill from post 2),
  - code review of the change (a review skill/command; comparing a quick in-IDE review
    to a structured `/code-review`),
  - generating a CHANGELOG for a package release (the release-notes skill),
  - planning a larger feature with Plan mode + checkpoints/rollback.
- **Reviewing AI-generated code (say no to slop):** watch the diff and interrupt when it
  drifts, run a self-critique/"find issues" pass, let an automated PR-review bot catch
  the rest, and keep a human accountable for anything merged. Same quality bar as
  human-written code; the agent automates the typing, not the judgment.
- **Cursor vs Claude Code — when to use each** (kept balanced, not promotional): visual
  diffs / Tab / Inline Edit / indexed codebase search vs terminal-first / scriptable /
  works inside Rider or VS / CI-friendly; request-based vs token-based cost; codebase
  indexation (RAG) vs `grep`/`rg`; Windows/PowerShell experience; and using both as a
  cross-check (same task, two tools, compare). Mention the "agent in any IDE" angle: a
  CLI agent in Rider's terminal keeps Rider's debugger and refactoring while adding the
  agent's reasoning.
- Closing recap + back-link to posts 1 and 2.

Tags: `tools`, `tutorial`, `vcs`, `ai`, `cursor`, `claude-code`.

> Note on length: post 2 carries the most weight (SKILL.md plus the catalogue). If it
> runs too long during drafting, the natural relief valve is to move the per-skill
> catalogue tour into its own short follow-up rather than padding or cramming. Default is
> to keep it at three.

---

## Files to create (implementation phase)

Three new files in `C:\UnitySrc\srombauts.fr\_posts\`:

- `2026-01-29-why-out-of-the-box-ai-agents-fall-short.markdown`
- `2026-02-12-teaching-the-agent-your-codebase-rules-skills-commands.markdown`
- `2026-03-25-ai-agents-mcp-servers-and-everyday-workflows.markdown`

Each begins with frontmatter following the existing convention:

```yaml
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
```

Cross-links between posts use the pretty permalink form:
- Post 1: `/2026/01/29/why-out-of-the-box-ai-agents-fall-short/`
- Post 2: `/2026/02/12/teaching-the-agent-your-codebase-rules-skills-commands/`
- Post 3: `/2026/03/25/ai-agents-mcp-servers-and-everyday-workflows/`

---

## Public references we can cite

The slide deck cites many **public** sources that fit the author's reference-style-links
habit and would strengthen the posts. Pick a tasteful handful per post (the author
typically uses a few, not a wall of links). Safe, public candidates:

- **Anthropic:** Building Effective Agents; Equipping agents with Agent Skills; "Don't
  Build Agents, Build Skills Instead" (Zhang & Murag talk); `anthropics/skills` on
  GitHub; How Anthropic teams use Claude Code; Claude Code docs; skill-authoring best
  practices.
- **OpenAI:** Prompt Engineering guide; Greg Brockman's note on agentic software
  development (the AGENTS.md / "codify skills" / human-accountability advice).
- **Cursor docs/blog:** Rules, Commands, Agent Skills, MCP, Modes, Agent Best Practices;
  Composer model post; dynamic context discovery; secure codebase indexing.
- **LLM fundamentals (mostly for post 1):** the "static, stateless, directional"
  explainer; "How Contexts Fail" (context rot/poisoning); "Inverse Scaling in Test-Time
  Compute" (overthinking); an LLM non-determinism explainer.
- **Skills ecosystem:** the skill.md open-standard write-up; `skills.sh`.

Do **not** cite: the internal Confluence pages, Zoom recording links, internal Google
Docs, the Unity Helpdesk, or anything behind `unity3d.com` / `codice@cloud`.

---

## Explicitly omit (internal-only / confidential)

- VPN requirement and any internal Jira/Confluence instance URLs or token-generation
  steps.
- The "fight back Claude Code dominance at Unity" framing and the goals / calendar-invite
  / pre-session / attendee-logistics sections.
- Internal links and identifiers from the slide deck: `confluence.unity3d.com` pages,
  `unity3d.zoom.us` recordings, internal Google Docs, the Unity Helpdesk catalog,
  `@unity3d.com` Google-account login, `codice@cloud`, the `#cursor` Slack channel, and
  internal action items ("Agents Captain", PR process for `.cursor/`, etc.).
- Plastic SCM internal command specifics beyond what is needed to make a generic point
  (keep "a source-control CLI the agent doesn't know"; name Unity Version Control as the
  product, not internal mechanics).
- Skill *contents* that are confidential, even though naming the catalogue is encouraged.
  Listing the skills and what each is for is fine and is part of the portfolio framing;
  reproducing their bodies is not. Keep `cm` command internals, the code-review REST flows
  (`plastic-codereview-api`), localization keys (`localization-strings`), and the
  architecture map (`repository-architecture`) at the "this skill exists and does X"
  level, not a copy of the skill body.
- Specific model version numbers / pricing from the deck's "2026 state of the art" list,
  which date quickly and are partly internal pricing — keep model talk conceptual (Auto
  mode, reach for a stronger model on hard tasks, watch cost).
- Anything that would expose Unity-confidential codebase detail.

---

## Open choices to confirm during implementation

- Whether to include screenshots/diagrams (would go in `assets/images/`, referenced
  root-relative) or keep text-only for the first draft. *Current default: text-only.*
- How many reference links to include per post, and which subset from the list above.
- Whether post 2's catalogue tour stays inline or, if post 2 gets too long, moves to a
  short standalone follow-up.

---

## Verification

Since this is content, verification is a local Jekyll preview plus link/lint checks:

1. **Build & serve locally:** from `C:\UnitySrc\srombauts.fr`, run
   `bundle exec jekyll serve` and open the three new posts at their `/YYYY/MM/DD/slug/`
   URLs. Confirm they build with no Liquid/kramdown errors. (Dates are all in the past
   relative to 2026-06-08, so no `--future` flag is needed.)
2. **Check rendering:** headings, `toc: true` sidebar, code blocks, and reference-style
   links render correctly.
3. **Check cross-links:** the inter-post "next/previous" links resolve to the right
   permalinks (`/2026/01/29/...`, `/2026/02/12/...`, `/2026/03/25/...`).
4. **Tags:** confirm new posts appear under their tags on the tag archive page,
   including the three new tags (`ai`, `cursor`, `claude-code`).
5. **Content review:** re-read against the "explicitly omit" list to ensure no
   internal-only material leaked in from either source file.
6. **Humanizer pass (required):** confirm each post has been run through the `humanizer`
   skill, with a voice sample, and that no em/en dashes remain. See *VITAL: use the
   `humanizer` skill for all prose* above.
7. Do **not** commit or push until the author explicitly approves.
