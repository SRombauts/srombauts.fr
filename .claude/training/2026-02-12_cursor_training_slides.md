# Using Cursor on our codebase - demo & sharing tips @ Thu Feb 12, 2026 1pm - 1:50pm (CET) (Sébastien Rombauts)

**Duration:** ~40 min presentation + 10 min live demo + Q&A
**Audience:** Senior Software Engineers++

---

slides: show a picture of Context in LLM : <model == knowlodge> + <system prompt == personality> +<rules> + Nx <prompt> (history of the discussion)

show an OLD RULE, like the .github/copilot-instructions.md
> It's a README.md for the AI

Discuss about introspections of custom context / rules / 
> Without reading any file form the project, please tell me what you have already loaded into your context, and tell me from which file it's being loaded.


## 1. Introduction & goals (3 mins)

### The shift
*   From: "writing code" (typing syntax, remembering boilerplate).
*   To: "architecting, reviewing & curating code"—think of yourself as a tech lead delegating to a junior: give specs, set acceptance criteria, review the output.
*   Goal: move from "light users" (Ask / Tab / Inline Edit only) to "power users" (Rules, Commands, Skills, and Agent, Plan, Debug modes).
*   **Agent-first mindset**: The tool of first resort should be interacting with an agent, not opening an editor or terminal. This is a cultural shift, not just tooling.
    *   *Reference*: [Greg Brockman on agentic software development](https://x.com/gdb/status/2019566641491963946) — OpenAI's internal approach to retooling teams.

### Why standardize?
*   Individual productivity is fine, but team sharing increases our collective velocity.
*   We need to share our "magic prompts" and enforce our architectural constraints automatically.
*   Building on the Cursor training (large codebase, Skills, Subagents), this session focuses on daily practice and team culture.

---

## 2. LLM Coding Concepts (10 mins)

### Static & stateless
*   Mental model: LLMs are "static executables", frozen in time (training cutoff) and stateless (no memory between sessions).
*   Implication: they don't know our codebase, our workflows, or our "unwritten rules". They don't learn from previous chats.
*   It's like having a new intern showing for every task
*   The solution: give context every time, or use Rules/Skills to automate it.
*   *Reference*: [Large Language Model Concepts (Medium)](https://medium.com/@daveziegler/large-language-model-concepts-for-curious-users-the-static-stateless-and-directional-nature-of-a0f4d8ec2972)

### Context window & "compacting"
*   The context window is not infinite.
*   Garbage in, garbage out: irrelevant files lead to hallucinated or generic answers.
*   "Compacting" is a warning sign: when context fills up, the agent compacts (summarizes) history. That's lossy.
    *   *Rule of Thumb*: If you trigger compacting, you likely dumped too much irrelevant data.
    *   *Reference*: [How Long Contexts Fail](https://www.dbreunig.com/2025/06/22/how-contexts-fail-and-how-to-fix-them.html) — why "more context" isn't always better (distraction, poisoning).
*   **Context rot**: As conversations grow, the quality of agent responses degrades.
    Earlier context gets compressed, misinterpreted, or lost entirely.
    *   *Best practice*: Stay in the first half of the context window. Start a new session for each task.
*   Strategy: be surgical. Start new chats. Use skills (more on that later).

### "Thinking" (chain of thought)
*   Concept: the model can "think" (generate hidden reasoning tokens) before answering, to plan its approach.
*   Thinking budget: models like `Claude 4.6 Sonnet` let you allocate a "thinking budget".
    *   *Keywords*: In some interfaces (like Claude Code), keywords like "think harder" or "ultrathink" increase this budget.
    *   *Trade-off*: Extended reasoning is powerful for complex architecture but can lead to "overthinking" on simple tasks (getting distracted by irrelevant details).
    *   *Reference*: [Inverse Scaling in Test-Time Compute](https://arxiv.org/pdf/2507.14417) — why thinking longer isn't always better.

### Nondeterminism
*   Reality: the same prompt can produce different outputs each time (temperature, sampling).
*   Implication: don't expect deterministic behavior. Tests and review loops are essential.
*   *Reference*: [Why LLMs are Non-Deterministic](https://www.hopsworks.ai/dictionary/llm-non-determinism)

### Hallucinations & grounding
*   Hallucinations: LLMs often produce plausible-sounding but wrong information.
*   Mitigations:
    *   Ground the model with **specific context** (`@Files`, `@Code`).
    *   Ask for **citations** ("Show me where this is defined").
    *   **Review everything** — treat output like a junior's PR.
*   *Reference*: [Prompt Engineering Guide (OpenAI)](https://platform.openai.com/docs/guides/prompt-engineering)

### Prompt shape (2-minute checklist)
Use a consistent structure so the agent can act deterministically:
*   Goal: what outcome do you want?
*   Constraints: non-negotiables (rules, style, forbidden patterns).
*   Context: attach the minimum via `@Files & Folders` / `@Code` / `@Docs`.
*   Acceptance criteria: what must be true at the end (tests, behavior, perf)?

### RAG (Retrieval-Augmented Generation)
*   Cursor automatically indexes your codebase.
*   When you ask a question, it searches for relevant chunks *before* sending to the LLM.
*   *Tip*: Better variable names = Better RAG results.
*   *Reference*: [Securely Indexing Large Codebases](https://cursor.com/blog/secure-codebase-indexing)

### Tools & MCP (Model Context Protocol)
*   LLMs are not just text generators; they can act (read, run, call APIs).
*   Tools: read files, search the web, run terminal commands.
*   MCP: standard for connecting to external data (Linear, Postgres, Localhost).
    *   *Reference*: [Model Context Protocol (MCP)](https://cursor.com/docs/context/mcp)

### Models (2026 state of the art)
*   `Composer 1` (Cursor native): frontier model for low-latency agentic coding.
    *   *Performance*: near frontier-level; Cursor's blog notes that `Claude 4.5 Sonnet`
        and `GPT-5` score higher, but Composer is ~4x faster.
    *   *Reference*: [Building a fast frontier model with RL](https://cursor.com/blog/composer)
*   `Claude 4.5 Sonnet`: strong reasoning, balanced speed. The default workhorse.
*   `Claude 4.6 Opus`: best for complex coding when you need maximum reasoning.
    *   **Cost note**: output tokens cost ~1.7x more than Sonnet. Use it for
        hard tasks, not routine edits.
*   `GPT-5.3 Codex`: High speed, broad knowledge. Codex variant tuned for coding.
*   `Gemini 3 Pro`: Large context handling (up to 1M tokens in Max Mode).
*   Unity best practice: set model to **Auto** for most tasks.
    *   Why: it helps avoid errors when a provider hits capacity limits
        (concurrent instances).
    *   Cost note: Auto pricing isn't cheaper than picking a model directly.
    *   *Reference*: [Models](https://cursor.com/docs/models)
*   Track usage: [Dashboard](https://cursor.com/dashboard?tab=usage) — 500 requests/month per user (Enterprise).

---

## 3. Onboarding the AI: Rules, Skills & Team Knowledge (10 mins)

### Dynamic Context Discovery
Since LLMs are stateless (see Section 2), we need to provide context. But instead of dumping everything into the prompt (Static Context), we let the agent *discover* what it needs.
*   *Reference*: [Dynamic Context Discovery (Cursor Blog)](https://cursor.com/blog/dynamic-context-discovery)

### The "Onboarding" Stack
We emulate an onboarding process by providing documentation the agent can read on-demand:

1.  **Rules** (`.cursor/rules/`): Project constraints and guidance.
    *   Includes **Project Rules**, **User Rules** (global), and **Team Rules** (dashboard).
    *   *Reference*: [Rules](https://cursor.com/docs/context/rules)
2.  **Commands** (`.cursor/commands/`): Reusable `/` workflows to standardize prompts.
    *   *Reference*: [Commands](https://cursor.com/docs/context/commands)
3.  **Skills** (`.cursor/skills/`): Procedural knowledge ("How to do Y").
    *   *Reference*: [Agent Skills](https://cursor.com/docs/context/skills)

**Note on AGENTS.md:** Some projects use a single `AGENTS.md` file at the root instead of `.cursor/rules/`.
We favor the modular `.cursor/rules/` approach because it supports glob-based scoping
(e.g., Unity plugin-specific rules only apply to Unity plugin files).
This keeps context clean and prevents irrelevant rules from being loaded.
*   **Best practice from OpenAI**: "Create and maintain an AGENTS.md for any project you work on;
    update the AGENTS.md whenever the agent does something wrong or struggles with a task."
    *   *Reference*: [Greg Brockman on agentic software development](https://x.com/gdb/status/2019566641491963946)

### `.cursor/rules/` (Declarative Constraints)
*   **What**: Instructions the agent *must* follow. "Always do X", "Never do Y".
*   **Example**:
    *   *Constraint*: "Never use `async/await`. Use `ThreadWaiter` pattern."
    *   *Constraint*: "Line length <= 100 chars."
*   **Effect**: The agent reads this *automatically* when working on relevant files.

### `.cursor/skills/` (Procedural Workflows - Cursor 2.4)
*   **What**: Step-by-step guides for specific tasks (e.g. "How to add a localized string").
*   **Why**: Better than rules for complex how-to; keeps context clean. Agent loads SKILL.md only when relevant.
*   **Usage**: Invoke via `/` in Agent chat, or let the agent apply it when relevant.
*   **Structure**: One folder per skill → `skill-name/SKILL.md` (required) + optional `reference.md`, `scripts/`.
*   **Cross-tool**: Cursor also reads from `.claude/skills/` and `.codex/skills/`, so skills are portable.
*   **Community**: [skills.sh](https://skills.sh/) — `npx skills add <owner/repo>`.
*   **Writing skills**: See **Annex B** for naming, descriptions, and best practices.
*   **Codify successful workflows**: "Write skills for anything that you get Cursor to do, and commit it to the skills directory."
    This turns one-off successes into repeatable team knowledge.
    *   *Reference*: [Greg Brockman on agentic software development](https://x.com/gdb/status/2019566641491963946)
*   *Reference*: [Agent Skills](https://cursor.com/docs/context/skills) · [skill.md standard (Mintlify)](https://www.mintlify.com/blog/skill-md) · [Cursor 2.4](https://cursor.com/changelog/2-4)
    *   *Reference*: [Don't Build Agents, Build Skills Instead — Barry Zhang & Mahesh Murag, Anthropic (YouTube)](https://youtu.be/CEvIs9y1uog) — Why skills beat agents: packaging procedural knowledge that agents can dynamically load.

### `.cursor/commands/` (Reusable Workflows)
*   **What**: Project-wide slash commands (markdown prompts) to standardize repeat tasks.
*   **Why**: Replace legacy "custom modes" with shareable, version-controlled workflows.
*   **Examples**:
    *   `/code-review-task`: Review a branch or task against our Plastic constraints.
    *   `/code-review-pending-changes`: Review local pending changes before checkin.
    *   `/write-tests`: Generate focused NUnit tests for a change.
    *   *Reference*: [Commands](https://cursor.com/docs/context/commands)

### `.cursorignore`
*   **What**: `.gitignore` for the LLM.
*   **Why**: Keep the context clean. Ignore logs, build artifacts, huge auto-generated files.
*   **Benefit**: Saves tokens, improves accuracy, prevents "reading" binary files.
*   **Also**: `.cursorindexingignore` excludes from indexing only (still readable by AI).
    *   *Reference*: [Ignore files](https://cursor.com/docs/context/ignore-files)

### Action Item
*   We need a process for PRing changes to `.cursor/`.
*   If you find a prompt that works perfectly, **codify it** into a Skill.
*   Team heuristics:
    *   If you repeat a prompt twice: make it a **Command**.
    *   If Agent repeats a mistake twice: tighten a **Rule** (scoped by `globs`).
    *   If it's a multi-step SOP: write a **Skill**.

---

## 4. Cursor Power User Features (10 mins)

### Agent Modes (switch with `Ctrl+.`)
*   **Ask Mode**: Read-only. Use when exploring code or asking questions without making changes.
*   **Agent Mode (Act)**: The default. The Agent takes "destructive" action (writing files, running scripts).
    *   *Use when*: You know what needs to be done. "Do X."
*   **Plan Mode** (`Shift+Tab` to toggle):
    *   *Concept*: The Agent gathers information, reasons, and produces a plan *without* making changes yet.
    *   *Workflow*: Ask for a plan -> Review/Refine -> Accept (switches to Act mode).
    *   *Why*: "Pump the brakes" on aggressive agents. Great for architecture or exploring unknown codebases.
    *   *Tip*: "Save to workspace" stores plans in `.cursor/plans/` for documentation and team sharing.
*   **Debug Mode**: Switch to Debug when troubleshooting errors or unexpected behavior.
    It generates hypotheses, adds instrumentation, asks you to reproduce, then fixes based on runtime evidence.
*   **Subagents** (Advanced — Cursor 2.4):
    *   **Concept**: Spawning a "clean" instance of the agent with its own independent context window.
    *   **Why**: Parallelism (run 2+ agents) and Context Hygiene (don't pollute main chat with huge logs).
    *   **Built-in**: Explore (codebase search), Bash (shell commands), Browser (web interactions).
    *   **Custom**: Define your own in `.cursor/agents/` (e.g., a verifier subagent).
    *   *Reference*: [Subagents](https://cursor.com/docs/context/subagents)

### Agent
*   **Agent**: The autonomous coding partner.
    *   Can spawn **Subagents** (Cursor 2.4) to handle research or terminal commands in parallel.
    *   Can ask **Clarifying Questions** if your prompt is ambiguous.
    *   **Workflow Tips**:
        *   **Queue Messages**: Type `Enter` to queue instructions while Agent is working.
        *   **Interrupt**: `Ctrl+Enter` to send immediately (bypassing queue).
        *   **Checkpoints**: Auto-snapshots of Agent changes; restore if it goes off rails.
        *   **Summarize**: Use `/summarize` if the chat gets too long.

    *   *Reference*: [Subagents](https://cursor.com/docs/context/subagents)
    *   *Reference*: [Agent Overview](https://cursor.com/docs/agent/overview)

### Tab
*   Cursor's autocompletion model (multi-line edits and cross-file jumps).
*   It uses recent edits and accepted suggestions to infer intent.
*   *Tip*: If you tab through a change, verify it! Don't sleepwalk.
*   **Power Moves**:
    *   **Partial Accept**: `Ctrl+Right` to accept word-by-word.
    *   **Auto-Import**: Tab automatically adds missing imports.
    *   **Tab in Peek**: Works inside "Go to Definition" windows.
    *   *Reference*: [Tab](https://cursor.com/docs/tab/overview)

### Inline Edit (Ctrl+K)
*   Edit a selection (or insert new code) with a short instruction.
*   Use "Quick Question" to ask about selected code before changing it.
    *   *Reference*: [Inline Edit](https://cursor.com/docs/inline-edit/overview)

### Context is King (@ Symbols)
*   `@Files & Folders`: Attach exact files (most reliable).
*   `@Folders`: Provide a folder map and drill down with `/`.
*   `@Code`: Attach a specific code snippet (more surgical than whole files).
*   `@Docs`: Attach documentation (and optionally share docs with the team).
*   `@Past Chats`: Reference earlier conversations without copy-pasting. Agent selectively pulls what it needs.
*   `@Branch`: Give the agent context about your current work ("Review the changes on this branch").
*   Note: explicit `@Web` / `@Git` menu items were removed in Cursor 2.x. Ask Agent
    directly to review diffs or fetch docs; it will use tools as needed.
*   *Reference*: [Cookbook: Large Codebases](https://cursor.com/docs/cookbook/large-codebases)
    *   *Reference*: [@ Mentions](https://cursor.com/docs/context/mentions)

### Unit testing
*   Cursor is very good at test boilerplate.
*   *Prompt*: "Write three unit tests for this function using NUnit, covering the success case, a failure case with invalid input, and a null reference exception."

### Reviewing AI-generated code
*   **During generation**: Watch the diff view; press **Escape** to interrupt if it goes off track.
*   **Agent Review**: After the agent finishes, click **Review → Find Issues** to run a dedicated self-critique pass on the diffs.
*   **Bugbot**: Push to source control for automated PR reviews. [Bugbot](https://cursor.com/docs/bugbot)
    *   *Reference*: [Agent Review](https://cursor.com/docs/agent/review)

### Parallel agents & worktrees
*   Cursor can run multiple agents in parallel using [git worktrees](https://cursor.com/docs/configuration/worktrees).
    Each agent works in its own isolated copy of the repo.
*   You can also run the **same prompt across multiple models** simultaneously and compare results.
*   Useful for hard problems where different models take different approaches.

### Hooks (Advanced)
*   `.cursor/hooks.json`: Run scripts before or after agent actions.
*   Example: a "stop" hook that re-runs the agent until all tests pass (loop agent pattern).
    *   *Reference*: [Agent Best Practices (hooks section)](https://cursor.com/blog/agent-best-practices)

### Sharing & Security (Team Hygiene)
*   **Shared transcripts**: Share a read-only chat link, and let others fork from it.
    Great for spreading \"known-good\" prompting patterns.
    *   *Reference*: [Shared transcripts](https://cursor.com/docs/shared-transcripts)
*   **Security controls**: Understand approvals, `.cursorignore`, and MCP safety.
    *   *Reference*: [Agent Security](https://cursor.com/docs/agent/security)

### Cursor Blame (Git only — Enterprise)

> **Brief mention** — skip details if short on time.

*   See exactly which lines were generated by AI vs. Humans.
*   Useful for tracking adoption and code quality.
    *   *Reference*: [Cursor Blame](https://cursor.com/docs/integrations/cursor-blame)

### Cloud Agents (Advanced)

*   **What**: Asynchronous agents running in isolated cloud environments (Ubuntu VMs).
*   **Use Case**: Long-running tasks, fixing CI failures, iterating on tests without blocking your local machine.
*   **Setup**: `Cursor: Start Cloud Agent Setup` (creates `.cursor/environment.json`).
    *   *Reference*: [Cloud Agents](https://cursor.com/docs/cloud-agent)

### Cursor CLI (Agent in Terminal)
*   **Concept**: Bring the Agent *to* your IDE (Rider, VS, Vim), instead of switching editors.
*   **The "Copilot Killer" Workflow**:
    *   Open Rider/VS for its superior debugger and C# refactoring tools.
    *   Open the **integrated terminal** in Rider/VS.
    *   Run the Cursor CLI to chat with the agent and modify files in place.
*   Why: you keep Rider's tooling (debugger, refactoring) and add Cursor's reasoning in the same repo.
*   *Reference*: [Cursor CLI Blog](https://cursor.com/blog/cli)

---

## 5. Live Demo (10 mins)

**Scenario**: Full Workflow on a Real Task.
*   I will pick a real Jira task from our backlog.
*   **Demonstrate**:
    1.  **Branch**: Create a new branch for the task.
    2.  **Plan Mode**: Create a plan from the Jira description.
        *   *Tip*: "Save to workspace" to store in `.cursor/plans/` for documentation.
    3.  **Agent (Ctrl+I)**: Implement the changes across multiple files.
    4.  **Review + Checkpoints**: Verify changes, roll back if needed.
        *   *Tip*: Use **Review -> Find Issues** to let AI self-critique the diffs.
    5.  **Share**: Export or share a transcript for the team to learn from.
    6.  **Check-in**: Draft a commit message (always review).

---

## 6. Takeaways & Resources (5 mins)

### Key Takeaways

**Customization is essential:**
*   **Don't use it "out of the box".** If you use Cursor with zero customization, you're using it wrong.
*   **Stop prompt engineering.** If you spend time crafting complex prompts (like with ChatGPT), you're probably compensating for missing context.
*   **Customize it.** Rules and Skills adapt the AI to your project and workflows.

**If Agent results are poor quality:** Try adding rules, custom context, or skills. That's usually what's missing.

**Prompt precision and batching:**
*   Be precise in your prompt, and bundle related changes into one request if you
    know what you are doing. It counts as a single request, as opposed to a back and forth chat.

**Context rot:**
*   As conversations grow, agent quality degrades. Stay in the first half of the context window.
*   Start a new session for each task to maintain quality and clarity.

**Task framing:**
*   Assign tasks, don't ask questions.
*   If you treat AI like an oracle, you're using the wrong mental model.
*   Use a declarative spec: describe the end state and specify acceptance criteria.

**Appropriate tasks:**
*   Code that can be compiled and run locally by the agent, with unit tests.
    Avoid tasks that depend on CI infrastructure or new UI design.
*   Apply existing patterns: add a new test, add a new dialog, or copy a package
    from another repo.
*   Read logs and callstacks, then find the corresponding code.

**Inapropriate tasks:**
*   **Bad**: "Review the entire codebase to verify all the rules"
    - Too broad; agent will hit context limits, produce shallow results, or trigger compacting.
*   **Better**: "Check one rule for which tool pattern matching can be used"
    - More focused, but still requires scanning many files for a single concern.
*   **Far better**: "Review thoroughly a set of files against all the rules"
    - Surgical scope: deep analysis on a manageable set of files.
    - Agent can apply all constraints and provide actionable feedback.

**Say no to slop:**
*   Maintain at least the same quality bar for AI-generated code as for human-written code.
*   Ensure that some human is accountable for any code that gets merged. Review every change.
*   Avoid "functionally-correct but poorly-maintainable code" creeping into the codebase.
*   *Reference*: [Greg Brockman on agentic software development](https://x.com/gdb/status/2019566641491963946) — "Managing AI generated code at scale is an emerging problem, and will require new processes and conventions to keep code quality high."

**Agent-first codebase structure:**
*   Write tests that are quick to run locally.
*   Create high-quality interfaces between components (clear boundaries, minimal coupling).
*   Make internal tools agent-accessible via CLI or MCP servers.
*   *Reference*: [Greg Brockman on agentic software development](https://x.com/gdb/status/2019566641491963946)

### Resources
*   [Getting Started with Cursor (Confluence)](https://confluence.unity3d.com/spaces/AIUnity/pages/522061994/Getting+Started+with+Cursor)
*   **Cursor official docs**:
    *   [Rules](https://cursor.com/docs/context/rules)
    *   [Commands](https://cursor.com/docs/context/commands)
    *   [Agent Skills](https://cursor.com/docs/context/skills)
    *   [@ Mentions](https://cursor.com/docs/context/mentions)
    *   [Modes](https://cursor.com/docs/agent/modes)
    *   [MCP](https://cursor.com/docs/context/mcp)
    *   [Agent Best Practices](https://cursor.com/blog/agent-best-practices)
*   **LLM Fundamentals**:
    *   [Building Effective Agents (Anthropic)](https://www.anthropic.com/research/building-effective-agents)
    *   [Prompt Engineering Guide (OpenAI)](https://platform.openai.com/docs/guides/prompt-engineering)
    *   [Structured Outputs (OpenAI)](https://platform.openai.com/docs/guides/structured-outputs)
*   **Skills (writing & best practices)**:
    *   [Annex B: Best practices for writing SKILL.md](#annex-b-best-practices-for-writing-skillmd) (in this doc).
    *   [Annex C: Using AI to create a new SKILL.md](#annex-c-using-ai-to-create-a-new-skillmd) — use the **create-skill** skill so the agent follows a structured workflow.
    *   [Annex D: Probing the agent's context](#annex-d-probing-the-agents-context-skill-discoverability) — check whether skills and rules are discoverable.
    *   [Skill authoring best practices (Anthropic)](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices) — naming (gerund vs noun), conciseness, progressive disclosure.
    *   [anthropics/skills (GitHub)](https://github.com/anthropics/skills) — official examples, skill-creator, template.
    *   [The Complete Guide to Building Skills for Claude (PDF)](https://resources.anthropic.com/hubfs/The-Complete-Guide-to-Building-Skill-for-Claude.pdf?hsLang=en) — planning, structure, testing, patterns.
    *   [skill.md open standard (Mintlify)](https://www.mintlify.com/blog/skill-md) · [skills.sh](https://skills.sh/) — `npx skills add <owner/repo>`.
*   **Anysphere Training Recordings**:
    *   [Part 1](https://unity3d.zoom.us/rec/play/CwbGkyDF_jMWEGNY5mKuPc6GhGJz6m8CfhbPbKLtyLPYtvE89VJ[…]NWqCGriHQfDUhU_AcQDe-BesPaARsKthOpz-klgAsWbU.JzywY2onReYsb2gF)
    *   [Part 2](https://unity3d.zoom.us/rec/play/UHQ4GudhGZezPePGnH55FnYjD05whgZ9SA2HylAHxSo9LBXq0s-[…]Ak1Yb2JqHp2xt47eunnywjZzHbdxL6pRKLgvzrCmkfKt.MBycc5wwbQC-GqBH)

### Next Steps
1.  [ ] **Version**: Keep `.cursor/rules/`, `.cursor/skills/`, and `.cursor/commands/` in the repo (shared via codice@cloud).
2.  [ ] **Ignore**: Add `.cursorignore` at repo root (template in `.cursor/training/cursorignore.template`).
3.  [ ] **Agents Captain**: Designate a primary person on each team responsible for thinking about how agents can be brought into workflows, sharing experiences, and maintaining team skills/rules.
    *   *Reference*: [Greg Brockman on agentic software development](https://x.com/gdb/status/2019566641491963946)
4.  [ ] **Contribute**: Each team member adds one Rule/Command/Skill they wish the AI knew.
5.  [ ] **Share**: Post your best "aha!" moments (or a shared transcript) in `#cursor`.


---

## 7. Claude Code (Anthropic) (2 mins)

> **SKIP during session** — mention briefly (1 min) as an alternative tool; details are for self-study.

Claude Code is Anthropic's coding assistant. It runs in the terminal, IDEs, and on the web, so it fits well
when you prefer a CLI-first workflow or want direct access to Claude models for coding tasks.

### What it is
*   **Agentic coding tool**: You describe a task, it works in your repo, edits files, and can run commands.
*   **Multiple surfaces**: Terminal, IDE integrations, and web UI (useful when you are not in an editor).
*   **Good for**: Deep codebase exploration, refactors, and "do the work for me" tasks where you still
    review every change.

### Key differences vs Cursor (in practice)
*   **Surface**: Cursor is a full IDE with built-in agent, Tab, and Inline Edit. Claude Code is a tool you
    run from terminal/IDE/web and bring into your existing editor.
*   **Configuration**: Cursor uses `.cursor/` rules, skills, and commands; Claude Code uses `.claude/`
    (we should decide whether to use .claude/skills that Cursor can read).
*   **Approachability vs power**: Cursor tends to be easier for newcomers; Claude Code is often perceived as
    more advanced or CLI-oriented. Our team should validate this with hands-on use.

### Why consider using both
*   **Cross-check outputs**: Run the same task in two tools and compare; it catches mistakes and bias.
*   **Complementary workflows**: Cursor for interactive IDE work, Claude Code for terminal-first or web
    sessions.
*   **Capacity and credits**: You can switch tools if one is rate-limited, unavailable, or you want to use
    a different pool of credits (if licensing allows).

### Team decision point: `.cursor` vs `.claude`
We should discuss whether to support both configuration stacks or standardize on one. Supporting both gives
flexibility but risks drift and duplicate maintenance. A reasonable middle ground is to keep a single source
of truth for constraints and duplicate only the minimal onboarding guidance in the other tool.

### References
*   [Claude Code](https://www.anthropic.com/claude-code)
*   [Claude Code docs](https://docs.anthropic.com/en/docs/claude-code)
*   [How Anthropic teams use Claude Code](https://www.anthropic.com/news/how-anthropic-teams-use-claude-code)
*   [What is Claude Code? (Zapier)](https://zapier.com/blog/claude-code/)

---

## 8. Advanced reading: under the hood (skip)

> **SKIP during session** — this section is reference material for attendees to explore on their own.

These resources cover the concepts (Skills, Subagents, context) that modern AI coding agents share.

*   **Agent Skills (Deep Dive)**:
    *   [Don't Build Agents, Build Skills Instead — Barry Zhang & Mahesh Murag, Anthropic (YouTube)](https://youtu.be/CEvIs9y1uog) — Talk from Dec 2025 on why skills are the solution for giving agents domain expertise. Covers how Anthropic built Skills, network effects, and the vision of agents writing their own skills from experience.
    *   [Equipping agents for the real world with Agent Skills](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) — The engineering philosophy behind Skills.
    *   [anthropics/skills](https://github.com/anthropics/skills) — Reference implementations for complex skills (e.g., "Deep Research", "Code Review").
*   **Autonomous Coding Loops**:
    *   [Ralph Wiggum as a "software engineer"](https://ghuntley.com/ralph/) — The original post on the Ralph Wiggum Technique by Geoff Huntley.
    *   [A Brief History of Ralph](https://www.humanlayer.dev/blog/brief-history-of-ralph) — Real-world use cases, lessons learned, and field reports.
    *   [We Put a Coding Agent in a While Loop](https://github.com/repomirrorhq/repomirror/blob/main/repomirror.md) — Y Combinator hackathon field report: shipped 6 repos overnight.
*   **Cursor CLI**:
    *   [Cursor CLI Blog](https://cursor.com/blog/cli) — Official announcement and use cases.
*   **Internal Reference**:
    *   *[Getting Started With Claude Code](https://docs.google.com/document/d/1ikQIXv2x1qbOLAGn7OTJ5cyzUP9vu6KfJp43HYRcNJE/)* (Internal Doc) — Contains detailed explanations of Act/Plan and Thinking modes.

---

## Annex A: Access & setup (prerequisites)

Complete these steps **before** the training session:

*   **Request Access**: [Unity Helpdesk](https://helpdesk.unity3d.com/support/catalog/items?popular=true).
*   **Download**: [Cursor Downloads](https://cursor.com/downloads).
*   **Login**: Use your `@unity3d.com` Google account.
*   **Privacy Mode**: Ensure work is covered by your team's policy (see Unity onboarding).
*   *Reference*: [Getting Started with Cursor (Confluence)](https://confluence.unity3d.com/spaces/AIUnity/pages/522061994/Getting+Started+with+Cursor)

---

## Annex B: Best practices for writing SKILL.md

This annex summarizes how to write effective Agent Skills so the agent can discover and use them. For full detail, use the official references below.

### References

| Resource | Content |
|----------|--------|
| [Skill authoring best practices (Anthropic)](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices) | **Naming:** “We recommend gerund form (verb + -ing)”; acceptable: noun phrases (e.g. `skill-creator`), action-oriented. Plus conciseness, progressive disclosure, checklist. |
| [anthropics/skills (GitHub)](https://github.com/anthropics/skills) | Official skill repo: examples, **skill-creator** (create new skills), template, doc/PDF/PPTX/XLSX reference skills. |
| [The Complete Guide to Building Skills for Claude (PDF)](https://resources.anthropic.com/hubfs/The-Complete-Guide-to-Building-Skill-for-Claude.pdf?hsLang=en) | Planning, file structure, YAML frontmatter, testing, distribution, patterns (workflow orchestration, MCP enhancement). |
| [skill.md: An open standard (Mintlify)](https://www.mintlify.com/blog/skill-md) | Design tips: decision tables, boundaries, gotchas; link out instead of duplicating. |

### File and folder structure

*   **Required**: One folder per skill, containing exactly `SKILL.md` (case-sensitive).
*   **Optional**: `reference.md`, `examples.md`, `scripts/` for progressive disclosure.
*   **Paths**: Use forward slashes (`scripts/helper.py`). No Windows-style backslashes.
*   **References**: Keep links one level deep from SKILL.md so the agent loads complete files.

### Naming conventions

| Item | Rule | Examples |
|------|------|----------|
| **Folder / `name` in frontmatter** | kebab-case only; lowercase letters, numbers, hyphens. Max 64 chars. | `processing-pdfs`, `localization-strings` |
| **Preferred style** | Gerund form (verb + -ing) or noun phrase. | ✅ `analyzing-spreadsheets`, `code-review` |
| **Verb form** | Prefer gerund (Anthropic best practices); noun phrase acceptable (e.g. Anthropic’s `skill-creator`). Be consistent. | ✅ `writing-skills` · ✅ `skill-creator` |
| **Avoid** | Vague names, spaces, underscores, capitals. Reserved: `anthropic`, `claude`. | ❌ `helper`, `utils`, `My Cool Skill` |

### YAML frontmatter (required)

```yaml
---
name: your-skill-name
description: What it does. Use when [trigger phrases].
---
```

*   **`name`**: kebab-case, ≤64 chars, no XML tags.
*   **`description`**: Non-empty, ≤1024 chars. **Critical for discovery** — the agent uses it to decide when to load the skill.
    *   **WHAT**: Specific capabilities (e.g. "Extract text and tables from PDFs, fill forms").
    *   **WHEN**: Trigger scenarios and phrases (e.g. "Use when working with PDF files or user mentions PDFs, forms").
    *   **Voice**: Third person only (e.g. "Processes Excel files" not "I can help you" or "You can use this").

### Authoring principles

*   **Concise is key**: Assume the agent is already capable. Only add context it doesn’t have. Challenge every paragraph for token cost.
*   **SKILL.md size**: Keep body under ~500 lines; move detail to linked files (progressive disclosure).
*   **Degrees of freedom**: Match specificity to fragility — high (text instructions) for flexible tasks, low (exact scripts) for fragile or critical operations.
*   **Consistency**: One term per concept (e.g. always "API endpoint" or always "field"); no time-sensitive cutoffs (use "Current method" vs "Old patterns" section instead).
*   **Options**: Prefer one default approach with a clear escape hatch; avoid "you can use A or B or C or...".

### Quick checklist before sharing

*   [ ] Description is specific and includes both WHAT and WHEN, in third person.
*   [ ] SKILL.md body under ~500 lines; extra detail in linked files.
*   [ ] Folder and `name` in kebab-case; no vague names.
*   [ ] File references one level deep; forward slashes only.
*   [ ] No time-sensitive wording; consistent terminology.
*   [ ] Examples concrete; workflows have clear steps.

---

## Annex C: Using AI to create a new SKILL.md

You don't have to write skills from scratch. Use the AI to generate and refine them.

*   **How**: Ask the agent to create a new skill (e.g. "I want to add a skill that does X" or "Help me create a SKILL.md for Y"). If available, use the **create-skill** skill (e.g. @create-skill or "follow the create-skill skill") so the agent follows a structured workflow.
*   **What to provide**: Purpose, when it should trigger, and any examples or constraints. The agent can then draft the folder structure, frontmatter, and body.
*   **Refine**: Review the draft against Annex B (or the create-skill checklist); ask the agent to tighten descriptions, add trigger phrases, or split content into reference files.
*   **In this repo**: The project skill **writing-skills** (`.cursor/skills/writing-skills/`) aligns with Annex B and repo conventions; the Cursor built-in **create-skill** gives the full creation workflow (discovery → design → implementation → verification).

---

## Annex D: Probing the agent's context (skill discoverability)

Skills and rules only help if the agent actually loads them. You can check what's in context without opening files yourself.

*   **Probe questions**: Ask the agent to answer *without reading any additional files*. For example "Without reading any additional file, can you tell me how you would do X?" or "Using only what you already have in context, how would you approach Y?"
*   **What you learn**: If it gives a detailed, correct answer, the right skill or rule is likely loaded. If it's vague or wrong, the description or trigger phrases may need to be improved so the skill gets selected for that kind of request.
*   **Use it to**: Test after adding a new skill, debug "the agent doesn't follow our process," or tune descriptions and rule wording for better discovery.

---

## Annex E: The Ralph Wiggum Technique (autonomous coding loops)

The Ralph Wiggum Technique, created by Geoff Huntley, is an approach to autonomous coding where you put an AI agent in a loop with a declarative specification and let it work independently.

*   *Reference*: [Ralph Wiggum as a "software engineer" (Geoff Huntley)](https://ghuntley.com/ralph/)
*   *Reference*: [A Brief History of Ralph (HumanLayer Blog)](https://www.humanlayer.dev/blog/brief-history-of-ralph)

### What is Ralph?

In its purest form, Ralph is a Bash loop:

```bash
while :; do cat PROMPT.md | claude-code ; done
```

The agent reads a declarative specification (`PROMPT.md`), executes changes, and repeats. Each iteration runs in a fresh context window, avoiding context rot.

### Core principles

*   **Declarative specification**: Describe the desired end state, not step-by-step instructions.
    Write `PROMPT.md` with clear acceptance criteria.
*   **Eventual consistency**: Ralph requires faith. It will make mistakes, but you tune the prompt
    (like adding signs to a playground) until the failures become predictable and rare.
*   **Deterministically bad in an undeterministic world**: Ralph's failure modes are predictable.
    When it does something wrong, you add constraints to the prompt and start a new loop.
*   **Fresh context windows**: Each loop iteration starts clean, preventing context rot and
    compacting issues that plague long interactive sessions.
*   **Autonomous execution**: Ralph can run overnight while you sleep, shipping code asynchronously.

### When to use Ralph

**Good use cases:**

*   **Greenfield projects**: Building something new from scratch with clear requirements.
*   **Refactoring to standards**: Create a `CODING_STANDARDS.md` and let Ralph apply it across the codebase.
*   **Spec generation**: Generate detailed specifications from high-level requirements.
*   **Applying patterns**: Repetitive tasks like adding tests, migrating APIs, or standardizing components.

**Poor use cases:**

*   **Exploration and discovery**: When you don't know what you want yet, use interactive Agent mode.
*   **Critical production systems**: Ralph is better for greenfield or non-critical refactors.
*   **When you need tight feedback loops**: If you're iterating rapidly, interactive mode is faster.

### How to use Ralph

1.  **Write `PROMPT.md`**: Describe the desired end state with clear acceptance criteria.
    Include standards, constraints, and examples.
2.  **Start the loop**: Run the bash loop or use a tool that supports autonomous execution.
3.  **Monitor**: Check periodically. Ralph may "overbake" (generate unexpected features like
    post-quantum cryptography support) if left too long.
4.  **Tune the prompt**: When Ralph makes mistakes, add specific guidance to `PROMPT.md`.
    Think of it as adding signs to a playground: "SLIDE DOWN, DON'T JUMP, LOOK AROUND."
5.  **Start fresh**: When the prompt gets too cluttered, start a new Ralph (new loop, clean prompt).

### Real-world examples

*   **CURSED programming language**: Ralph built an entire programming language (compiler, standard library)
    from scratch, in C, then Rust, then Zig, including a stage-2 compiler written in the language itself.
*   **6 repos overnight**: Y Combinator hackathon team put Ralph in a loop and it shipped 6 repositories
    overnight. ([We Put a Coding Agent in a While Loop](https://github.com/repomirrorhq/repomirror/blob/main/repomirror.md))
*   **$50k contract for $297**: One engineer used Ralph to deliver a $50k contract with only $297 in AI costs.

### Lessons learned from the field

*   **If specs are bad, results will be bad**: Garbage in, garbage out. Invest time in `PROMPT.md`.
*   **Know your desired end state**: If you can't define success, you won't recognize it when Ralph delivers.
*   **Code is cheap**: Easier to re-run Ralph on fresh code than to merge/rebase large PRs.
*   **Small iterations win**: Run Ralph once nightly with small, mergeable changes.
    Better to wake up to one small refactor every morning than 50 files changed at once.
*   **Human accountability still required**: Review everything. Maintain the same quality bar as
    human-written code. Ralph automates the typing, not the judgment.

### Comparison with interactive Agent mode

| Aspect | Interactive Agent (Ctrl+I) | Ralph Wiggum Loop |
|--------|---------------------------|-------------------|
| **Use case** | Exploration, iteration, debugging | Greenfield, refactoring, applying standards |
| **Context** | Single long conversation | Fresh context per iteration |
| **Feedback** | Immediate, synchronous | Asynchronous, periodic check-ins |
| **Control** | High (review each change) | Low (eventual consistency) |
| **Quality bar** | Same as human code | Same as human code (but tuned via prompt) |

### How Ralph relates to this training

Ralph embodies many of the principles we've covered:

*   **Declarative specifications** (Section 6: Task framing)
*   **Context hygiene** (Section 2: Context rot)
*   **Rules and constraints** (Section 3: Rules and Skills)
*   **Agent-first codebase structure** (Section 6: Takeaways)

The difference is that Ralph runs autonomously, not interactively. Think of it as the extreme
end of "agent-first mindset"—you write the requirements and walk away.

### Getting started

*   Read [Geoff Huntley's original post](https://ghuntley.com/ralph/) for the philosophy and examples.
*   Review [A Brief History of Ralph](https://www.humanlayer.dev/blog/brief-history-of-ralph) for
    real-world use cases and lessons learned.
*   Start small: try Ralph on a toy project or a well-defined refactoring task.
*   Tune your prompts: each failure is an opportunity to add a sign to the playground.
*   Join the conversation: Ralph is still evolving. Share what you learn.

---

## Annex F: Cursor CLI (Agent in Any IDE)

The Cursor CLI brings Cursor's agent capabilities to any IDE or editor, so you can use Cursor's reasoning without leaving your primary development environment.

*   *Reference*: [Cursor CLI Blog](https://cursor.com/blog/cli)

### What is Cursor CLI?

The Cursor CLI is a command-line interface that connects to Cursor's agent and lets you interact with it from any terminal. This means you can use Cursor in Rider, Visual Studio, Vim, Emacs, or any other editor.

### The "Copilot Killer" Workflow

This workflow combines the best of both worlds: your IDE's specialized tooling + Cursor's agent reasoning.

1.  **Open your primary IDE** (e.g., Rider, Visual Studio) for its superior debugger, refactoring tools, and language-specific features.
2.  **Open the integrated terminal** in that IDE (or a separate terminal in the same directory).
3.  **Run the Cursor CLI** to chat with the agent and modify files in place.
4.  **Review changes** in your IDE with full context, debugging, and refactoring support.

### Why this matters for Plastic SCM development

*   **Rider's C# tooling**: Rider has superior C# refactoring, debugging, and analysis compared to VSCode-based editors.
*   **Cursor's reasoning**: Cursor has better agentic capabilities than GitHub Copilot for complex tasks.
*   **Best of both**: Keep Rider open for debugging and refactoring, use Cursor CLI for agent-driven code generation.

### When to use Cursor CLI vs. Cursor IDE

| Aspect | Cursor IDE | Cursor CLI |
|--------|-----------|-----------|
| **Best for** | Primary coding, all-in-one experience | Using Cursor with other IDEs |
| **Tooling** | VSCode ecosystem | Your IDE's native tooling |
| **Agent access** | Built-in UI | Terminal-based |
| **Workflow** | Unified editor + agent | IDE for editing, CLI for agent |

### Installation and usage

*   **Install**: Follow instructions at [Cursor CLI](https://cursor.com/blog/cli).
*   **Basic usage**: Navigate to your repo in terminal, run `cursor-cli` or similar command.
*   **Typical workflow**: Ask the agent to make changes, review in your IDE, iterate.

### Limitations and considerations

*   **Terminal-only interface**: No GUI for agent interactions (yet).
*   **File watching**: Changes appear in your IDE, but you need to ensure file watchers are enabled.
*   **Context**: You still need to provide context (file paths, descriptions) in your prompts.

### Getting started

*   Read the [official Cursor CLI blog post](https://cursor.com/blog/cli) for installation and examples.
*   Try it in a small repo or side project first.
*   Experiment with keeping Rider open for debugging while using CLI for generation.
*   Share your workflow with the team if you find a good pattern.

