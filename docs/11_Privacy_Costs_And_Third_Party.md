# Privacy, Costs and Third-Party Software

## No eXe cloud

eXe Agent runs on your PC inside the Unreal Editor. There is no eXe account, no eXe server and no telemetry to the eXe developer. eXe sends nothing to the internet unless you configure a cloud AI provider, a tunnel or another service listed below.

All eXe network endpoints listen on `127.0.0.1` only (by default ports 8798 to 8800 and 47861). Nothing listens on an external network interface.

## What is sent where

| You use... | Data that leaves your PC | Goes to |
|---|---|---|
| **Tools** view | Nothing | Nobody |
| Blender | Nothing. eXe talks only to the Blender add-on on your PC (`127.0.0.1`, port 9876) | Nobody |
| Chat with a cloud provider | Your messages, attached images, and the project information the AI requests (file contents, asset data, logs) | The provider you chose (OpenAI, Anthropic, Google Gemini or DeepSeek), under their terms |
| Chat with a local model | Nothing, if your model runs on your PC | Your local model |
| Claude Code, Codex, Claude Desktop | What that client sends to its provider. Claude Desktop also downloads the npm package `mcp-remote` to reach eXe | Anthropic or OpenAI under your account; the npm registry (registry.npmjs.org) |
| ChatGPT remote access | Requests and answers through your tunnel | Your tunnel provider, your sign-in service and OpenAI |
| Asset generation | Your description; eXe asks before each request. The finished file is downloaded from the address the service returns | The service you chose (Meshy, Tripo, OpenAI, Stability AI, ElevenLabs) or your local server |

Check your provider's data policy before you send confidential project content.

## Costs

- **eXe Agent:** one-time price on Fab. No subscription.
- **AI usage:** billed by your AI provider under your own account. The chat shows the token usage your provider reports.
- **Asset generation:** billed by the service you chose under your own account.
- **Tunnel and sign-in services** for remote access: billed by those services if they are not free.

## Local storage

- Project data (jobs, chats, settings, backups): `<YourProject>/Saved/eXe.Loading`
- eXe documents (plan copies, notes, decisions, project rules): `<YourProject>/ProjectDocs/eXe`, only when eXe saves something there. eXe refuses to save keys in this folder.
- API keys: Windows Credential Manager, for your Windows user. The entries are named `eXe.Loading/NativeChat/...` (chat) and `eXe.Loading/AssetGeneration/...` (asset generation).
- Power Write, YOLO, **Plan before changes** and your own MCP servers: settings files of your Windows user under `%LOCALAPPDATA%\eXe.Loading`

Full list and how to remove everything: [Installation](01_Installation.md#where-exe-stores-data).

## Third-party software

eXe Agent includes third-party components, among them VibeUE (MIT license) and Python packages. The complete lists with licenses are in the plugin folder:

- `Resources/THIRD_PARTY_NOTICES.md`
- `Resources/THIRD_PARTY_SOFTWARE.json`
- `Resources/EXPERIMENTAL_DEPENDENCIES.md`

Unreal Engine plugins that eXe uses are part of your Engine installation and are not redistributed.

Previous: [Changelog](10_Changelog.md) · [Documentation Index](INDEX.md) · Next: [FAQ](12_FAQ.md)
