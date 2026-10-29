# Installation

This page explains how to install, enable, check, update and remove eXe Agent.

## Requirements

- Windows 64-bit
- Unreal Engine 5.8 (tested with 5.8.3)
- A Blueprint or C++ project. C++ editing and full builds need a project with C++ source code.
- These Engine plugins are required and are enabled together with eXe Agent. All of them ship with Unreal Engine 5.8:

| Plugin (internal name) | Note |
|---|---|
| `PythonScriptPlugin` | Python Editor Script Plugin; hosts the eXe core |
| `ModelContextProtocol` | Unreal's MCP server (experimental) |
| `ToolsetRegistry` | Unreal's toolsets (experimental) |
| `EditorScriptingUtilities`, `EnhancedInput`, `Niagara`, `MeshModelingToolset`, `ModelViewViewModel`, `StateTree`, `MetaSound`, `GameplayTagsEditor` | Used by eXe's Unreal tools |

- Optional Engine plugins: `LiveCodingToolset`, `AllToolsets`, `Fab`, `EOSShared`. eXe works without them; some tools are only available when they are enabled.

eXe Agent does not copy, replace or redistribute any Engine files.

## Install from Fab

1. Close the Unreal Editor.
2. In the Epic Games Launcher, open **Fab Library**, find **eXe Agent** and click **Install to Engine**. Choose Unreal Engine 5.8.
3. Open your project.
4. Go to **Edit → Plugins**, search for **eXe Agent** and enable it. Accept the Engine plugin dependencies.
5. Restart the editor when Unreal asks you to.

Do not install separate VibeUE or ExeLoadingMcpToolset plugins next to eXe Agent. Both are already included.

## Start Unreal's MCP server

eXe works in the editor through Unreal's built-in Model Context Protocol (MCP) server. Its automatic start can be off by default.

1. Open **Edit → Editor Preferences** and find **Model Context Protocol**.
2. Enable **Auto Start Server**.
3. To start the server right away without a restart, run the console command `ModelContextProtocol.StartServer`.

Keep the default local address `http://127.0.0.1:8000/mcp` unless you have a reason to change it. Never expose local ports to the internet.

## Open eXe Agent and check that it works

Open the **eXe Agent** window in one of three ways:

- the **eXe Agent** button in the level editor toolbar (the arrow next to it opens a view directly)
- **Window → eXe Agent**
- **Ctrl+Shift+Space** (you can change it under **Editor Preferences → Keyboard Shortcuts**)

The header of the window shows your project name and the connection state. Expected: **Connected**.

For details, open **Settings → Connection**. Expected:

- **eXe Core: running**
- **Project link: active**
- **Editor: connected**
- **Unreal MCP:** server running

If a line looks different, hover over the **Unreal MCP** line for the next steps or see [Troubleshooting](08_Troubleshooting_And_FAQ.md).

## Where eXe stores data

- Jobs, plans, results, settings and backups of a project: `<YourProject>/Saved/eXe.Loading`
- Chats of a project are kept with that project.
- API keys: saved for your Windows user in Windows Credential Manager, never in the project folder.
- Project rules (optional): `<YourProject>/ProjectDocs/eXe/Rules`

eXe starts with the editor and stops when the editor closes. Nothing keeps running in the background.

## Update

Fab updates arrive through the Epic Games Launcher. Close the editor before updating. Your project data in `Saved/eXe.Loading` is kept.

## Remove

1. Optional, before disabling: remove saved API keys. In **Chat**, open the AI controller and click **Remove saved key**.
2. Disable **eXe Agent** in **Edit → Plugins** and restart the editor.
3. Optional: delete `<YourProject>/Saved/eXe.Loading` to remove all eXe jobs, chats and settings of that project.
4. Optional: if you connected Claude Code, Codex or Claude Desktop, click **Revoke token** under **Settings → AI clients** before you disable the plugin, or remove the `exe-loading` entry from the client's MCP configuration yourself.

## Do not

- Do not run `pip install` or upgrade Python packages to fix an import error. eXe ships its own pinned Python packages. See [Troubleshooting](08_Troubleshooting_And_FAQ.md).
- Do not run a separate eXe server or a second copy of the plugin for the same project.

Previous: [Documentation Index](INDEX.md) · Next: [Quick Start](02_Quick_Start.md)
