# Permissions and Safety

You decide what eXe may change. eXe reads and plans freely, and every project change runs through eXe: a small, clear change you ask for runs directly, larger work shows a plan for your approval first. **Plan before changes** sets how strict this is.

## Who can approve a plan

| Where you work | How you approve | How eXe records it |
|---|---|---|
| A small, clear change you ask for, in the eXe chat or an AI client | Your request is the approval; eXe runs it directly | Your request, quoted in the job |
| The eXe chat in Unreal | Click **Approve plan** or type an approval such as `approve` | Your own decision |
| Claude Code, Codex, Claude Desktop, ChatGPT with sign-in | Write `approve` in that chat; the client passes your decision on | Delegated, not independently verified |
| ChatGPT without sign-in | Only at the level **Approve + execute** ([Remote Access](07_Remote_Access_ChatGPT.md)) | Delegated by your setting |

There is nothing to switch on for chat approval. **Jobs** shows every plan in full, but you approve in the chat where it was planned.

## Approve by typing

In the eXe chat, you can type your answer instead of clicking. The whole message must be the answer; a sentence that only contains one of these words is a normal message. Upper or lower case and a final `.` or `!` do not matter.

| Card | Counts as yes | Counts as not now |
|---|---|---|
| **The plan above is ready for your approval** or **The next step needs your approval** | `approve`, `yes`, `ok`, `okay`, `go ahead`, `do it`, `just do it`, `do it directly`, and the same words in German, Spanish, French, Japanese, Korean and Chinese (for example `freigeben`, `ja`, `mach`, `aprobar`, `oui`) | `no`, `later`, and the same words in the other languages (for example `nein`, `später`, `non`) |
| **A build is needed to continue** | `yes` (or `ja`, `sí`, `oui` ...) | `no` or `later` |

Anything else you type is passed to the AI as a normal message, for example `Change step 2 so that it also renames the asset.`

## Ask for a plan, or skip it

You can say what you want in your request:

- `Show me the plan first.` eXe shows a plan, even for a small change.
- `Do it without a plan.` A larger task can then run directly, without the size limit below. Deletes, Python scripts and editor restarts still ask you first.

## What an approval covers

An approval covers exactly one sealed plan: its targets, its expected changes and the targets that must not change. Inside that scope eXe works without asking again, including retries and repairs. If the work needs anything outside the scope, eXe extends the plan and asks you again.

Project changes made through eXe are checked, backed up and listed for review. If an AI client changes files with its own tools instead of eXe, or connects directly to Unreal's MCP server, eXe cannot check, approve or revert those changes.

## Plan before changes

**Settings → Permissions → Plan before changes (all your projects)**

- **Automatic** (default): small, clear changes run directly; larger tasks show their plan as a suggestion first.
- **Only when I ask:** eXe shows a plan only when your request asks for one.
- **Always:** every change shows its plan for your approval first, also while YOLO is on.

Small means at most 5 steps and 5 changed assets or files, with nothing deleted and no Python script, and eXe can read every asset, Blueprint or level change back itself. Deletes and Python scripts always go through a plan. Full builds follow your build setting.

## Permissions

**Settings → Permissions → Write modes (all your projects)**

The status line under the buttons shows the current state, for example `YOLO: off · Power Write: off · Plan: automatic`.

### Power Write

- **Off** after installation. While it is off, eXe refuses plans that change C++ or other source files or run your own Python scripts. Blueprint, asset and level work is not affected.
- **On:** approved plans may also change C++ and other source files and run Python scripts. Unreal's Undo does not cover these changes. eXe asks you to confirm before it turns on.
- **Check** shows the current state. **Power Write: on only while YOLO is on** means you did not turn Power Write on yourself; it switches off again with YOLO.

Turn Power Write on only for projects with version control or backups.

### YOLO

- **Off** after installation.
- **On:** eXe approves and runs every sealed plan from local or signed-in AI clients without asking you, including C++ changes, builds and deletions, for up to 90 minutes per job. Power Write is on while YOLO is on. Access through a tunnel without sign-in is never covered. Changes stay listed and can be reverted where eXe has a saved copy. eXe asks you to confirm before it turns on, and the header shows **YOLO on**.
- If **Plan before changes** is **Always**, plans still wait for you and YOLO only covers builds. The status line then says **YOLO: on (builds only; plans wait because Plan is Always)**.

