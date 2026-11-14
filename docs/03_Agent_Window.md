# The eXe Agent Window

Everything in eXe happens in one dockable editor window called **eXe Agent**. Open it with the **eXe Agent** toolbar button, **Window → eXe Agent** or **Ctrl+Shift+Space**. The arrow next to the toolbar button opens a view directly.

The header shows your project and the state of eXe: **eXe running**, **eXe running · n job(s) running**, **eXe running, no project**, **eXe running · Unreal MCP is off, see Settings**, **eXe running · check Unreal MCP in Settings**, **Starting...**, **Reconnecting...** or **eXe could not start · see Settings**. Below it are four views: **Chat**, **Jobs**, **Tools** and **Settings**. When a job needs your decision, the view label reads **Jobs (n)** and the toolbar tooltip says so too.

## Chat

You describe tasks in your own words. eXe reads the project and works in the editor. Small, clear changes you ask for run directly; larger tasks show a plan for your approval first. **Settings → Permissions → Plan before changes** decides this ([Permissions and Safety](06_Permissions_And_Safety.md#plan-before-changes)).

- **Chats sidebar:** **+ New chat**, a search box and the chats of this project. **Show older chats** loads more. The arrows hide and show the sidebar.
- **AI controller:** the button at the top right shows the provider and model of the current chat. Click it to change provider, model and key for new chats ([Connect AI Providers](04_Connect_AI_Providers.md)). An existing chat keeps the controller it started with.
- **Message box:** **Enter** sends, **Shift+Enter** adds a line.
  - **+ Image** attaches up to 3 images (or drop them on the box). The model must be able to read images.
  - **+ Selection** adds the actors selected in the level and the assets selected in the Content Browser to your message.
- While eXe works, **Stop** stops the reply. You can still type: **Add note** passes a note to the running work.
- **Continue** appears when a turn reached its step limit or was paused at a safe point.
- **Inspect interrupted step** appears when an editor step was interrupted and its result is unknown. Nothing is repeated automatically.
- The **…** menu offers **Continue work**, **Refresh** and **Export chat as Markdown**.
- The chat shows the token usage reported by your provider. Optionally enter your provider's prices per 1M tokens in the AI controller to see costs.

### Decision cards

When eXe needs you, a card appears below the reply:

| Card | Buttons |
|---|---|
| **The plan above is ready for your approval** | **Approve plan**, **Not now**, **Details in Jobs** |
| **The next step needs your approval** | **Approve**, **Not now**, **Details in Jobs** |
| **A build is needed to continue** | **Build now**, **Later** |

Clicking a button is the same as typing the answer, for example `approve`. Approving runs exactly what the plan shows. Anything else needs a new plan.

### Changes list

Above the message box, **Changes (n)** lists the files and assets that finished jobs changed in this project. Unsaved editor changes are not included.

- **Diff** shows what a job changed in a text file. Unreal assets are binary and have no text diff; open the asset to compare it.
- **Keep** accepts the selected changes and hides them. Nothing on disk changes.
- **Revert** puts the selected files and assets back to the state before the job. The current version is kept as a backup.
- **All chats** also shows changes made from other chats and AI clients in this project.

Changes stay recorded for 14 days and can be reverted during that time. You can hide the list under **Settings → General**.

## Jobs

Every task that changes something becomes a job. **Jobs** lists all jobs of this project with a search box, the filters **All**, **Running**, **Planned**, **Waiting** and **Finished**, and **Needs attention only**.

Select a job to see:

- **Plan and decision:** the full plan text with targets, expected changes, **May change only**, **Must not change** and **May repair**. A long plan is paged. You approve a plan or a build in the chat where it was planned (the eXe chat or your AI client), not here. Buttons, depending on the state: **Request revision**, **Later** (for a build), **Stop work**, **Cancel work**. For a revision, describe what you want in the text box (at least 20 characters).
- **Progress:** the current and next step.
- **Result and checks:** how far the result is proven and every check that ran.
- **Steps:** what each step did. For game tests, **Show PIE screenshot** shows the picture taken after a game step.
- For finished jobs: **Show changes** and **Undo this job's changes**.
- **Copy summary** copies a short report. **Copy for support** copies the technical details of the job for a bug report.

## How a job works

1. **Goal.** You describe what you want in the chat or in your AI client.
2. **Plan.** The AI prepares a plan. eXe checks it against your project and seals it: exact targets, expected changes, targets that must not change.
3. **Approval.** A small, clear change you asked for counts as approved and runs directly. Otherwise you approve the plan in the chat, or ask for a revision.
4. **Execution.** eXe runs the approved steps. It may save, compile, ask for a build or repair a failed step, but only inside the approved scope. If the work needs something outside the plan, eXe extends the plan and asks you again.
5. **Verification.** eXe reads the result back from the editor or the files and compares it with the plan.
6. **Result.** The job ends with a result level.

## Result levels

| Level | Meaning |
|---|---|
| **Goal verified** | eXe read fresh values back from the editor and they meet the goal of the plan. |
| **Goal not independently verified** | The goal was reported as reached, but eXe could not confirm it with its own read-back, for example a visual change. Check it yourself. |
| **Change proven** | eXe proved the change itself (for example the saved file or asset matches the plan), but not the overall goal. |
| **Tool success** | The tool reported success and eXe confirmed it, but neither the change nor the goal was read back. |
| **Execution finished** | The step ran, but no check could confirm anything. |
| **Failure** | A step failed. The job shows the reason. |

A job shows the weakest level of its changing steps. eXe never shows a higher level than its checks support.

## Tools

Checks and a build that work without any AI provider. See [Capabilities](05_Capabilities.md#without-an-ai-provider).

## Settings

Settings are grouped. Use **Search settings** to find an option.

| Group | What you find there |
|---|---|
| **Connection** | Project, Unreal version, eXe Core, project link, editor, the address for AI clients (MCP) and the Unreal MCP status |
| **General** | Interface language, reply language, changes list, theme, builds, project rules |
| **Permissions** | Power Write, YOLO and Plan before changes ([Permissions and Safety](06_Permissions_And_Safety.md)) |
| **AI clients (Claude Code, Codex, Claude Desktop)** | Copy start commands, connect, renew or revoke the access token ([Connect AI Providers](04_Connect_AI_Providers.md)) |
| **Blender and your own MCP servers** | Check a Blender you have open (needs the free add-on MCP for Blender), and add your own MCP servers as extra tools for Claude Code and Codex |
| **ChatGPT and remote access** | Tunnel access with or without sign-in ([Remote Access with ChatGPT](07_Remote_Access_ChatGPT.md)) |
| **Asset generation** | Generate 3D models, images and sound effects with your own provider key or local server ([Capabilities](05_Capabilities.md#asset-generation)) |
| **Advanced** | Diagnostics for support |

Notes on **General**:

- **Language** changes the language of the eXe Agent window only: English, Deutsch, 日本語, 简体中文, 한국어, Español or Français. Default: same as the editor.
- **eXe replies in** sets the language of chat answers and plans, independent of the interface language. Plan headings exist only in English and German.
- **Theme** colors the eXe Agent window only. **Custom** lets you pick an accent color on a dark or light background.
- **Project rules:** each Markdown file in `ProjectDocs/eXe/Rules` is one rule, for example "Put new assets under /Game/MyFeature". Active rules are given to the AI for every new plan; they guide it, eXe does not enforce them. Rules the AI suggests start as proposals; delete their first line to activate them. **Rules on**, **Rules off**, **Check** and **Copy rules folder path** control them.

Previous: [Quick Start](02_Quick_Start.md) · [Documentation Index](INDEX.md) · Next: [Connect AI Providers](04_Connect_AI_Providers.md)
