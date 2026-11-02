# Known Issues and Limitations

## Known Issues

- **Plan check without the Unreal MCP server.** If Unreal's MCP server is not running when the AI submits a plan, the plan check fails with a technical message (`WinError 10061`) instead of a plain hint. Start the server ([Troubleshooting](08_Troubleshooting_And_FAQ.md#unreal-mcp-server-not-running)) and submit the plan again.

New reports are collected in the `#known-issues` channel on [Discord](https://discord.gg/ebW7kKCC25).

## Known Limitations

- **Windows only.** Version 1.0.0 supports Win64. macOS and Linux are not supported.
- **Unreal Engine 5.8 only.** Other engine versions are not tested.
- **Experimental Engine features.** eXe relies on Unreal's experimental Model Context Protocol and Toolset Registry. Engine updates may require a plugin update.
- **Editor must be running.** eXe runs inside the Unreal Editor. When the editor is closed, eXe and all AI access to it stop.
- **AI provider needed for AI features.** Planning and executing tasks need an AI provider, a local model or an AI client. Result quality depends on the model. Without one, the **Tools** view still works.
- **Anthropic not tested live.** The Anthropic chat connection follows Anthropic's API documentation but was not tested against the live service for version 1.0.0. Please report problems on Discord.
- **Some messages in English.** The interface is translated into 7 languages. Detail messages from the eXe Core, such as setup steps in tooltips and error reasons, are in English.
- **C++ changes need Power Write.** While Power Write is off, eXe refuses plans that change source files.
- **Reverting has limits.** eXe can revert files and assets it changed where it kept a saved copy. Unsaved editor changes and files changed by someone else afterwards are not reverted. Use version control.
- **Reopen after builds.** eXe never restarts the editor. After every full build, successful or not, you open the project again.
- **Optional clients.** Claude Code, Codex and Claude Desktop are installed, signed in and started by you. eXe copies the start command but never runs it.
- **ChatGPT access** needs a ChatGPT plan with connector support and a tunnel that you run yourself.
- **Blender and your own MCP servers.** The Blender add-on **MCP for Blender** is not included; you install it in Blender yourself. Tools from your own MCP servers run in Claude Code or Codex outside eXe's plans, so eXe cannot check or undo what they do. Only addresses on this PC are accepted, at most 8 servers.
- **Changes outside eXe.** Changes made by an AI client with its own tools, or through a direct connection to Unreal's MCP server, are not checked, approved or revertible by eXe.
- **Not every Unreal task is covered.** When eXe has no capability for a task, it says so.

Previous: [Troubleshooting and FAQ](08_Troubleshooting_And_FAQ.md) · [Documentation Index](INDEX.md) · Next: [Changelog](10_Changelog.md)
