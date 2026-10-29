# Known Issues and Limitations

## Known Issues

No known issues are recorded for version 1.0.0. Current reports are collected in the `#known-issues` channel on [Discord](https://discord.gg/ebW7kKCC25).

## Known Limitations

- **Windows only.** Version 1.0.0 supports Win64. macOS and Linux are not supported.
- **Unreal Engine 5.8 only.** Other engine versions are not tested.
- **Experimental Engine features.** eXe relies on Unreal's experimental Model Context Protocol and Toolset Registry. Engine updates may require a plugin update.
- **Editor must be running.** eXe runs inside the Unreal Editor. When the editor is closed, eXe and all AI access to it stop.
- **AI provider needed for AI features.** Planning and executing tasks need an AI provider, a local model or an AI client. Result quality depends on the model. Without one, the **Tools** view still works.
- **C++ changes need Power Write.** While Power Write is off, eXe refuses plans that change source files.
- **Reverting has limits.** eXe can revert files and assets it changed where it kept a saved copy. Unsaved editor changes and files changed by someone else afterwards are not reverted. Use version control.
- **Reopen after builds.** eXe never restarts the editor. After every full build, successful or not, you open the project again.
- **Optional clients.** Claude Code, Codex and Claude Desktop are installed, signed in and started by you. eXe copies the start command but never runs it.
- **ChatGPT access** needs a ChatGPT plan with connector support and a tunnel that you run yourself.
- **Changes outside eXe.** Changes made by an AI client with its own tools, or through a direct connection to Unreal's MCP server, are not checked, approved or revertible by eXe.
- **Not every Unreal task is covered.** When eXe has no capability for a task, it says so.

Previous: [Troubleshooting and FAQ](08_Troubleshooting_And_FAQ.md) · [Documentation Index](INDEX.md) · Next: [Changelog](10_Changelog.md)
