# Installation

This page explains how to install eXe Agent, check that it works, update it and remove it. It takes you step by step through every setting you need. Words you may not know are explained in the [Glossary](13_Glossary.md).

## Requirements

- Windows 64-bit
- Unreal Engine 5.8 (tested with 5.8.3)
- A Blueprint project or a C++ project
- For C++ changes and builds only: the Visual Studio C++ tools and the Windows SDK that Unreal Engine 5.8 requires. Blueprint, asset and level work does not need them.
- For AI features: your own API key, a local model on your PC, or an official AI client such as Claude Code or Codex. Without any AI, the **Tools** view still works.

You do **not** need to install Python. eXe uses the Python that comes with Unreal Engine.

### Engine plugins eXe needs

These Engine plugins ship with Unreal Engine 5.8. They are switched on together with eXe Agent; you do not install anything extra.

| Plugin (internal name) | What it is for |
|---|---|
| `PythonScriptPlugin` | Python Editor Script Plugin; runs the eXe core inside the editor |
| `ModelContextProtocol` | Unreal's MCP server (experimental); the way eXe works in the editor |
| `ToolsetRegistry` | Unreal's toolsets (experimental); the editor tools eXe calls |
| `EditorScriptingUtilities`, `EnhancedInput`, `Niagara`, `MeshModelingToolset`, `ModelViewViewModel`, `StateTree`, `MetaSound`, `GameplayTagsEditor` | Used by eXe's Unreal tools |

Optional Engine plugins: `LiveCodingToolset` and `AllToolsets`. eXe works without them; some tools are only available when they are on.

eXe Agent does not copy, replace or redistribute any Engine files.

### Names you may see

The product is called **eXe Agent**. You may also see these names. They all mean the same plugin:

| Name | Where you see it |
|---|---|
| **eXe Agent** | **Edit → Plugins**, the toolbar button and the window title |
| `ExeLoadingBridge` | The plugin folder on disk |
| **eXe.Loading** | The publisher, and folder names such as `Saved/eXe.Loading` |
| **eXe.Loading plugin**, **VibeUE plugin** | Some help texts. VibeUE is a part of eXe Agent, not a separate plugin. When a help text asks you to enable one of them, check that **eXe Agent** is enabled. |

## Step 1: Install from Fab

1. Close the Unreal Editor.
2. Open the Epic Games Launcher, go to **Fab Library**, find **eXe Agent** and click **Install to Engine**. Choose Unreal Engine 5.8.
3. Open your project.
4. Go to **Edit → Plugins**, type `eXe Agent` into the search box and make sure it is enabled. Accept the Engine plugin dependencies if Unreal asks. If eXe Agent is already enabled, skip to Step 2.
5. Restart the editor when Unreal asks you to.

Do not install separate VibeUE or ExeLoadingMcpToolset plugins next to eXe Agent. Both are already included.

## Step 2: Start Unreal's MCP server

eXe works in the editor through Unreal's built-in **Model Context Protocol (MCP)** server. Unreal ships with this server, but its automatic start can be off. You set this once per project.

1. Open **Edit → Editor Preferences**.
2. Type `Model Context Protocol` into the search box at the top.
3. Turn on **Auto Start Server**.
4. To start the server right away without a restart: open **Window → Output Log**, type `ModelContextProtocol.StartServer` into the **Cmd** field at the bottom and press **Enter**.

Keep the default address `http://127.0.0.1:8000/mcp` unless you have a reason to change it. Never make local ports reachable from the internet.

**Working on two projects at the same time?** Each open project needs its own MCP port. In the second project, open the same settings, set **Server Port Number** to a free port, for example `8001`, keep **Auto Start Server** on and restart that editor.

## Step 3: Open eXe Agent and check that it works

Open the **eXe Agent** window in one of three ways:

- the **eXe Agent** button in the level editor toolbar (the arrow next to it opens a view directly)
- **Window → eXe Agent**
- **Ctrl+Shift+Space** (you can change it under **Editor Preferences → Keyboard Shortcuts**)

The header of the window shows your project name, a colored dot and the state of eXe. When everything works, you see a **green dot** and **eXe running**.

