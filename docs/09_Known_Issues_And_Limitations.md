# Known Issues and Limitations

## Known Issues

- **Jobs counter.** The line above the job list can show **Running 0** while a job in the list is running. The list is right.
- **Play In Editor.** While a game preview that you started is running, eXe's read requests to the editor fail and an error line appears in the Output Log. Stop the preview first.
- **Large Blueprint graphs.** A graph with more than 128 nodes is returned shortened and marked as such. The AI can still read single nodes.
- **Search in very large projects.** A search stops after 8 seconds and then says that its result is incomplete. Narrow the search to a folder or a file type.

Current reports are collected in the `#known-issues` channel on [Discord](https://discord.gg/ebW7kKCC25).

## Known Limitations

- **Windows only.** Version 1.0.0 supports Win64. macOS and Linux are not supported.
- **Unreal Engine 5.8 only.** Other engine versions are not tested.
- **Experimental Engine features.** eXe relies on Unreal's experimental Model Context Protocol and Toolset Registry. Engine updates may require a plugin update.
- **Editor must be running.** eXe runs inside the Unreal Editor. When the editor is closed, eXe and all AI access to it stop.
- **AI provider needed for AI features.** Planning and executing tasks need an AI provider, a local model or an AI client. Result quality depends on the model. Without one, the **Tools** view still works.
- **C++ changes and Python scripts need Power Write.** While Power Write is off, eXe refuses plans that change source files or run your own Python scripts.
- **Reverting has limits.** eXe can revert files and assets it changed where it kept a saved copy. Saved copies are kept for 14 days; after that a change stays listed but can no longer be reverted. It keeps no copy of World Partition actor files (One File Per Actor) or of files over 64 MB. Unsaved editor changes and files changed by someone else afterwards are not reverted. Use version control.
- **Reopen after builds.** eXe never restarts the editor. After every full build, successful or not, you open the project again.
- **Optional clients.** Claude Code, Codex and Claude Desktop are installed, signed in and started by you. eXe copies the start command but never runs it.
- **ChatGPT access** needs a ChatGPT plan with connector support, a tunnel that you run yourself and sign-in (OAuth). Access without sign-in is not supported in 1.0.
- **Changes outside eXe.** Changes made by an AI client with its own tools, or through a direct connection to Unreal's MCP server, are not checked, approved or revertible by eXe.
- **Not every Unreal task is covered.** When eXe has no capability for a task, it says so.

Previous: [Troubleshooting and FAQ](08_Troubleshooting_And_FAQ.md) · [Documentation Index](INDEX.md) · Next: [Changelog](10_Changelog.md)
