# Permissions and Safety

You decide what eXe may change. After installation eXe can read and plan, and every change needs your approval of an exact plan.

## Who can approve a plan

| Where you work | How you approve | How eXe records it |
|---|---|---|
| The eXe chat in Unreal | Click **Approve plan** or write `approve` | Your own decision |
| **Jobs** in the eXe Agent window | Tick the confirmation and click **Approve exact plan** | Your own decision |
| Claude Code, Codex, Claude Desktop, ChatGPT with sign-in | Write `approve` in that chat; the client passes your decision on | Delegated, not independently verified |
| ChatGPT without sign-in | Only at the level **Approve + execute** ([Remote Access](07_Remote_Access_ChatGPT.md)) | Delegated by your setting |

There is nothing to switch on for chat approval.

## What an approval covers

An approval covers exactly one sealed plan: its targets, its expected changes and the targets that must not change. Inside that scope eXe works without asking again, including retries and repairs. If the work needs anything outside the scope, eXe extends the plan and asks you again.

Project changes made through eXe are checked, backed up and listed for review. If an AI client changes files with its own tools instead of eXe, or connects directly to Unreal's MCP server, eXe cannot check, approve or revert those changes.

## Permissions

**Settings → Permissions → Write modes (all projects of this Windows user)**

### Power Write

- **Off** after installation. While it is off, eXe refuses plans that change C++ or other source files. Blueprint, asset and level work is not affected.
- **On:** approved plans may also change C++ and other source files. Unreal's Undo does not cover these changes. eXe asks you to confirm before it turns on.
- **Check** shows the current state.

Turn Power Write on only for projects with version control or backups.

### YOLO

- **Off** after installation.
- **On:** eXe approves and runs every sealed plan from local or signed-in AI clients without asking you, including C++ changes, builds and deletions, for up to 90 minutes per job. Power Write is on while YOLO is on. Access through a tunnel without sign-in is never covered. Changes stay listed and can be reverted where eXe has a saved copy. eXe asks you to confirm before it turns on.

Both switches are stored in a file of your Windows user. A program or AI client that runs its own shell commands as your user could change that file, so only give such tools shell access you trust.

## Builds

- **Settings → General → Run full builds automatically** applies to the current project only. When it is on, eXe closes the editor and runs Unreal Build Tool for an approved step that needs a full build. When it is off, eXe asks you to build, in the chat (**Build now** / **Later**) or in **Jobs** (**Allow eXe to build** / **Later**).
- When the editor closes, Unreal may ask you to **Save**, **Discard** or **Cancel** unsaved work.
- eXe never restarts the editor. After the build, open the project again yourself; eXe then continues the job. If the build failed, eXe shows the compiler errors.

eXe only starts Unreal Build Tool from your own Engine installation. It never starts other programs.

## Auto Save

**Settings → General → Auto Save** saves exactly the assets changed by an approved action and nothing else. It is off by default and independent of the build setting. When it is off, Unreal may ask you to save.

## Reverting changes

- **Changes list** above the chat input: select files or assets and click **Revert** to put them back to the state before the job. The current version is kept as a backup.
- **Jobs:** for a finished job, **Undo this job's changes** puts every file the job changed back to the copy saved when the job started.
- Files someone changed after the job and unsaved editor changes are left alone and listed. C++ changes need a new build afterwards.
- **Edit → Undo** in the editor still works for many editor changes in the current session.

Use version control (for example Git, Perforce or Diversion) for every project you work on with AI.

## Good practice

- Keep Power Write and YOLO off until you know how eXe works in your project.
- Read the plan before you approve it, especially the targets that must not change.
- Commit your project before large jobs.
- Use project rules (**Settings → General → Project rules**) for conventions every plan must follow.

Previous: [Capabilities](05_Capabilities.md) · [Documentation Index](INDEX.md) · Next: [Remote Access with ChatGPT](07_Remote_Access_ChatGPT.md)