| Dot | Header text | Meaning |
|---|---|---|
| Green | **eXe running** | Everything is ready |
| Accent color (blue by default) | **eXe running · n job(s) running** | eXe is working on a job |
| Yellow | **eXe running · Unreal MCP is off, see Settings** or **eXe running · check Unreal MCP in Settings** | Unreal's MCP server is not usable yet. See Step 2 or [Troubleshooting](08_Troubleshooting_And_FAQ.md) |
| Yellow | **eXe running, no project** | eXe is not connected to the open project yet. Wait a moment; if it stays, restart the editor |
| Text color (white in the dark theme) | **Starting...** or **Reconnecting...** | eXe is starting or briefly not answering. Wait a few seconds |
| Red | **eXe could not start · see Settings** | Open **Settings → Connection**, read the reason and see [Troubleshooting](08_Troubleshooting_And_FAQ.md) |

For more detail, open **Settings → Connection**. When everything works, it shows:

- **eXe Core: running**
- **Project link: active**
- **Editor: connected**
- **Unreal MCP: running at** followed by the address

If a line looks different, hover over the **Unreal MCP** line to see the next steps for your case.

Next: [Quick Start](02_Quick_Start.md) for your first answer and your first change.

## Where eXe stores data

eXe starts with the editor and stops when the editor closes. Nothing keeps running in the background.

| What | Where | Applies to |
|---|---|---|
| Jobs, plans, results, chats, backups, the chosen AI controller and project settings | `<YourProject>/Saved/eXe.Loading` | This project |
| Power Write, YOLO, **Plan before changes**, your own MCP servers | `%LOCALAPPDATA%\eXe.Loading` | All your projects (your Windows user) |
| API keys | Windows Credential Manager, entries that start with `eXe.Loading/` | Your Windows user, never the project folder |
| eXe workspace for Claude Code and Codex (start file and workflow guides) | `%LOCALAPPDATA%\eXe.Loading\CLI\workspaces` | One folder per project |
| eXe documents: plan copies, notes, decisions and project rules | `<YourProject>/ProjectDocs/eXe` (created when eXe saves something there or you click **Copy rules folder path**) | This project |

After **Connect / repair** for AI clients, eXe also sets two Windows user environment variables, `EXE_LOADING_LOCAL_TOKEN` and `EXE_LOADING_LOCAL_AUTH_HEADER`, and writes an `exe-loading` entry into the configuration of Claude Code, Codex and Claude Desktop. **Revoke token** removes the variables and makes the key invalid; the entry itself stays until you remove it.

### Should I put these folders in version control?

- `Saved/` is not meant for version control. Unreal's usual ignore rules already leave it out.
- `ProjectDocs/eXe` contains only Markdown files, and eXe refuses to save keys there. Commit `ProjectDocs/eXe/Rules` if your team should share the same project rules. Plans, notes and decisions are your choice: commit them to keep a record, or add them to your ignore file.

## Update

Fab updates arrive through the Epic Games Launcher. Close the editor before you update. Your project data in `Saved/eXe.Loading` is kept.

## Remove

1. Optional, before you disable the plugin: remove saved API keys. In **Chat**, open the AI controller and click **Remove saved key**; it removes the key of the provider saved for this project. For another provider, choose it, leave the key field blank, click **Save** and then **Remove saved key**. To remove a key for asset generation, open **Settings → Asset generation**, choose the provider, leave the key field empty and click **Save key**.
2. Optional: if you connected Claude Code, Codex or Claude Desktop, click **Revoke token** under **Settings → AI clients**, or remove the `exe-loading` entry from the client's MCP configuration yourself.
3. Disable **eXe Agent** in **Edit → Plugins** and restart the editor.
4. Optional: delete `<YourProject>/Saved/eXe.Loading` to remove all eXe jobs, chats and settings of that project, `<YourProject>/ProjectDocs/eXe` to remove eXe's documents, and `%LOCALAPPDATA%\eXe.Loading` to remove the settings for all your projects. Keys left in Windows Credential Manager can be removed there; their names start with `eXe.Loading/`.

## Do not

- Do not run `pip install` or upgrade Python packages to fix an import error. eXe ships its own pinned Python packages. See [Troubleshooting](08_Troubleshooting_And_FAQ.md).
- Do not run a separate eXe server or a second copy of the plugin for the same project.

Previous: [Documentation Index](INDEX.md) · Next: [Quick Start](02_Quick_Start.md)
