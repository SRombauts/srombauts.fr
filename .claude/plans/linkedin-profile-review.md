# Plan: LinkedIn profile review

## Context

This is part of the 2026 job search (the blog and the wider online presence now
double as verifiable career evidence; see the sibling plan
`consolide-srombauts-online-presence.md`, which already covers the `_config.yml`
bio, the About/portfolio AI framing, LinkedIn-URL normalization, and de-emphasizing
X across the site chrome). **This plan is narrower: it is about the LinkedIn profile
itself** (`https://www.linkedin.com/in/srombauts/`, redirects to `fr.linkedin.com`).

Most of the work here is **manual edits on LinkedIn** — LinkedIn is not a repo and
cannot be edited from here. The only repo-side items are two public-facing typos on
the portfolio page that a recruiter hits immediately after clicking through from
LinkedIn.

### Review history

- **First pass (logged-out "first look"):** only name/URL, headline, location,
  company, education, languages and activity were visible. The *About*,
  *Experience*, *Skills*, *Featured* and *Contact info* were behind login and
  deferred.
- **Second pass (2026-06-22, full PDF export `LinkedInProfile.pdf`):** the deferred
  sections are now reviewed — see **Part A7** (Experience cleanup) and **A4 /
  Part B2** below. The PDF also corrected a first-pass assumption: the *headline*
  is already `Senior Software Engineer, Tools` (good — already "Engineer"); the
  "Programmer" wording is in the **Summary's first sentence**, not the headline.

### What the visible headline says

> Headline (PDF): `Senior Software Engineer, Tools`
> Summary opens: "Senior Software **Programmer** working with the Unity Editor and
> Unreal Engine.Strong…" (note also the missing space after "Engine.")

---

## Part A — On LinkedIn (manual edits, ordered by importance)

### A1. Strengthen the headline (highest leverage — ~80% of the first look)

PDF correction: the headline already reads `Senior Software Engineer, Tools` — so
the Engineer-vs-Programmer problem is **not** in the headline (it's in the Summary,
see A4). The remaining opportunity:

1. **It's thin.** "Senior Software Engineer, Tools" wastes most of the ~220-char
   limit and front-loads no searchable differentiators.
2. **Add durable, provable keywords** the repos already back: C++, developer
   tooling, **author of the official Unreal Engine Git & Plastic SCM source-control
   plugins**, and the current pivot to **AI-assisted software engineering** (which
   the blog and portfolio now lead with, but the headline ignores). Avoid tying the
   identity to Unity specifically, per `leaving-unity-job`.

Decision (2026-06-29): the headline should make **AI engineering visible alongside
the tools and engine expertise**. This is intentionally a different balance from the
About (A4), which stays tech-led with AI as a single trimmable closing line — the
headline is where AI shows as an always-visible keyword. No em dashes (use `|`).
Three ready-to-paste options, all under LinkedIn's 220-char limit:

- **Recommended (tools + engines + version control + AI):**
  `Senior Software Engineer | Developer Tools & Version Control for Unreal Engine & Unity (C++/C#) | AI Engineering: skills for AI coding agents`
- **Concise:**
  `Senior Software Engineer | C++ Developer Tools for Unreal Engine & Unity | AI engineering & skills for AI coding agents`
- **Closest to the author's wording (SKILL branding):**
  `Senior Software Engineer | Developer Tools, C++, Unreal Engine & Unity | AI Engineering (SKILLs for AI Coding Agents)`

Precision note: bare "AI Engineering" can read as ML / model-building; pairing it
with "skills for AI coding agents" keeps it honest about what the work actually is.
For a Defense or no-AI target, the third `|` segment is easy to drop.

### A2. Fill the Featured section with verifiable evidence

The strongest job-search asset is that the claims are *provable*. Add to **Featured**
(and the **Contact info → website** field):

- the GitHub Pages project index `https://srombauts.github.io/` (quick repo tour),
- the blog `https://srombauts.eu/`,
- the UE Git Plugin page, and `SQLiteC++` (most-starred lib).

Featured is prime first-look real estate and is usually left empty. This is also the
public counterpart to the GitHub profile-README hub drafted in the sibling plan.

### A3. Use the personal gmail in Contact info, not the work email

Since Unity is being left, make sure the contact email on the profile is the gmail
address, not `@unity3d.com` (same rule the site follows — see `publish-only-gmail-email`).

### A4. Rewrite the About / Summary (now reviewed from the PDF)

Current Summary problems:
- Opens "Senior Software **Programmer**…" — should be **Engineer** (matches the
  headline, the Darewise/Unity titles, and the blog bio; better recruiter keyword).
