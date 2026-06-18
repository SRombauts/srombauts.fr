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

Three ready-to-paste rewrites (all under LinkedIn's ~220-char limit) — pick one:

- **Recruiter-optimized:**
  `Senior Software Engineer — Developer Tools, C++, Unreal Engine & Unity | Author of the official UE Git & Plastic SCM source-control plugins | now focused on AI-assisted software engineering`
- **Concise:**
  `Senior Software Engineer | C++ & developer tooling for Unreal Engine and Unity | AI-assisted software engineering`
- **Pivot-forward (if targeting AI-tooling roles):**
  `Senior Software Engineer | AI-assisted software engineering & coding agents | C++ developer tools, Unreal Engine & Unity, source control`

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

Paste-ready rewrite (role-neutral so it stays accurate after the Unity departure):

> Senior Software Engineer specializing in developer tools, build systems, and
> version control — across the Unity Editor (C#) and Unreal Engine (C++).
>
> 20+ years of engineering, from low-level embedded / FPGA systems to game-engine
> tooling. Core strengths: C++ and C#, CI/CD, version control (Git, Perforce,
> Plastic SCM / Unity Version Control), Python, CMake, and Linux.
>
> Most recently focused on AI-assisted software engineering: I author Claude Code
> skill files that teach coding agents a team's development workflow, architecture,
> coding standards, and code-review practices — and I've given internal talks to
> spread the practice across the team.
>
> Long-time open-source contributor (GitHub): author of the SQLiteCpp C++ wrapper
> and of the Git and Plastic SCM source-control plugins for Unreal Engine (the Git
> plugin shipped officially in UE4.7, earning a GDC 2016 invitation from Epic Games).

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
