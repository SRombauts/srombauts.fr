---
title: "Git Plugin v2.2 for Unreal Engine 4.17"
tags:
  - unreal-engine
  - vcs
  - github
---

[I have just released a new v2.2 of the Git Source Control Provider plugin for Unreal Engine 4.17 with many bugfixes](https://github.com/SRombauts/UEGitPlugin/releases/tag/2.2-beta) backported from upcoming UE versions!

I am often asked if I still work on it, so I figured that I would publish some news here.

## Many Pull Requests!

This is my 16th release of the Git Plugin, with 181 commits across 17 Unreal Engine version (since 4.0 in early 2014 🙂

I have never stopped working on the Git plugin for UE4. I have regularly submitted small or large Pull Requests to [the official Unreal Engine’s Github repository (private but free)](https://github.com/EpicGames/UnrealEngine).

To this day, [I have provided 49 PR to Epic Games, and around 44 have already been merged](https://github.com/EpicGames/UnrealEngine/pulls/SRombauts) 🙂. The bulk of them are bugfixes on the Git plugin itself, but I’ve also added many features.

## Release v2.2 for UE4.17

- Fix action icons in History log Window UI (“add”, “delete”, “branch”).
  Before this, every revision of any file history was an “edit” icon!
- Implement GetBranchSource() so that History now displays the previous name of a file that has been renamed
  Detects special case of move (“branch” in Perforce term) and point to the previous revision
- Fix “UpdateStatus” not picking renamed assets, nor removed/missing/untracked ones
  Git rename detection require to do “git status” command on the whole sub-directory (not on the explicit list for current asset files)
  Detection of deleted assets require to do an extra pass of parse in this “git status” results specifically for searching such asset files
- Fix global “UpdateStatus” operation not finding modified assets
- Run an “UpdateStatus” at “Connect” time to populate the Source Control cache
  This fix a bug when right clicking on a directory of the Content Browser :
  the UI does not know the state of all contained assets and as such present the “Add” entry, but clicking on it can lead to a “no asset to add” message
- Revert Cleanup RunDumpToFile(): WaitForProc() hang indefinitely!
- Expand the size of the Button “Initialize project with Git”
  To help remind the user that Git Source Control is not possible without a Git repository initialized.
- Fix #45 Add logs to help identify problem with git.exe and git lfs
- Ignore “.vs” folder of Visual Studio 2017

## Future

Since Git LFS 2.0 was release earlier this year, I’ve been working on integrating it into the Unreal Engine plugin.

The problem is that it requires quite some intensive rework because it does change the whole workflow and hypothesis on how Git works (DVCS local vs centralized LFS).

So it will come at some point in time, but it will require more work on some smaller features, like support for “remote origin” and associated “git push”.

## Support my work

If you want to support my work, [small tips are welcome](https://www.paypal.me/SRombauts) 🙂
