# Brag document 2024–2025 — Unity VCS Tech team

> Markdown transcription of `Sebastien's brag document 2024-2025`, covering the
> second half of my Unity tenure on the VCS Tech ("Plastic") team. Internal Unity
> links have been redacted. The public, sanitized summary lives in `_pages/cv-en.markdown` and
> `_pages/cv-fr.markdown`.

## Goals for this year

- Contribute to the Unity Plugin roadmap, prioritize the most important CSAT
  improvements. Help uncover issues, points of friction and frustration. Gather and
  bring feedback to the team.
- Modernize the Unity Plugin dev environment, from the CI and integration with Unity
  tooling to the .NET Framework version used in HAL, etc.
- Keep the Unreal Plugin up to date with new Engine releases, moving from the Unreal
  Marketplace to Fab.com.
- Unity Editor VersionControl integration, and a new Perforce Package.

## Goals for next year

- **CSAT related:** find, study and fix the most complex issues remaining on the Unity
  Plugin — random bugs, hard-to-reproduce but painful crashes, performance issues and
  complex integration with the Unity Editor.
  - Reported via CSAT and customer support tickets; will help users adopt and trust the
    plugin.
  - Success measured through the number of tickets closed and the number of remaining
    complaints.
- **Feature:** work on one important feature on the Desktop Application with another team
  member. Thinking of improvements to the Branch Explorer (displaying shelves in the
  graph?).
  - Impact on CSAT.
  - Measure usage through analytics.
- **Unity & Unreal Plugin releases:** continue the effort to maintain the plugins up to
  date with the bi-annual Engine releases, updating them in a timely manner (weeks, not
  months) and answering customer requests ASAP as always.
- **Team growth:** promote improving our culture of QA, vs. relying overly on code
  reviews and unit tests only.

## Projects

### Ignore / Hidden Changes

- Files getting checked out even though they are in `hidden_changes.conf`.
- New unit tests covering the `WorkspaceMonitor`, and the `FileFilters` for the
  `ignore.conf` as well.

### PRD — UVCS Tier 1 Plugins

### Code Coverage

- Code coverage for all the releases we had in nearly two years, starting from Unity
  Plugin 0.43.0 / 1.17.7 (build on 2022/10/28, just before the 2.0.0 collab removal).
- Updated our "Unity Plugin Releases" page in Confluence so we will think of updating it
  on every release going forward.
- Checked in the checkpoints in the repo so we keep track of this.
- Coverage dashboard: _[internal link redacted]_
- New documentation page: _[internal link redacted]_

### Unity Plugin

- Release planning and execution, coordinating team validation:
  - Release 2.5.1 and 2.5.2.
  - Release 2.6.0 (after the epic ride for 3.0.1).
  - Release 2.7.1 just in time for U6.1 @ GDC 2025 (with last-minute regressions).
  - Release 2.8.1.
  - Didn't participate in 2.9.1 nor 2.9.2 (August), but released 2.9.3.
  - Release 2.10.0 and 2.10.1 for U6.3 @ Unite 2025 (with many last-minute fixes).
- Unity CI & processes:
  - APV2 compliance (public API checks).
  - Packageworks process (Wrench tooling and Renovate GitHub setup).
- Validation effort: thorough validation of all tasks related to
  - Merging branches.
  - Shelve & Switch.
  - Shelve view.
- Create new Code Review from the plugin:
  - Initiative proposed for Q4 as a way to better leverage branches from the plugin.
  - Lots of work, with some review from Violeta before the Christmas break.
  - Lots of back and forth with Miryam and Mathias to improve on it after the break.
  - Involved a ton of work with Alvaro along the way, including testing and iterating on
    the new generic dialog with checkbox, and the regression they introduced on macOS.
- Investigation of performance regression:
  - Investigation of alleged performance regressions introduced by 2.6.0: it turned out
    the Unity Editor behaves strangely on exit play, oscillating between two performance
    profiles seemingly randomly. Closed as Won't Fix (not our responsibility).
- Migration to @unity organizations:
  - Involved a lot in testing the migration of @cloud organizations to @unity orgs.

### Unity Editor

- ~100 Unity Editor PRs (plus some more on Neutron). Internal PR list: _[internal link
  redacted]_
  - 2.7.1
  - 2.8.1
  - 2.8.2
  - Reducing testing overhead for VersionControl and YamlMerge automated tests.
  - Perforce Cloud support.
  - 2.9.x

### Unreal Plugin

- **UE5.5:**
  - Fixed compilation with the upcoming Unreal Engine 5.5, so the plugin is compatible.
  - Fixed extreme performance issues with how Unreal processed list-lock output.
  - Fixed `cm checkconnection` having authentication issues when used with multiple
    accounts (+ fix `cm`).
  - Create Workspace wizard now supports @unity Unified Organizations and Projects:
    - Major UX improvements, using a drop-down menu instead of a free-form edit text box.
  - Release 1.12.0 before closing 2024.
- **Fab.com replaced the Unreal Engine Marketplace:**
  - New process, updated landing pages, logo, etc.
  - <https://www.fab.com/listings/42f9c431-d7a7-4e09-af55-fb4b896e9c97>
- **UE5.6:**
  - Got the PR for 1.11.0 merged (our previous release, with the "Changesets" view).
  - Fixed a conflicting Localization label for Epic Games.
  - Released 1.12.1 in the week following the 5.6 release.

### CLI

- Added support for @unity Unified Organizations to the `--server` parameter.
- Added a new argument `<repserverspec>` to `cm checkconnection`, and added the first
  multiserver smoke test for `checkconnection`.
- Added support for @unity orgs.

### Perforce Plugin

- Infrastructure update: P4 AP, Yamato CI & Bokken images, building with a version number.
  - Perforce Cloud support.
  - Windows 10 long names.
- macOS ARM64 "Apple Silicon".

### Perforce Package study

- TL;DR: overly complicated architecture, adding layers around the native
  `PerforcePlugin.exe` instead of simplifying the VersionControl integration.

## Collaboration & mentorship

- Code Coverage for the Unity Plugin: showed the team how to record code coverage while
  running the unit tests. Documented internally. _[internal link redacted]_

## Design & documentation

- Unity VCS Package Roadmap revamp.
- HackWeek 2024 — dogfooding Unity Version Control.

## In progress

- unity-plugin release process improvements.

## Company building

## What you learned

- Localization pipeline for Unreal Engine.
- Refining the AI agents' custom instructions (context engineering) for use with Cursor
  and GitHub Copilot.

## Outside of work

- Astrophotography, using advanced processing algorithms (and a few small pull requests
  to improve or fix the Siril open-source software).
- Baking my own bread.