### Which settings apply where

| Setting | Applies to |
|---|---|
| Power Write, YOLO, **Plan before changes** | All your projects (your Windows user) |
| **Run full builds without asking** | This project |
| ChatGPT and tunnel access (level without sign-in, sign-in settings) | This project |

These settings are stored in files of your Windows user or of the project. A program or AI client that runs its own shell commands as your user could change those files, so only give such tools shell access you trust.

## C++ and builds

C++ changes need **Power Write**, and builds need the Visual Studio C++ tools and the Windows SDK that Unreal Engine 5.8 requires.

### Live Coding

For a change inside existing `.cpp` files, eXe uses Live Coding through the Engine plugin `LiveCodingToolset`, which is switched on together with eXe Agent. Live Coding updates the code in the running editor; the job shows **Live Coding running**.

Important: Live Coding changes only the running editor, not the files Unreal loads at the next start. **Before you restart Unreal after a Live Coding change, close it, build the project in your IDE (Visual Studio or Rider) and open it again.** Otherwise the C++ change is gone after the restart. eXe reminds you of this in the chat.

### Full builds

Other C++ changes need a full build, for example a new class, a changed header (`.h`), a changed `Build.cs` file or a changed constructor. Unreal Build Tool can only build while the editor is closed.

- **Settings → General → Build → Run full builds without asking** applies to the current project only. When it is off, eXe asks you first, unless the plan you approved already includes the build: in the eXe chat (**Build now** / **Later**) or in the chat of your AI client. **Jobs** offers **Later**. When it is on, eXe builds right away.

What happens during a full build:

1. eXe saves the assets the job changed. For other unsaved work, Unreal may ask you whether to save it. If you click **Cancel** there, the editor stays open and nothing is built.
2. The editor closes and Unreal Build Tool runs in a console window titled **eXe Full Build: Unreal Build Tool is running. When this window closes, reopen your project.** The job shows **Closing editor** and **Building editor target**.
3. When the console window has closed, open your project again yourself. eXe never restarts the editor.
4. eXe reads the build result and continues the job.

If the build failed:

- Open `<YourProject>/Saved/eXe.Loading/LAST_FULL_BUILD.md`. eXe writes this file before every full build. It names the build log, says that the first `error` line in the log is the cause, and contains the exact build command.
- Fix the error in your IDE, then open the project (Unreal offers to rebuild) or run the build command from the file. When the editor is open again, eXe takes your fix over as your own change and asks for one confirming build.

Claude Code: after you open the project again, type `/mcp`, choose **exe-loading** and click **Reconnect**.

eXe only starts Unreal Build Tool from your own Engine installation. It never starts other programs.

## Saving

eXe saves exactly the assets an approved step changed and nothing else. Your other unsaved work stays as it is.

## Reverting changes

- **Changes list** above the chat input: select files or assets and click **Revert** to put them back to the state before the job. The current version is kept as a backup. If a later eXe job changed the same file, that newer change is reverted first.
- **Jobs:** for a finished job, **Undo this job's changes** puts every file the job changed back to the copy saved when the job started.
- Files someone changed after the job and unsaved editor changes are left alone and listed. C++ changes need a new build afterwards.
- eXe keeps the saved copies for 14 days. After that the change leaves the **Changes** list; **Jobs** still shows it, but it can no longer be put back.
- Not covered: World Partition actor files (One File Per Actor) and files over 64 MB. eXe keeps no copy of them, so it cannot put them back. Changes an AI client made with its own tools are not covered either.
- **Edit → Undo** (Ctrl+Z) is not a way to undo eXe's changes: eXe's steps are not entries in the editor's undo history. Use **Revert** in **Changes** or **Undo this job's changes** in **Jobs**.

Use version control (for example Git, Perforce or Diversion) for every project you work on with AI.

## Good practice

- Keep Power Write and YOLO off until you know how eXe works in your project.
- Read the plan before you approve it, especially the targets that must not change.
- Commit your project before large jobs.
- Use project rules (**Settings → General → Project rules**) for conventions the AI should follow in every plan.

Previous: [Capabilities](05_Capabilities.md) · [Documentation Index](INDEX.md) · Next: [Remote Access with ChatGPT](07_Remote_Access_ChatGPT.md)
