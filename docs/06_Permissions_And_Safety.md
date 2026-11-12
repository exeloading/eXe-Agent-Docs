# Permissions and Safety

You decide what eXe may change. eXe reads and plans freely, and every project change runs through eXe: a small, clear change you ask for runs directly, larger work shows a plan for your approval first. **Plan before changes** sets how strict this is.

## Who can approve a plan

| Where you work | How you approve | How eXe records it |
|---|---|---|
| A small, clear change you ask for, in the eXe chat or an AI client | Your request is the approval; eXe runs it directly | Your request, quoted in the job |
| The eXe chat in Unreal | Click **Approve plan** or write `approve` | Your own decision |
| Claude Code, Codex, Claude Desktop, ChatGPT with sign-in | Write `approve` in that chat; the client passes your decision on | Delegated, not independently verified |
| ChatGPT without sign-in | Only at the level **Approve + execute** ([Remote Access](07_Remote_Access_ChatGPT.md)) | Delegated by your setting |

There is nothing to switch on for chat approval. **Jobs** shows every plan in full, but you approve in the chat where it was planned.

## What an approval covers

An approval covers exactly one sealed plan: its targets, its expected changes and the targets that must not change. Inside that scope eXe works without asking again, including retries and repairs. If the work needs anything outside the scope, eXe extends the plan and asks you again.

Project changes made through eXe are checked, backed up and listed for review. If an AI client changes files with its own tools instead of eXe, or connects directly to Unreal's MCP server, eXe cannot check, approve or revert those changes.

## Plan before changes

**Settings → Permissions → Plan before changes (all your projects)**

- **Automatic** (default): small, clear changes run directly; larger tasks show their plan as a suggestion first.
- **Only when I ask:** eXe shows a plan only when your request asks for one.
- **Always:** every change shows its plan for your approval first, also while YOLO is on.

Small means at most 5 steps and 5 changed assets or files, with nothing deleted and no Python script. Deletes and Python scripts always go through a plan. Full builds follow your build setting.

## Permissions

**Settings → Permissions → Write modes (all your projects)**

### Power Write

- **Off** after installation. While it is off, eXe refuses plans that change C++ or other source files or run your own Python scripts. Blueprint, asset and level work is not affected.
- **On:** approved plans may also change C++ and other source files and run Python scripts. Unreal's Undo does not cover these changes. eXe asks you to confirm before it turns on.
- **Check** shows the current state.

Turn Power Write on only for projects with version control or backups.

### YOLO

- **Off** after installation.
- **On:** eXe approves and runs every sealed plan from local or signed-in AI clients without asking you, including C++ changes, builds and deletions, for up to 90 minutes per job. If **Plan before changes** is **Always**, plans still wait for you and YOLO only covers builds. Power Write is on while YOLO is on. Access through a tunnel without sign-in is never covered. Changes stay listed and can be reverted where eXe has a saved copy. eXe asks you to confirm before it turns on.

Both switches are stored in a file of your Windows user. A program or AI client that runs its own shell commands as your user could change that file, so only give such tools shell access you trust.

## Builds

- **Settings → General → Build → Run full builds without asking** applies to the current project only. When it is on, eXe closes the editor and runs Unreal Build Tool for an approved step that needs a full build. When it is off, eXe asks you first: in the eXe chat (**Build now** / **Later**) or in the chat of your AI client. **Jobs** offers **Later**.
- When the editor closes, Unreal may ask you to **Save**, **Discard** or **Cancel** unsaved work.
- eXe never restarts the editor. After the build, open the project again yourself; eXe then continues the job. If the build failed, eXe shows the compiler errors.
- Claude Code: after you open the project again, type `/mcp`, choose **exe-loading** and click **Reconnect**.

The build setting is stored with the project, in `<YourProject>/Saved/eXe.Loading`; Power Write and YOLO are stored for your Windows user. A program or AI client that runs its own commands on your computer could change these files, so only give such tools access you trust.

eXe only starts Unreal Build Tool from your own Engine installation. It never starts other programs.

## Saving

eXe saves exactly the assets an approved step changed and nothing else. Your other unsaved work stays as it is.

## Reverting changes

- **Changes list** above the chat input: select files or assets and click **Revert** to put them back to the state before the job. The current version is kept as a backup.
- **Jobs:** for a finished job, **Undo this job's changes** puts every file the job changed back to the copy saved when the job started.
- Files someone changed after the job and unsaved editor changes are left alone and listed. C++ changes need a new build afterwards.
- eXe keeps the saved copies for 14 days. After that a change stays listed but can no longer be put back.
- Not covered: World Partition actor files (One File Per Actor) and files over 64 MB. eXe keeps no copy of them, so it cannot put them back. Changes an AI client made with its own tools are not covered either.
- **Edit → Undo** in the editor still works for many editor changes in the current session.

Use version control (for example Git, Perforce or Diversion) for every project you work on with AI.

## Good practice

- Keep Power Write and YOLO off until you know how eXe works in your project.
- Read the plan before you approve it, especially the targets that must not change.
- Commit your project before large jobs.
- Use project rules (**Settings → General → Project rules**) for conventions the AI should follow in every plan.

Previous: [Capabilities](05_Capabilities.md) · [Documentation Index](INDEX.md) · Next: [Remote Access with ChatGPT](07_Remote_Access_ChatGPT.md)
