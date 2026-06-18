# Plan: Consolidate Sébastien Rombauts' online network + scaffold AI-expertise surfacing

## Context

The personal blog now lives at <https://srombauts.eu/> (Jekyll + GitHub Pages, repo
still named `srombauts.fr`). It reads as a 2010s C++/gamedev blog: the last published
post is **2023-02-20**, the framing is "Senior C++ developer", and the author's actual
recent focus (AI coding agents, Rules/Skills/Commands, MCP) is invisible to the public.

A separate review of the wider presence found a **loosely connected, partly stale
network**:

- **Domain split.** `srombauts.github.io` still links to the old `http://srombauts.fr`;
  the GitHub profile's website field points to `https://srombauts.eu`. Two blog domains
  in play.
- **No profile hub.** `github.com/SRombauts/SRombauts` returns 404 — there is no profile
  README, the single highest-leverage landing surface on GitHub.
- **LinkedIn is a dead end both ways.** It appears only in site chrome (sidebar/footer/
  SEO), is never linked from any post or page, and links back to nothing.
- **Twitter/X is over-represented** relative to how the author now thinks about the
  network (the brief listed github.io, GitHub, LinkedIn — not X).
- **No public AI artifacts exist.** The recently-updated GitHub repos are gamedev/C++/
  recipes/woodworking; the rich AI work lives in **internal** repos
  (`unity-version-control-skills`, `muse-skills` on `github.cds.internal.unity3d.com`)
  and internal training docs. None of that can be linked publicly.

**Decisions taken (from the author):**
1. **Scaffold only** this pass — do the network/cross-link/About/portfolio/config work
   now; the actual AI blog posts are a **separate follow-up** (the 3-post series already
   specified in `extract-from-...-smooth-allen.md`).
2. **Edit sibling repos that are checked out locally.** `srombauts.github.io` is at
   `C:\UnitySrc\srombauts.github.io` -> edit directly. The profile-README repo does not
   exist -> deliver a ready-to-publish draft + creation steps.
3. **De-emphasize X, push LinkedIn** — keep X but make GitHub + LinkedIn primary
   everywhere, and surface LinkedIn from content, not just chrome.

**Intended outcome:** every public surface (blog, github.io, GitHub profile) tells the
same current story (developer tools + C++/UE/Unity + source control + **AI-assisted
software engineering**), cross-links cleanly on the **`.eu`** domain, foregrounds GitHub
and LinkedIn, and is primed so the forthcoming AI series drops into a coherent structure.

**Hard guardrail — nothing confidential leaks.** Do NOT reference, link, or paraphrase:
internal hosts (`*.unity3d.com`, `github.cds.internal.unity3d.com`), the internal skills
repos, Confluence/Jira/Zoom/Slack, `@unity3d.com` accounts, `codice@cloud` / `plastic://`
identifiers, ticket keys, internal source paths, or colleague names. The only safe,
public AI artifact to point at is **this blog repo's own `AGENTS.md` + `.claude/`** setup.

---

## Part A — srombauts.fr (this repo)

### A1. `_config.yml` — refresh identity + reorder socials

- `url`: `http://srombauts.eu` -> `https://srombauts.eu` (GitHub Pages serves https;
  fixes canonical/SEO). Leave `CNAME` untouched per AGENTS.md.
- `author.bio` (line 49): rewrite from
  *"Senior software engineer at Unity. Author of the Git & Plastic SCM source control
  plugins in UnrealEngine #gamedev"* to a current line that adds developer-tools +
  **AI-assisted software engineering**, keeping the author's `;)` voice. Keep it short
  (sidebar card).
- `description` (line 27) / `subtitle` (line 24): light refresh so the masthead/SEO
  blurb mentions tools + AI, not just "Game/Tools dev".
- **De-emphasize X across all four link blocks** — `author.links` (51-60),
  `footer.links` (88-97), `social.links` (74-77), and the `og`/`twitter`/`facebook`
  SEO keys: reorder so **GitHub first, LinkedIn second, Twitter last**. Do not delete X.
  Normalize the LinkedIn URL to lowercase `https://www.linkedin.com/in/srombauts/`
  (matches the live vanity URL; currently `.../SRombauts`).

### A2. `_pages/about.markdown` — strengthen AI framing + add a "find me" block

- The AI framing is already seeded (lines 11/13); tighten it and make AI-assisted
  engineering a first-class part of the self-description rather than a trailing clause.
- Add a short **"Find me elsewhere"** reference-style link block at the bottom: GitHub
  (primary), LinkedIn (primary), the github.io project index, X (last). This is the
  content-level LinkedIn surfacing that's currently missing everywhere.
- Add one honest forward-reference: a line noting a series on customizing AI coding
  agents is coming, linking to `/tags/` (or the portfolio AI section from A3) so the
  link target exists today and auto-populates when the posts land.
- Run the result through the **`humanizer`** skill (mandatory for prose per AGENTS.md;
  no em/en dashes).

### A3. `_pages/portfolio.markdown` — turn the first TODO into a real section

