# Working with Cursor: AI in Unity @ Wed Mar 25, 2026 4pm - 4:45pm (CET) (Sébastien Rombauts)

**Format:** Live demo session with minimal slides
**Duration:** ~45 min (demo-heavy) + Q&A
**Audience:** All engineers at Unity Technologies!

---

## Agenda

### 0. Catch phrase? Don't say hello, don't introduce you.

### 2. Introduction to Cursor (10 min)
- **What is Cursor**: VSCode-based IDE with built-in AI agent, not just autocomplete
- **Core features tour**:
  - Tab (multi-line autocomplete, partial accept with `Ctrl+Right`)
  - Inline Edit (`Ctrl+K`) — quick targeted changes
  - Agent mode (`Ctrl+I`) — autonomous coding partner
  - Plan mode (`Shift+Tab`) — gather context, reason, produce a plan before acting
  - Context feeding: `@Files`, `@Code`, `@Docs`, `@Folders`
- **Models**: Auto mode, Composer 1, Claude 4.5/4.6 Sonnet/Opus, GPT-5 — what's available and when to pick what
- **What sets it apart from Copilot**: agent mode, subagents, Skills, Rules, Commands

### 3. Customizing Cursor for Your Codebase (5 min)
- **Why out-of-the-box is not enough**: the agent doesn't know your codebase, your CLI, your conventions
- **Rules** (`.cursor/rules/`): declarative constraints, scoped by file globs
- **Skills** (`.cursor/skills/`): procedural how-to guides the agent loads on demand
- **Commands** (`.cursor/commands/`): reusable `/slash` workflows for the team
- Brief mention of `.cursorignore` for context hygiene

### 4. Cursor vs Claude Code: Speed, Cost & Strategy (7 min)
- **Side-by-side comparison**: same task in Cursor IDE vs Claude Code CLI
  - Cursor: visual diffs, Tab completions, inline edit, agent UI
  - Claude Code: terminal-first, works inside any IDE (Rider, VS), scriptable loops
- **Request model & cost**:
  - Cursor: 500 requests/month (Enterprise), but each request can be 1M+ tokens — very generous
  - Claude Code: token-based billing — cost scales with conversation length
- **Codebase indexation**: Cursor indexes your entire codebase; once ready, code search is dramatically faster and more accurate than the `grep`/`rg` calls that Claude Code relies on
- **Speed**: Cursor feels noticeably snappier in practice — faster responses, less waiting
- **Windows experience**: Cursor has better native integration with PowerShell; Claude Code runs through Bash/MSYS2 which doesn't always play well with Windows CLIs and tools
- **When to use what**:
  - Cursor for interactive exploration, plan mode, visual review, Windows-heavy workflows
  - Claude Code for CLI-driven workflows, CI integration, autonomous loops, non-IDE contexts
  - Using both as cross-check (run same task in two tools, compare output)

### 1. Quick Context (1 min)
- What is Unity Version Control (Plastic SCM) — the codebase we're demoing on

### 5. Live Demos: Skills in Action (20 min)

> All demos are live on the Unity Version Control codebase.

#### Demo A — Intro to Cursor UI & Tips & Tricks
- Live walkthrough of the Cursor interface (not slides)
- Tab completion (multi-line autocomplete, partial accept with `Ctrl+Right`)
- Inline Edit (`Ctrl+K`) — quick targeted changes
- Agent mode (`Ctrl+I`) — autonomous coding partner
- Plan mode — gather context, reason, produce a plan before acting
- Context feeding: `@Files`, `@Code`, `@Docs`, `@Folders`
- Tips: checkpoints & rollback, fresh sessions, model selection (Auto, Claude 4.5/4.6, GPT-5)
- What sets Cursor apart from Copilot: agent mode, subagents, Skills, Rules, Commands

#### Demo B — Setting Up Jira & Confluence MCP Servers (full VPN required)
- What are MCP servers and why they matter — external tools the agent can use
- Walk through the MCP configuration in `.cursor/mcp.json`
- Set up Jira MCP: API token generation, connection test
- Set up Confluence MCP: API token, test reading a page
- Live: query a Jira ticket and read a Confluence page from Cursor
- Note: requires full VPN connection to Unity's internal instances

#### Demo C — Handling a small task: bug fix or minor feature
- Start from a Jira ticket
- Agent creates a branch via CLI skill (`cm` commands)
- Agent mode: implement the fix across multiple files
- Highlight: the agent doesn't know `cm` out of the box; the skill is what makes it work

#### Demo D — Code review of the task
- Run a code review on the branch from Demo C
- Show the review skill: what rules it enforces, how it structures feedback
- Compare: quick review in Cursor agent vs structured review via Claude Code `/code-review`

