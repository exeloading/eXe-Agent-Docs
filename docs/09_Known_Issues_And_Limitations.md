# Known Issues and Limitations

## Known Issues

- **Jobs counter.** The line above the job list can show **Running 0** while a job in the list is running. The list is right.
- **Play In Editor.** While a game preview that you started is running, eXe's read requests to the editor fail and an error line appears in the Output Log. Stop the preview first.
- **Large Blueprint graphs.** A graph with more than 128 nodes is returned shortened and marked as such. The AI can still read single nodes.
- **Search in very large projects.** A search stops after 8 seconds and then says that its result is incomplete. Narrow the search to a folder or a file type.

Current reports are collected in the `#known-issues` channel on [Discord](https://discord.gg/ebW7kKCC25).

## Known Limitations

- **Windows only.** Version 1.0.0 supports Win64. macOS and Linux are not supported.
- **Unreal Engine 5.8 only.** Version 1.0.0 runs on Unreal Engine 5.8. Support for Unreal Engine 5.9 is planned as a free update after Epic releases 5.9 and Fab accepts it.
- **Experimental Engine features.** eXe relies on Unreal's experimental Model Context Protocol and Toolset Registry. Engine updates may require a plugin update.
- **Editor must be running.** eXe runs inside the Unreal Editor. When the editor is closed, eXe and all AI access to it stop.
- **AI provider needed for AI features.** Planning and executing tasks need an AI provider, a local model or an AI client. Result quality depends on the model. Without one, the **Tools** view still works.
- **C++ changes and Python scripts need Power Write.** While Power Write is off, eXe refuses plans that change source files or run your own Python scripts.
- **Reverting has limits.** eXe can revert files and assets it changed where it kept a saved copy. Saved copies are kept for 14 days; after that a change can no longer be reverted. It keeps no copy of World Partition actor files (One File Per Actor) or of files over 64 MB. Unsaved editor changes and files changed by someone else afterwards are not reverted. Use version control.
- **Reopen after builds.** eXe never restarts the editor. After every full build, successful or not, you open the project again.
- **Optional clients.** Claude Code, Codex and Claude Desktop are installed, signed in and started by you. eXe copies the start command but never runs it.
- **ChatGPT access** needs a ChatGPT plan with connector support, a tunnel that you run yourself and sign-in (OAuth). Access without sign-in is not supported in 1.0.
- **No proxy for the built-in chat.** The eXe chat and asset generation connect to the provider directly and do not use a system proxy. In a network that reaches the internet only through a proxy, use Claude Code or Codex instead.
- **Changes outside eXe.** Changes made by an AI client with its own tools, or through a direct connection to Unreal's MCP server, are not checked, approved or revertible by eXe.
- **Not every Unreal task is covered.** Creating a new level, building lighting and packaging the game are not eXe steps in 1.0; do them in Unreal yourself.
- **Edit → Undo does not cover eXe.** eXe's changes are not entries in the editor's undo history. Revert them in **Changes** or **Jobs**.
- **Files under source control.** eXe does not check files out. A read-only file, for example a Perforce file that is not checked out, cannot be saved. Check out the files a plan names before you approve it.
- **Menu names.** This documentation uses the English editor menus. In a translated editor the menus have translated names.
- **Some texts are always English.** Replies come in English unless you change **eXe replies in** under **Settings → General**. Plan headings exist only in English and German, and some detail messages from the eXe core (tooltips, error reasons) are always in English.
- **Local models only on this PC.** The eXe chat accepts a local model server only at `127.0.0.1` or `localhost`, not on another computer.

Previous: [Troubleshooting](08_Troubleshooting_And_FAQ.md) · [Documentation Index](INDEX.md) · Next: [Changelog](10_Changelog.md)
