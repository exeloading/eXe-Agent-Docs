# Troubleshooting

Find the message you see on this page (use your browser's search, **Ctrl+F**), or look at the section for your problem. Answers to general questions are in the [FAQ](12_FAQ.md).

On this page:

- [eXe does not start](#exe-does-not-start)
- [Unreal MCP messages](#unreal-mcp-messages)
- [Chat messages](#chat-messages)
- [Claude Code, Codex and Claude Desktop](#claude-code-codex-and-claude-desktop)
- [Builds and C++](#builds-and-c)
- [Jobs and changes](#jobs-and-changes)
- [How to ask for help](#how-to-ask-for-help)

## eXe does not start

### The header stays on "Starting..." or shows "eXe could not start · see Settings"

**Likely causes:** a required Engine plugin is disabled, or a Python dependency conflict with another plugin.

1. Open **Settings → Connection** and read the reason (table below).
2. Check **Edit → Plugins**: **Python Editor Script Plugin**, **Model Context Protocol**, **Toolset Registry** and **All Toolsets** are enabled.
3. Open **Window → Output Log** and filter for `LogPython` and for `eXe`. A dependency conflict is named there.
4. Close the editor and open the project again. Do not run `pip install` and do not reload Python modules by hand.

| Reason under Settings → Connection | What to do |
|---|---|
| **eXe Core did not start in time. Check the Output Log for LogPython errors, then click Start.** | Look for `LogPython` errors in the Output Log, then click **Start** |
| **Unreal's Python scripting is not ready. Make sure the Python Editor Script Plugin is enabled, then restart the editor.** | Enable **Python Editor Script Plugin** in **Edit → Plugins** and restart |
| **Unreal's own Python (Engine/Binaries/ThirdParty/Python3) is missing. Verify the engine installation in the Epic Games Launcher.** | In the Epic Games Launcher, open the engine's menu and choose **Verify** |
| **eXe was started for a different project setup. Restart the editor.** | Restart the editor |
| **eXe's start script gave no answer. Check the Output Log for LogPython errors.** | Look for `LogPython` errors and send them to support |
| **EDITOR_PYTHON_DEPENDENCY_ALREADY_LOADED:** followed by a package name and a path | Another plugin loaded its own copy of a Python package that eXe needs before eXe started. The path shows which plugin it is. Disable that plugin for this project in **Edit → Plugins** and restart the editor. Do not run `pip install`. If you need both plugins, send the full line to support |

**Setup**, **Start** or **Recovery** appears under **Settings → Connection** when eXe Core is not running. Each one starts eXe Core again.

### "Last known state, n s old."

A banner with this text means the window lost contact with eXe Core for a moment and shows the last known state. Lines in **Settings** may end with **(last known state, eXe Core is not answering)**. Wait a few seconds. If it stays, check the header and the reasons above.

### "eXe running, no project"

eXe Core runs, but it is not connected to the open project yet. Wait a moment. If it stays, restart the editor.

## Unreal MCP messages

### "eXe running · Unreal MCP is off, see Settings"

Settings shows **Unreal MCP: not running at http://127.0.0.1:8000/mcp**. Unreal's MCP server is not started.

1. Open **Edit → Editor Preferences**, search for `Model Context Protocol` and enable **Auto Start Server**.
2. To start it right away: open **Window → Output Log**, type `ModelContextProtocol.StartServer` into the **Cmd** field and press **Enter**.
3. Check that the port and path match the address shown under **Settings → Connection**.

If the plugin **Model Context Protocol** is disabled in **Edit → Plugins**, enable it and restart the editor first.

### "eXe running · check Unreal MCP in Settings"

Open **Settings → Connection** and hover over the **Unreal MCP** line. It shows the steps for your case:

| Unreal MCP line | What to do |
|---|---|
| **... belongs to another Unreal editor, so eXe does not use it.** | Two projects use the same MCP port. In this project, set **Editor Preferences → Model Context Protocol → Server Port Number** to a free port (for example `8001`), keep **Auto Start Server** on and restart the editor |
| **eXe cannot confirm that ... belongs to this editor and sends nothing to it. Retry in a moment.** | Wait a moment. If it stays, check that the address has the form `http://127.0.0.1:<port>/mcp` and report the message |
| **the address ... is invalid** | Use a local address with a port, for example `http://127.0.0.1:8000/mcp` |
| Toolsets are missing (in the tooltip) | Follow the step in the tooltip. For the **Epic editor toolsets**, enable them in **Editor Preferences → Model Context Protocol** and restart. When the tooltip asks you to enable the **eXe.Loading plugin** or the **VibeUE plugin**, check that **eXe Agent** is enabled in **Edit → Plugins** (VibeUE is part of eXe Agent) and restart |

### Two editors are open

Each editor runs its own eXe with its own jobs and its own address; **Settings → Connection** shows it. Each project also needs its own Unreal MCP port (see the first row above). Claude Desktop and clients you start yourself work with the project of the last **Connect / repair**; click **Connect / repair** in the project you work on ([Two projects](04_Connect_AI_Providers.md#two-projects-and-switching-projects)).

## Chat messages

Most messages end with a code in brackets, for example `(CHAT_PROVIDER_HTTP_429)`; a few start with the code instead. The code is for support.

| Message | Cause | What to do |
|---|---|---|
| **No AI is connected yet. Choose one under Connect AI.** | No AI controller is set for this project | Click **Connect AI** and set provider, model ID and key ([Connect AI Providers](04_Connect_AI_Providers.md)) |
| **Enter a model ID under Connect AI.** | The model field is empty | Enter the model ID |
| **This is a model name, not a model ID. ...** | You entered a display name such as `Claude Sonnet 5.5` | Enter the ID, for example `claude-sonnet-5-5`, exactly as your provider lists it |
| **This AI provider needs a key. Add it under Connect AI.** | No key is saved for this provider | Paste your API key and click **Save** |
| **The AI provider rejected the key. Check it under Connect AI.** | The key is wrong, expired or deleted at the provider | Create a new key at your provider and save it |
| **The key could not be saved in Windows Credential Manager.** | Windows refused to store the key | Try again. If it keeps failing, check that Windows Credential Manager works for your Windows user, and contact support |
| **The AI provider refused the request for now: a rate limit, or no credit left. ...** | Too many requests in a short time, or your provider account has no credit | Wait and try again, or add credit and check your plan with the provider. eXe cannot change this limit |
| **The AI provider rejected the request.** | The provider refused it, for example because the model ID does not exist for your account | Check the model ID and your account at the provider. The text after the message is the provider's own reason |
| **The AI provider reported an internal error, also on a second try. ...** | A problem at the provider | Send the message again in a moment |
| **The AI provider could not be reached. ...** | No internet connection, a firewall, or a wrong local address | Check your connection. For a local model, check that the server runs and that its address is on this PC and ends in `/v1`. Behind a company proxy, see [Known Limitations](09_Known_Issues_And_Limitations.md) |
| **The reply broke off. Send the message again.** | The connection to the provider broke during the reply | Send the message again |
| **The model did not produce a usable tool call, not even on a second try. ...** | The model could not answer in the form eXe needs. Common with small local models | Send the message again, or choose a stronger model |
| **No plan has been submitted yet, so there is nothing to approve. ...** | The AI talked about a plan but did not submit it | Ask it to submit its plan, or choose a stronger model |
| **The AI model declined this request. ...** | The model refused the request | Rephrase it in a new chat, or choose another model. Your project and jobs are not affected |
| **The reply reached the model's output limit and stopped. Ask for a smaller step.** | The answer got too long for the model | Ask for a smaller step |
| **This request is too large for the model, even after summarizing the chat. ...** | The message, the attached images or the chat do not fit into the model | Send less at once, or start a new chat |
| **The request is too large for the AI provider. Send less at once or remove an image.** | The provider refused the size of the request | Send less at once or remove an image |
| **This chat has grown too long to save. ...** | The chat history is too large | Choose **Continue in a new chat** in the **…** menu |
| **The AI could not summarize this chat. ...** | Compacting failed | Try again, or start a new chat |
| **There is nothing to summarize in this chat yet.** | **Compact chat now** on a new chat | Nothing to do |
| **This works only while the chat is idle. ...** | You used a menu entry while eXe was working | Wait for the current step or your decision |
| **This turn reached its step limit. Click Continue or send a new message.** | Long tasks are split into turns | Click **Continue** |
| **Another chat is still working. Wait for it or stop it, then click Continue.** | Only one chat can work at a time | Wait, or open the other chat and click **Stop** |
| **The open project changed. Start a new chat for this project.** | The chat belongs to a project that is no longer open | Click **+ New chat** |
| **eXe Core is not ready. Check Settings > Connection, then send the message again.** | eXe Core is starting or stopped | See [eXe does not start](#exe-does-not-start) |
| **An editor step was interrupted and its result is unknown. ...** | The editor closed or crashed during a step | Click **Inspect interrupted step**, check the project, then continue. eXe repeats nothing automatically |
| **An image is missing or too large. ...** / **This image type is not supported. ...** | Up to 3 images, at most 3 MB each, PNG, JPEG, GIF or WebP | Use smaller or other images |
| **This model cannot read images. ...** | The chosen model has no image input (with DeepSeek, only `deepseek-flash` reads images) | Remove the image or choose another model |
| **Something changed at the same time. Try again in a moment.** | Two actions met at the same moment | Try again |
| **eXe accepts this decision only from the eXe Agent window of the editor that runs it. ...** | A decision came from a different window or editor | Use the eXe Agent window of this editor. Restart the editor if it keeps happening |
| **The local model runs with a context length of ... tokens. eXe needs at least 32768 ...** | Your local server runs the model with a small context | Set a larger context length (Ollama: **Context length** or `OLLAMA_CONTEXT_LENGTH`; LM Studio: the context length the model is loaded with), load the model again, send again |

## Claude Code, Codex and Claude Desktop

### The client does not see eXe

1. In **Settings → AI clients**, click **Connect / repair**, then **Check status**. The status line tells you what is missing ([status table](04_Connect_AI_Providers.md#connect-once)).
2. Close command windows that were already open and restart Claude Desktop.
3. Start Claude Code or Codex with the copied line (**Copy Claude Code command** or **Copy Codex command**) in a new terminal (PowerShell or Command Prompt). Install and sign in to the client yourself.

### The terminal says "eXe is not connected yet" or "... was not found"

See [Start Claude Code or Codex](04_Connect_AI_Providers.md#start-claude-code-or-codex).

### The client reports EXE_PROJECT_MISMATCH

The client reached the eXe of another open project, and eXe refused to do anything there. Click **Connect / repair** in the project you work on, restart Claude Desktop, and copy the start command for Claude Code or Codex again in that project.

### Claude Code or Codex cannot run commands or edit files itself

This is on purpose: the copied start command opens the client with a reduced set of tools, so project changes go through eXe and can be checked and undone ([What the eXe session can do](04_Connect_AI_Providers.md#start-claude-code-or-codex)).

## Builds and C++

### The editor did not reopen after a build

This is expected. eXe never restarts the editor. Wait until the console window **eXe Full Build: Unreal Build Tool is running...** has closed, then open the project yourself. The job then continues.

### The build failed

- For a job's build: open `<YourProject>/Saved/eXe.Loading/LAST_FULL_BUILD.md`. It names the build log and the build command. The first `error` line in the log is the cause ([Full builds](06_Permissions_And_Safety.md#full-builds)).
- For **Build project** in **Tools**: open the project again; the **Tools** view lists the compiler errors.

### "Build cancelled: the editor stayed open, nothing was built."

You clicked **Cancel** when Unreal asked about unsaved work. Nothing was built. Start the build again when you are ready.

### Claude Code lost eXe after a full build

The editor was closed for the build, so Claude Code lost its connection. Open the project again, then type `/mcp` in Claude Code, choose **exe-loading** and click **Reconnect**. The job continues.

### A C++ change is gone after restarting Unreal

The change was made with Live Coding, which only changes the running editor. Close Unreal, build the project in your IDE (Visual Studio or Rider) and open it again ([Live Coding](06_Permissions_And_Safety.md#live-coding)).

### eXe refuses to change C++ files

**Power Write** is off. Turn it on under **Settings → Permissions** if you want eXe to change C++ and other source files ([Power Write](06_Permissions_And_Safety.md#power-write)).

## Jobs and changes

### A job ended with "Goal not independently verified"

eXe did the work but could not confirm the goal with its own read-back, for example a visual change. Check the result in the editor.

### An editor step was interrupted

If the editor closed or crashed during a step, eXe shows **Inspect interrupted step** and repeats nothing automatically. Check the project, then continue or start a new task.

### A change could not be reverted

The row in **Changes** says why: **changed again later**, **no saved copy**, **BASELINE_TOO_LARGE** (file over 64 MB), **result not recorded** or **job still running** ([Changes list](03_Agent_Window.md#changes-list)). Use version control for these cases.

### The job list says "Running 0" while a job runs

Known issue in 1.0.0. The list itself is right.

## How to ask for help

Post in the `#support` channel on [Discord](https://discord.gg/ebW7kKCC25) or write to [exeagent.support@gmail.com](mailto:exeagent.support@gmail.com). Please include:

- eXe Agent version and Unreal Engine version
- AI provider and model, or the AI client you used
- What you did, what you expected and what happened
- For a job: the text from **Copy for support** in **Jobs**
- Relevant lines from the Output Log (filter for `LogPython` and `eXe`)

Do not post API keys or private project content.

Previous: [Remote Access with ChatGPT](07_Remote_Access_ChatGPT.md) · [Documentation Index](INDEX.md) · Next: [Known Issues and Limitations](09_Known_Issues_And_Limitations.md)