#### Demo E — Generating CHANGELOG for a package release
- Show the release-notes skill in action
- Agent gathers merged tasks, writes CHANGELOG entries
- Review and refine the output

#### Demo F — Planning more complex development
- Start from a larger Jira ticket or feature request
- Plan mode: gather context, produce a plan, get approval before touching code
- Agent mode: begin implementation following the plan
- Review: use checkpoints, rollback if needed

#### Bonus — Writing & sharing a Skill (if time permits)
- Live-create a simple skill from a repeated workflow
- Show the skill structure (SKILL.md, frontmatter, folder layout)
- Commit it — now the whole team benefits

### 4. Cursor vs Claude Code: Speed, Cost & Strategy (5 min)
- **Side-by-side comparison**: same task in Cursor IDE vs Claude Code CLI
  - Cursor: visual diffs, Tab completions, inline edit, agent UI
  - Claude Code: terminal-first, works inside any IDE (Rider, VS), scriptable loops
- **Request model & cost**:
  - Cursor: 500 requests/month (Enterprise), but each request can be 1M+ tokens — very generous
  - Claude Code: token-based billing — cost scales with conversation length
- **Codebase indexation**: Cursor indexes your entire codebase; code search is dramatically faster than the `grep`/`rg` calls that Claude Code relies on
- **Speed**: Cursor feels noticeably snappier in practice — faster responses, less waiting
- **Windows experience**: Cursor has better native integration with PowerShell; Claude Code runs through Bash/MSYS2 which doesn't always play well with Windows CLIs and tools
- **When to use what**:
  - Cursor for interactive exploration, plan mode, visual review, Windows-heavy workflows
  - Claude Code for CLI-driven workflows, CI integration, autonomous loops, non-IDE contexts
- **Choosing a model**: when to use Auto, when to pick a specific model, cost implications
- **Tracking your spending**: where to find usage dashboards, how to monitor token/request burn

### 5. Key Takeaways (2 min)
- **Customize or lose**: out-of-the-box AI is generic; Rules + Skills make it yours
- **Context hygiene**: fresh sessions, surgical context, avoid compacting
- **Share what works**: if you repeat a prompt twice, make it a Command or Skill
- **Review everything**: AI is a junior dev, you are the tech lead

### 6. ANNEXES
- list of our skills (committed) — matches **Available Skills** in `.claude/skills/README.md` (eight documented; the repo also has seven additional skill folders not yet called out there)
  - `development-workflow`
  - `csharp-code-style`
  - `code-review`
  - `release-notes`
  - `plastic-scm-cli-reference`
  - `jira-mcp-server`
  - `confluence-mcp-server`
  - `unity-plugin-release`
- list of ideas of new skills (some drafts on my machine) — seven extra skill folders in this repo (not in README yet)
  - `agent-response-style`
  - `localization-strings`
  - `logging-debugging`
  - `threadwaiter-async-pattern`
  - `unity-plugin-ci`
  - `unity-plugin-development`
  - `unity-plugin-testing`

---

## Pre-session Setup (for attendees)

- Cursor installed and logged in with `@unity3d.com` account
- (Optional) Claude Code installed if you want to follow along with CLI demos
- (Optional) Full VPN connected if you want to try MCP server setup afterward
- No codebase checkout required — this is a watch-and-learn session

---

## Calendar Invite

Subject: How We Use Cursor on the Unity Version Control Codebase

Join special guest Sébastien Rombauts and Co. for a live demo of how the Unity Version Control team uses Cursor to accelerate development on a large C#/.NET codebase, with a focus on the Unity Version Control package for the Editor.

- Goals:
  - Fight back Claude Code dominance at Unity & among power user ;)
  - Everyone would benefit using both Claude Code & Cursor
  - Show real usage and experience based on mistakes we made
- Introduction to Cursor:
  - What it is, core features, and what sets it apart from Claude Code
  - How we customized Cursor for our codebase and our CLI
  - How we write and share Skills so the whole team benefits
- Live demos:
  - Intro to Cursor UI and tips & tricks
    - Choosing a model
    - Tracking your spending
  - Setup Jira & Confluence MCP Servers (full VPN required)
  - Handling a small task: bug fixing or minor feature in the Unity package
  - Code review of the task
  - Generating CHANGELOG for a package release
  - Planning more complex development
- Cursor vs Claude Code: speed, cost, and strategies on when to use each

**Format:** ~40 min of live demos + Q&A. Minimal slides. Bring your questions.

**Prerequisites:** None, it is a watch-and-learn session. Having Cursor installed is a plus if you want to try things afterward.
