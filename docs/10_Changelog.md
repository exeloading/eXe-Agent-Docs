# Changelog

## eXe Agent v1.0.0

**Release summary**
First public release for Unreal Engine 5.8. eXe Agent lets you plan, approve, execute and verify Unreal development tasks with your own AI provider, directly in the editor.

**Added**
- One **eXe Agent** window with **Chat**, **Jobs**, **Tools** and **Settings**, opened from the toolbar, **Window → eXe Agent** or **Ctrl+Shift+Space**.
- Chat in the editor with OpenAI, Anthropic, Gemini, DeepSeek or a local model, with image attachments, selection insert, voice input and Markdown export.
- Plan, approve, execute and verify workflow with sealed scope and six result levels.
- Changes list with diff, keep and revert, and undo per job.
- Editing of Blueprints, assets, materials, UMG, animation, gameplay systems, levels, audio, VFX and world assets after approval; C++ editing with Power Write.
- Full project builds through Unreal Build Tool. eXe closes the editor; you open the project again after the build.
- Play in Editor tests with screenshots after game steps, including multiplayer runs.
- **Tools** view without an AI provider: asset checks, level check, Blueprint explanation, dependencies, clean-up report and project build.
- Connection for Claude Code, Codex and Claude Desktop (eXe copies the start command, you run it) and MCP access for local clients.
- Optional remote access from ChatGPT through your own tunnel, with optional sign-in.
- Optional asset generation with your own key (Meshy, Tripo, OpenAI, Stability AI, ElevenLabs) or your own local server.
- Power Write and YOLO switches, project rules, Auto Save.
- Interface in English, German, Japanese, Simplified Chinese, Korean, Spanish and French; separate reply language.
- Built-in skill guides for common Unreal workflows.

**Compatibility**
- Unreal Engine 5.8, Win64, Editor-only.
- Requires the Engine plugins listed in [Installation](01_Installation.md).

**Known limitations**
- See [Known Issues and Limitations](09_Known_Issues_And_Limitations.md).

Previous: [Known Issues and Limitations](09_Known_Issues_And_Limitations.md) · [Documentation Index](INDEX.md) · Next: [Privacy, Costs and Third-Party Software](11_Privacy_Costs_And_Third_Party.md)