- Replace the first TODO bullet ("Add references to my experiments with AI Coding
  Agents...") with a real **"AI-assisted software engineering"** section. Keep it honest
  and non-confidential:
  - Describe the practice (repository instructions / Rules / Skills / Commands / MCP,
    treating the agent like a junior dev you onboard and review).
  - Point at the **one genuinely public artifact**: this very site's
    [`AGENTS.md`](https://github.com/SRombauts/srombauts.fr/blob/master/AGENTS.md) and
    its `.claude/` skills (e.g. the vendored MIT `humanizer`) as a live example of an
    AI-customized repo.
  - Forward-link to the forthcoming series via `/tags/` (or a stable anchor) so it wires
    up automatically once the posts publish. No links to internal repos.
- Leave the remaining TODOs (ECS, SDL, OpenGL/gltext, Ogre3D, ZMQCpp) as-is.
- Humanize the new prose.

### A4. Link hygiene in existing posts (small, high-value fixes)

- `_posts/2018-04-04-I-joined-darewise-entertainment.markdown` and
  `_posts/2022-02-22-I-joined-unity.markdown`: the `[UEPlasticPlugin]` ref uses a
  slug-only path (`/2016-04-25-...`) that does not resolve under the site's
  `permalink: pretty` (dated) scheme. Fix to the dated form
  `/2016/04/25/unreal-engine-4-11-plastic-scm-source-control-provider/`.
- `_posts/2012-04-12-why-i-switched-from-mercurial-to-git.markdown`: the
  `[SQLiteCpp]: /2012/04/04/SQLiteCpp-0.1.0/` ref has no matching post (dead link).
  Repoint to the SQLiteCpp project page (`http://srombauts.github.io/SQLiteCpp`) or drop
  the ref. Verify with a local link check, not by assumption.

---

## Part B — srombauts.github.io (local at `C:\UnitySrc\srombauts.github.io`)

Single file: `README.md` (rendered by the `jekyll-theme-slate` GitHub Pages theme).

- **Fix the domain:** blog link `http://srombauts.fr` -> `https://srombauts.eu`.
- **Reframe the bio:** "Senior C++ developer" -> current framing matching the blog
  (Senior Software Engineer; developer tools, C++, Unreal Engine & Unity, source-control
  integrations, AI-assisted software engineering).
- **Push LinkedIn, de-emphasize X:** add a LinkedIn link next to the GitHub link; move
  the Twitter mention to last (keep, don't delete).
- Keep the repository list; optionally align descriptions with the blog's portfolio page.
- This is a separate repo: **commit/push only on explicit request** (it deploys live too).

---

## Part C — GitHub profile README hub (new; repo does not exist yet)

`github.com/SRombauts/SRombauts` is 404. A profile README is the biggest single network
win. Since the repo isn't local, deliver it as a ready-to-publish draft:

- Create `C:\UnitySrc\SRombauts-profile\README.md` (scratch folder, not committed
  anywhere yet) containing a concise profile hub:
  - One-line current bio (tools + C++/UE/Unity + source control + AI-assisted
    engineering), author voice.
  - **Links:** blog `https://srombauts.eu` (primary), LinkedIn (primary), github.io
    project index; X last.
  - A short "Selected projects" list mirroring the pinned repos (SQLiteCpp, UEGitPlugin,
    UEPlasticPlugin, SimplexNoise, shared_ptr) with one-line each.
  - A line on the AI-assisted-engineering focus, forward-linking to the blog (no internal
    repos).
- Include, in the plan output and as a comment block, the **publish steps**: create a
  public repo named exactly `SRombauts`, add `README.md`, push to `master`/`main`. (Repo
  creation + push is the author's to run; offer the `gh repo create` command.)
- Humanize the prose.

---

## Deferred to the follow-up (explicitly NOT done in this pass)

- Writing the **3 AI posts** (`2026-01-29`, `2026-02-12`, `2026-03-25`) per
  `extract-from-...-smooth-allen.md`.
- Introducing the `ai`, `cursor`, `claude-code` **tags** (they do nothing without posts;
  add them with the posts).
- Wiring About/portfolio forward-links to the concrete post permalinks (today they point
  at `/tags/` so they are valid immediately and self-populate later).

---

## Critical files

| File | Change |
|------|--------|
| `C:\UnitySrc\srombauts.fr\_config.yml` | https url; refreshed bio/description; reorder socials (GitHub+LinkedIn primary, X last); lowercase LinkedIn URL |
| `C:\UnitySrc\srombauts.fr\_pages\about.markdown` | strengthen AI framing; add "find me elsewhere" links (LinkedIn surfaced in content); forward-ref to series |
| `C:\UnitySrc\srombauts.fr\_pages\portfolio.markdown` | replace AI TODO with real AI-assisted-engineering section pointing at public `AGENTS.md`/`.claude` |
| `C:\UnitySrc\srombauts.fr\_posts\2018-04-04-...markdown` | fix slug-only permalink |
| `C:\UnitySrc\srombauts.fr\_posts\2022-02-22-I-joined-unity.markdown` | fix slug-only permalink |
| `C:\UnitySrc\srombauts.fr\_posts\2012-04-12-...git.markdown` | fix/replace dead SQLiteCpp ref |
| `C:\UnitySrc\srombauts.github.io\README.md` | .eu domain; reframed bio; add LinkedIn; de-emphasize X |
| `C:\UnitySrc\SRombauts-profile\README.md` (new) | drafted profile-README hub + publish steps |

Reuse the existing reference-style-link convention and minimal frontmatter already used
across `_posts`/`_pages`. Run the **`humanizer`** skill on every prose edit; keep
2-space/LF/UTF-8/final-newline per `.editorconfig`.

---

## Verification

1. Ask the user to check
7. **No commits/pushes** to either repo until the author explicitly approves (both deploy
   live on push to `master`).
