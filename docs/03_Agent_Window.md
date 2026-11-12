# The eXe Agent Window

Everything in eXe happens in one dockable editor window called **eXe Agent**. Open it with the **eXe Agent** toolbar button, **Window → eXe Agent** or **Ctrl+Shift+Space**. The arrow next to the toolbar button opens a view directly.

On this page:

- [Header](#header)
- [Chat](#chat): talking to eXe, what you see while it works, decision cards, the changes list
- [Jobs](#jobs): every task with its plan, progress, result and undo
- [How a job works](#how-a-job-works) and [Result levels](#result-levels)
- [Tools](#tools) and [Settings](#settings)

## Header

The header shows the project name, a colored dot and the state of eXe. The dot and the texts are explained in [Installation](01_Installation.md#step-3-open-exe-agent-and-check-that-it-works). The possible texts are **eXe running**, **eXe running · n job(s) running**, **eXe running, no project**, **eXe running · Unreal MCP is off, see Settings**, **eXe running · check Unreal MCP in Settings**, **Starting...**, **Reconnecting...** and **eXe could not start · see Settings**.

A warning in the header tells you when changes can run without your confirmation:

| Warning | Meaning |
|---|---|
| **YOLO on** | YOLO is on: plans from local or signed-in AI clients run without asking you ([YOLO](06_Permissions_And_Safety.md#yolo)) |
| **Remote can approve** | ChatGPT or tunnel access without sign-in is set to **Approve + execute** for this project ([Remote Access](07_Remote_Access_ChatGPT.md)) |
| **YOLO on · remote can approve** | Both |

Below the header are four views: **Chat**, **Jobs**, **Tools** and **Settings**. When a job needs your decision, the view label reads **Jobs (n)**.

## Chat

You describe tasks in your own words. eXe reads the project and works in the editor. Small, clear changes you ask for run directly; larger tasks show a plan for your approval first ([Plan before changes](06_Permissions_And_Safety.md#plan-before-changes)).

### Start page

A new chat asks **What should eXe Agent do?** and offers:

- **Connect an AI controller**: choose provider, model and key ([Connect AI Providers](04_Connect_AI_Providers.md)).
- **No API key? Use Claude Code or Codex with your own login**: opens the settings for AI clients ([Option 2](04_Connect_AI_Providers.md#option-2-claude-code-codex-or-claude-desktop)). Shown while no AI is connected.
- Once an AI is connected: three example tasks. Clicking one puts it into the message box, so you can edit it before you send it.

### Chats sidebar

**+ New chat**, a search box and the chats of this project. **Show older chats** loads more. **Hide chats** and **Show chats** fold the sidebar away and back.

### AI controller

The button at the top right shows the provider and model of the current chat, or **Connect AI** when none is set. Click it to change provider, model, key, chat length and prices. A new provider or model applies to new chats; an existing chat keeps the controller it started with. Chat length applies to all chats after **Save**. The controller is saved for this project; the key is saved for your Windows user. Details: [Connect AI Providers](04_Connect_AI_Providers.md#option-1-the-exe-chat-with-your-api-key).

### Message box

- **Enter** sends, **Shift+Enter** adds a line.
- **+ Image** attaches up to 3 images of at most 3 MB each, as PNG, JPEG, GIF or WebP. You can also drop them on the box. The model must be able to read images.
- **+ Selection** adds the actors selected in the level and the assets selected in the Content Browser to your message.
- While eXe works, you can still type: **Add note** passes a note to the running work.

### What you see while eXe works

| You see | Meaning |
|---|---|
| **Starting the chat...** | The chat is being prepared |
| **Thinking...** / **Writing...** | The AI is thinking or writing its reply |
| **Working in the editor · reading the project** | eXe runs a step in the editor. The text after the dot names the step, for example **looking up Unreal tools**, **checking the plan draft**, **preparing the plan for your approval**, **running a step of the approved plan**, **building**, **checking the result** or **saving notes in the eXe workspace** |
| **eXe · 3 steps: reading the project · done** | A grey line that sums up the steps eXe ran, or how many were **not successful** |
| **Waiting for the running job. Progress is shown below and under Jobs.** | A job runs; the chat waits for it |
| **Waiting for your decision.** | A decision card below the reply needs you |
| **Compacting the chat: ...** | The AI writes a summary of the chat (see [Long chats](#long-chats-and-costs)) |
| **Paused at a safe point. Click Continue to go on.** | eXe stopped at a safe point, for example at its step limit. Click **Continue** |
| **Stopping...** / **Stopped.** | You clicked **Stop** |

Cards below a reply:

- **Plan card** (**Plan ·** and its state, for example **Plan · Needs your decision**, with the plan name below): the number of steps, the assets or files the plan may change and how many steps are done, for example `4 steps · 2 assets or files · 1 of 4 done`. Each step shows its kind (**Asset**, **C++ source**, **Build** or **Editor action**) and its state; the current one says **running now**. **Full plan text** shows the complete plan.
- **Job card** (**Work in progress**): the current step after **Now:**. When the job waits for you, it says **Your decision is needed · Open in Jobs**.
- **Decision card**: see [Decision cards](#decision-cards).

When a reply finishes while you work elsewhere in the editor, Unreal shows a short notice in the corner: **eXe Agent: the reply is ready.**, **eXe Agent: waiting for your decision.**, **eXe Agent: stopped.** or **eXe Agent: the turn needs your attention.**

### Buttons in the chat

- **Stop** stops the current reply.
- **Continue** appears when a turn reached its step limit or was paused at a safe point.
- **Inspect interrupted step** appears when an editor step was interrupted and its result is unknown. Nothing is repeated automatically. Check the project, then continue.
- The **…** menu has five entries: **Continue work** (resume this task from eXe's current state), **Compact chat now**, **Continue in a new chat**, **Refresh** and **Export chat as Markdown**.

### Long chats and costs

The AI reads the whole chat again for every reply, so a long chat costs more per reply than a short one.

- **Chat length** in the AI controller sets when the AI summarizes a chat: 100k, 200k (recommended), 300k, 500k, 700k or 900k tokens. Above 200k, eXe shows a cost warning. The setting applies to all chats after **Save**.
- When a chat reaches its length, the AI writes a summary and continues from it. All messages stay visible, and the chat shows **Chat compacted. The AI continues from a summary of the messages above; they stay visible here.**
- **Compact chat now** (… menu) does this right away.
- **Continue in a new chat** (… menu) opens a new chat that starts from a summary of this one. The new chat starts with `Continued from "<title>". The AI starts from a summary of that chat.` and **Open that chat** takes you back to the earlier one.

The grey line at the top of a chat shows the provider, the model and the tokens your provider reported: `tokens in 120,000, out 3,400`, followed by `chat length about 45k of 200k tokens`. **not fully reported** means the provider did not report every round. If you enter your prices in the AI controller, the line also shows `about 0.4200 USD with your prices`. This is an estimate; your provider's bill is what counts.

### Decision cards

When eXe needs you, a card appears below the reply:

| Card | Buttons |
|---|---|
| **The plan above is ready for your approval** | **Approve plan**, **Not now**, **Details in Jobs** |
| **The next step needs your approval** | **Approve**, **Not now**, **Details in Jobs** |
| **A build is needed to continue** | **Build now**, **Later** |

Clicking a button is the same as typing the answer. Approving runs exactly what the plan shows. Anything else needs a new plan. Which typed answers count: [Permissions and Safety](06_Permissions_And_Safety.md#approve-by-typing).

### Changes list

Above the message box, **Changes (n)** lists the files and assets that finished jobs changed in this project. Click it to open the list. Unsaved editor changes are not included.

- Each row shows **new** or **changed**.
- **Select all** selects every row.
- **Diff** shows what a job changed in a text file. Unreal assets are binary and have no text diff; open the asset to compare it.
- **Keep** accepts the selected changes and hides them. Nothing on disk changes. A kept row comes back when the file changes again.
- **Revert** puts the selected files and assets back to the state before the job. The current version is kept as a backup. If a later eXe job changed the same file, that newer change is reverted first.
- **All chats** also shows changes made from other chats and AI clients in this project.

After **Revert**, eXe reports for example `2 reverted, 1 not reverted. Rows that stay listed show why.` The reasons:

| Reason on the row | Meaning |
|---|---|
| **changed again later** | Someone changed the file after the job. eXe leaves it alone |
| **no saved copy** | eXe has no copy, for example for a World Partition actor file or after 14 days |
| **BASELINE_TOO_LARGE** | The file is larger than 64 MB, so eXe kept no copy |
| **result not recorded** | The job did not record a result for this file |
| **job still running** | Wait until the job has finished |

The list shows changes from the last 14 days, which can be reverted during that time. Older jobs still show their changes under **Jobs → Show changes**, but they can no longer be reverted. You can hide the list under **Settings → General → Show changes above the chat input**; changes are still recorded.

## Jobs

Every task that changes something becomes a job. **Jobs** lists all jobs of this project.

- A search box (**Search work...**), the filters **All**, **Running**, **Planned**, **Waiting** and **Finished**, and **Needs attention only**.
- A line with the counts: `Running 1 · Planned 0 · Waiting 0 · Finished 12`. (Known issue: it can show **Running 0** while a job runs; the list is right.)
- **Load older work** and **Load more** show older jobs.

Select a job to see its details:

- **What this work does:** **Goal**, **Plan / approval**, **Expected changes**, **Assets**, **Files**, **May change only**, **Must not change** and **May repair**.
- **Plan and decision:** the full plan text. A long plan is split into pages: `Plan text, characters 1–16000 of 24000.` **Read next plan page** and **Read from beginning** move through it. You approve a plan or a build in the chat where it was planned (the eXe chat or your AI client), not here. Buttons, depending on the state:
  - **Request revision**: describe what should change in the text box (at least 20 characters). The AI then prepares a new plan.
  - **Later**: postpone a build.
  - **Stop work** and **Cancel work**: both end the job for good. Nothing more runs, and changes from steps that already finished stay listed under **Changes**, where you can revert them. The only difference is the word in the job's history while the job runs: **Stopped** or **Cancelled**. A plan that has not started yet is recorded as **Cancelled** either way. If you typed something in the text box, it is used as the reason and needs at least 20 characters; otherwise leave the box empty.
- **Progress:** the current step (**Now**) and the next one (**Next**). **Blocked:** names what stops the job.
- **Required results:** the overall results the plan must reach, each with its state. **No separate overall result checks; every step is still checked on its own.** means the plan has none.
- **Result and checks:** **How far the result is proven** (the [result level](#result-levels)), **Checks overall**, every single check, and the changed files and editor actions. For game tests, **Show PIE screenshot** or **Picture after game step n** opens the screenshot. **Image is usable** means the picture shows something; **The image may be empty or black and does not prove the result** means you should check the game yourself.
- **Steps:** what each step did.
- For finished jobs: **Show changes** lists every target as **unchanged**, **changed · can be undone** or **changed**. **Undo this job's changes** puts every file the job changed back to the copy saved when the job started.
- **Copy summary** copies a short report. **Copy for support** copies the technical details of the job for a bug report. API keys are not included.
- **Evidence**, **Diagnostics**, **Execution Context** and **Technical details (for support)** are for support. You do not need them for normal work.

### Status words

| Word | Meaning |
|---|---|
| **Running** / **In progress** | The job or step is running now |
| **Not started yet** | Planned, waits for its turn |
| **Needs your decision** | Waits for your approval or answer in the chat |
| **Waiting** | Waits for something else, for example the compiler or another job |
| **Blocked** | Cannot go on; the reason is shown after **Blocked:** |
| **Done** / **Passed** | Finished, checks passed |
| **Partly done** | Some steps or checks finished, others did not |
| **Failed** | A step failed; the job shows the reason |
| **Stopped** / **Cancelled** | You ended the job with **Stop work** or **Cancel work** |
| **Skipped** | The step did not run |
| **Sealed** | The plan is fixed and checked; nothing in it can change anymore |
| **Build queued**, **Waiting for compiler availability**, **Closing editor**, **Building editor target**, **Live Coding running** | Steps of a build ([Builds](06_Permissions_And_Safety.md#c-and-builds)) |

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
| **Connection** | Project, Unreal version, eXe Core, project link, editor, the address for AI clients (MCP) and the Unreal MCP status. **Setup**, **Start** or **Recovery** appears when eXe Core is not running; each starts it again |
| **General** | Interface language, reply language, changes list, theme, builds, project rules |
| **Permissions** | Power Write, YOLO and Plan before changes ([Permissions and Safety](06_Permissions_And_Safety.md)) |
| **AI clients (Claude Code, Codex, Claude Desktop)** | Connect, copy start commands, renew or revoke the access token ([Connect AI Providers](04_Connect_AI_Providers.md)) |
| **Blender and your own MCP servers** | Check a Blender you have open, and add your own MCP servers for Claude Code and Codex ([Capabilities](05_Capabilities.md#blender-and-your-own-mcp-servers)) |
| **ChatGPT and remote access** | Tunnel access with or without sign-in ([Remote Access with ChatGPT](07_Remote_Access_ChatGPT.md)) |
| **Asset generation** | Generate 3D models, images and sound effects with your own provider key or local server ([Capabilities](05_Capabilities.md#asset-generation)) |
| **Advanced** | Diagnostics for support |

### General

- **Language** changes the language of the eXe Agent window only: English, Deutsch, 日本語, 简体中文, 한국어, Español or Français. Default: same as the editor. A few texts change the next time you open the window.
- **eXe replies in** sets the language of chat answers and plans. Default: **English**. **Automatic (language of your message)** answers in the language you write in. Plan headings exist only in English and German. Some detail messages from the eXe core are always in English.
- **Show changes above the chat input** shows or hides the [changes list](#changes-list).
- **Theme** colors the eXe Agent window only: **Same as Unreal**, **Dark**, **Light**, **Midnight blue**, **Crimson**, **Black and orange**, **Black and green** or **Custom**. With **Custom** you pick an **Accent color** and, if you like, a **Light background**. Drop-down lists and menus keep Unreal's colors.
- **Build → Run full builds without asking** applies to this project only ([Builds](06_Permissions_And_Safety.md#c-and-builds)).
- **Project rules:** see below.

### Project rules

Project rules are short instructions the AI gets for every new plan in this project, for example "Put new assets under /Game/MyFeature" or "Name Blueprints with the prefix BP_". They guide the AI; eXe does not enforce them.

1. Click **Copy rules folder path**. It creates the folder `ProjectDocs/eXe/Rules` in your project folder (next to the `.uproject` file) if it does not exist yet and copies its path. You can also create the folder yourself.
2. Add one Markdown file per rule, for example `assets.md`, with one or a few sentences.
3. Click **Check**. The line shows `Project rules: on · 1 active · 0 proposal(s) · ...`.

Good to know:

- When the AI suggests a rule, it is saved as a proposal. The file starts with the line `<!-- exe-rule: proposed; delete this line to activate -->`. Delete that line to activate the rule.
- All active rules together may have up to 6,000 characters. A rule that no longer fits is skipped; keep rules short.
- **Rules on** and **Rules off** switch all rules of this project on or off.
- To share rules with your team, commit the `Rules` folder to version control.

### Advanced

**Advanced** shows diagnostics for support, such as **Core / Tool Surface**, **Controllers / Providers** and **Runtime**, with technical lines like `Default mode: ASK`. You do not need this group for normal work. Do not click **Stop Runtime** unless support asks you to: it stops eXe until you click **Start** under **Connection** or restart the editor.

Previous: [Quick Start](02_Quick_Start.md) · [Documentation Index](INDEX.md) · Next: [Connect AI Providers](04_Connect_AI_Providers.md)