- One dense run-on with a mid-thought `...`, plus a missing space (`Engine.Strong`).
- Only the first ~2 lines show before "see more", so they must carry who-you-are +
  what-you-shipped.

Paste-ready rewrite (updated 2026-06-29, humanizer-checked). Role-neutral so it
stays accurate after the Unity departure. Per the author's request this pass is
**more AI-forward than the previous one**: the opening sentence names "skills for
AI coding agents" so an AI keyword shows before LinkedIn's "see more" fold (aligned
with the Recommended headline in A1), and a detailed **three-stage AI section** sits
at the end (the practice, then sharing it, then public proof), mirroring the
structure and cadence of the "AI-assisted software engineering" section in
`_pages/portfolio.markdown`. Per a further author request (2026-06-29), the About
now **opens with the human qualities** (passion, team player, kindness, a positive
attitude) before the technical identity: the Recommended headline already carries
the searchable keywords, so the About's first lines are free to lead with who the
author is, and the team-player claim is backed later by the coaching / talks
evidence. To avoid the standard LinkedIn-buzzword feel, each trait is anchored to a
specific (generous with what I learn; team success over personal credit). The whole
AI material can still be trimmed for a Defense or no-AI target. The Epic Games GDC
2016 **invitation is confirmed** (2016-03-02 blog post "Joining Unreal Engine 4 team
for GDC 2016") and is stated plainly:

> Above all, I am a passionate engineer who loves building software with a team. I
> am kind, positive, and generous with what I learn, and I care more about the team
> succeeding than about personal credit.
>
> Senior Software Engineer specializing in developer tools, version control, and
> skills for AI coding agents, across Unreal Engine (C++) and the Unity Editor (C#).
>
> Over 20 years of engineering, from real-time embedded and FPGA systems to
> game-engine tooling. I work mainly in C++ and C#, with strong experience in
> version control (Git, Perforce, Plastic SCM / Unity Version Control), build
> systems, CI/CD, CMake, Python, and Linux.
>
> Long-time open-source contributor on GitHub. I wrote the Git and Plastic SCM
> (Unity Version Control) source-control plugins for Unreal Engine, and the
> SQLiteC++ wrapper. After my Git plugin was integrated officially into Unreal
> Engine 4.7, Epic Games invited me to join the Unreal Engine team at GDC 2016 in
> San Francisco.
>
> On the AI side, I have spent the past year working daily with Cursor and then
> Claude Code. I treat the coding agent like a new hire I onboard and review, and I
> shape what it sees: repository instructions (AGENTS.md / CLAUDE.md), reusable
> skills, slash commands, and MCP servers.
>
> I have also worked to spread this across the team, coaching colleagues and giving
> talks and live demos so the team works from one shared toolkit.
>
> The public proof is in my own repositories: this blog, my SQLiteC++ library, and
> an in-progress C++/SDL3 Pong each carry their own Claude Code skills for their
> builds, tests, and releases. A longer write-up series is on the way.

### A7. Clean up the Experience section (from the PDF)

The public site's `_pages/cv-en.markdown` is already cleaner and more complete than
LinkedIn — use it as the source of truth and bring LinkedIn up to it.

1. **Untranslated French bullets under English entries — biggest issue.** Five roles
   show the English description *followed by* the original French text (reads as
   duplicated/messy to an English-reading recruiter): **Freelance** (entirely FR),
   **ENGIE INEO Systrans** (R&D — EN then FR repeat), **Eurilogic**, **Renault**,
   **Dassault**. One language per entry; clean English for all of these already
   exists in `cv-en.markdown` (lines 82–160) — adapt from there.
2. **Typos:** `implemention` → implementation (Hobby); `The Great Espace` → **The
   Great Escape** (CodinGame; site already correct); `System On Ship` → **System On
   Chip** (page 6); `Intégration of C++ online services` → **Integration** (stray
   accent, Unity entry); standardize `SKILLs`/`SKILL files`/`SKILL.md` → "Claude
   Code skill files".
3. **Unity end date:** currently `February 2022 - Present (4 years 5 months)`. Set
   the end month once departure is appropriate to show publicly, so the timeline
   stays accurate and Unity doesn't read as permanent (`leaving-unity-job`).
4. **Renault / Eurilogic overlap** (Renault May 2005–May 2006 sits inside Eurilogic
   Aug 2003–May 2006) looks like conflicting dates to a non-French reader. Add a
   clause like "(client mission via Eurilogic)".

### A8. Split the Unity experience into two stacked roles (mirror the site)

`cv-en.markdown` / `cv-fr.markdown` now present Unity as **two** roles organized by
plugin phase, not one umbrella entry. The split is by plugin focus, which is the
stronger story and is intentionally *not* perfectly aligned with the internal team
reorgs (backend and desktop are framed as side work in each phase):

1. *Senior Software Engineer, Unreal Engine plugin* (Integration / Ecosystem team),
   **Feb 2022 – Dec 2024** — hired to modernize and migrate the Unreal plugin to
   UE5 (C++); plasticscm.com backend and other ecosystem plugins as "full stack"
   side work. Concluded with Unreal plugin **1.12.0** on **2024-12-04**.
2. *Senior Software Engineer, Unity Editor package* (VCS Tech team),
   **Jun 2023 – present** — Unity Editor package (C#): first contribution was release
   **2.0.5** (2023-06-01), later owned release planning from **2.5.0** through
   **2.12.x**; CI and release pipeline aligned with Unity Release Management tooling
   and stricter package-validation rules, ~100 Editor PRs, Perforce, the
   AI-assisted-engineering effort; Unreal plugin in maintenance; occasional
   desktop/Gluon work.

The two roles **overlap** (Jun 2023 – Dec 2024): the author was contributing to the
Unity package while still finishing the Unreal one. Overlapping positions under one
company are fine on LinkedIn and reflect the real transition.

On LinkedIn, split the single Unity entry into these two stacked positions under the
Unity company (same mechanism as the Darewise two-role history in B2.1). This also
removes the vague "More recently focused on..." phrasing the earlier pass flagged.
Decision (2026-06-29): on LinkedIn the author is fine publishing internal team and
product names (Plastic, Integration / Ecosystem, VCS Tech, Gluon); only **other
people's names** (e.g. the manager) are excluded. The public site CVs stay more
sanitized; see `blog-employer-framing` for keeping employer references neutral.

**Split mechanics:** edit the existing single role to become Position 2, then add a
new position under the same Unity company for Position 1; LinkedIn stacks them under
one "Unity" header. Dates are now from the author (2026-06-29): Position 1 ran
Feb 2022 – Dec 2024 (Unreal plugin 1.12.0 on 2024-12-04); Position 2 runs
Jun 2023 – present (first contribution release 2.0.5 on 2023-06-01). The overlap is
intentional and accurate. (Version note: the author first wrote the Dec-2024 Unreal
release as "2.12.0"; the brag doc records it as 1.12.0, and 2.12.0 is a Unity package
number — confirm if 1.12.0 is wrong.)

#### Ready-to-paste — Position 1

> **Title:** Senior Software Engineer, Unreal Engine plugin
> **Company:** Unity · **Location:** Paris · **Dates:** Feb 2022 – Dec 2024

```
Hired into the Plastic SCM Integration / Ecosystem team as the owner and original developer of the Unity Version Control (formerly Plastic SCM) plugin for Unreal Engine. My main focus was to modernize the plugin and migrate it to Unreal Engine 5 (C++).

- Owned the Unreal plugin end to end: feature development, customer support, and releases, bringing it in line with the modern Unreal Engine 5 source-control APIs.
- Kept the plugin up to date with each engine release, through to version 1.12.0 in December 2024.

On the side, I worked across the wider ecosystem as a "full stack" developer:
- Contributed to the plasticscm.com C# backend and ASP.NET frontend on Azure Cloud.
- Helped with other ecosystem plugins.

The Unreal plugin stayed my primary focus throughout this period. By mid-2023 I had also begun contributing to the Unity Version Control package for the Unity Editor, which became my main focus afterwards.
```

#### Ready-to-paste — Position 2

> **Title:** Senior Software Engineer, Unity Editor package
> **Company:** Unity · **Location:** Paris · **Dates:** Jun 2023 – Present

```
I started contributing to the Unity Version Control package for the Unity Editor (C#) in mid-2023 (my first contribution shipped in release 2.0.5 on 2023-06-01), while still finishing the Unreal plugin. As my team merged into the VCS Tech team and broadened to also own the Unity Editor package and the desktop applications, this became my main focus and the Unreal plugin moved into maintenance.

Unity Version Control package (Unity Editor, C#):
- Owned release planning and execution across many versions, from 2.5.0 through 2.12.x, coordinating team validation and aligning releases with Unity Editor milestones, including Unity 6.1 at GDC 2025 and Unity 6.3 at Unite 2025.
- Designed and built a "create a code review from the plugin" feature, including a reusable confirmation dialog and the related macOS UI work.
- Validated the branch-merge, shelve-and-switch, and shelve-view workflows, and investigated hard-to-reproduce performance and crash reports raised through customer support.
- Modernized the package CI and release pipeline to keep up with the Unity Release Management tooling and stricter package-validation rules: public-API compatibility checks, automated dependency updates, and a documented code-coverage workflow.

Unity Editor (C#):
- Around 100 merged pull requests, plus contributions to related internal repositories.
- Added Perforce Cloud support and reduced the overhead of the version-control and YAML-merge automated test suites.

Maintenance and cross-cutting work:
- Kept the Unreal plugin current with Unreal Engine 5.5 and 5.6, and moved its distribution from the Unreal Marketplace to Fab.
- Maintained the Perforce plugin and the Editor's version-control integration (Perforce Cloud, macOS ARM64, Windows long paths).
- Contributed occasionally to the Unity Version Control desktop and Gluon applications.

AI-assisted software engineering:
- Spent nearly a year using Cursor (AI IDE) intensively, then Claude Code, including an experimental Perforce package in C# with the UI Toolkit.
- Spearheaded the team's AI effort: authored the vast majority of our SKILL files (AI agent instructions), and gave internal Unity Talks on writing Claude Code SKILL.md files.
```

### A5. Photo + banner consistency

Match the LinkedIn photo to the blog avatar (`/assets/images/seb.jpeg`) for cross-
platform recognition. Add a simple background banner if empty (an empty banner reads
as a dormant profile).

### A6. Post, don't just engage (job-search specific)

Profile shows likes but no original posts. The AI-assisted-engineering blog series
(the 3 posts specified in `extract-from-cursor-training-an-ai-blog-series.md`) is the
freshest, most differentiating material — cross-post each as a LinkedIn post/article
when it publishes, to show an active, current profile rather than only Unity/Unreal
history.

---

## Part B — In this repo (editable now)

### B1. Fix two typos on the portfolio page

A recruiter clicking from LinkedIn lands on the portfolio first. Two real typos:

- `_pages/portfolio.markdown:29` — "a smart **an** easy to use C++ wrapper" →
  "a smart **and** easy to use".
- `_pages/portfolio.markdown:24` — "***Clic** the image*" → "*Click the image*".

Trivial one-line edits. Honor `.editorconfig` (2-space, LF, UTF-8, final newline).
Not prose-heavy, but if any surrounding sentence is reworded, run the `humanizer`
skill per `AGENTS.md`.

| File | Change |
|------|--------|
| `C:\UnitySrc\srombauts.fr\_pages\portfolio.markdown` | line 29 "an" → "and"; line 24 "Clic" → "Click" |

> Note: the Engineer-vs-Programmer fix is a **LinkedIn-side** action (A4 Summary).
> The blog bio already says "engineer"; the `_config.yml` bio refresh is handled in
> `consolide-srombauts-online-presence.md`, not here, to avoid duplication.

### B2. Reconcile LinkedIn ↔ site discrepancies (decide one canonical answer each)

The PDF surfaced real disagreements between LinkedIn and `cv-en.markdown`:

1. **Darewise Lead promotion.** LinkedIn shows two roles — *Senior Software
   Engineer* (Apr 2018–Feb 2020) then **Lead Tech and Tools Programmer**
   (Feb 2020–Feb 2022). The site collapses this to a single "Senior Software
   Engineer, Tools & Tech", hiding the promotion to **Lead**. Recommendation:
   surface the Lead title on the site too.
2. **Game name & stage.** LinkedIn names the MMO **"Life Beyond"** / "closed alpha";
   the site says **"Project-C"** / "closed pre-alpha". If "Project-C" was a
   deliberate anonymization, fine — but pick one and keep the alpha wording honest.
3. **Open-source dates.** LinkedIn Hobby says "2009 - Present (17 yrs)"; site scopes
   OSS to "2009 to March 2018". OSS is ongoing → "present" is the accurate framing.

---

## Verification

1. **A1 headline:** after editing on LinkedIn, view the profile logged-out (or in a
   private window) and confirm the new headline is not truncated mid-word and leads
   with "Senior Software Engineer".
2. **A2 Featured / A3 email:** confirm the website field and Featured links resolve,
   and that the contact email is the gmail address.
3. **B1 typos:** `bundle exec jekyll serve` from `C:\UnitySrc\srombauts.fr`, open
   `/portfolio/`, confirm "smart and easy" and "Click the image" render and the page
   still builds cleanly. Do **not** commit/push without explicit approval (push to
   `master` deploys live).
4. **Deeper review (deferred):** paste the full *About* + *Experience* + *Skills*
   text (or a profile PDF export) to review bullets, dates, and remaining typos.

---

## Guardrail / side note

`.claude/plans/` is **not** in `.gitignore` and is currently untracked. The existing
plan files reference internal Unity material that must never be pushed to the public
`SRombauts/srombauts.fr` repo. Recommend adding `.claude/plans/` (or all of
`.claude/`, except the tracked `.claude/skills/`) to `.gitignore`, or simply never
`git add`-ing the plans directory. This LinkedIn plan contains no confidential
material, but the sibling plans do.
