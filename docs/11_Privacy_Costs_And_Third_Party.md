# Privacy, Costs and Third-Party Software

## No eXe cloud

eXe Agent runs on your PC inside the Unreal Editor. There is no eXe account, no eXe server and no telemetry to the eXe developer. eXe sends nothing to the internet unless you configure a cloud AI provider, a tunnel or another service listed below.

All eXe network endpoints listen on `127.0.0.1` only (by default ports 8798 to 8800 and 47861). Nothing listens on an external network interface.

## What is sent where

| You use... | Data that leaves your PC | Goes to |
|---|---|---|
| **Tools** view | Nothing | Nobody |
| Chat with a cloud provider | Your messages, attached images, and the project information the AI requests (file contents, asset data, logs) | The provider you chose (OpenAI, Anthropic, Google Gemini, DeepSeek or an endpoint you enter), under their terms |
| Voice input | The recording (up to 60 seconds), once, to be turned into text; eXe does not keep it | OpenAI or Google Gemini with your key |
| Chat with a local model | Nothing, if your model runs on your PC | Your local model |
| Claude Code, Codex, Claude Desktop | What that client sends to its provider | Anthropic or OpenAI under your account |
| ChatGPT remote access | Requests and answers through your tunnel | Your tunnel provider, your sign-in service and OpenAI |
| Asset generation | Your description, and for image to 3D the source image; eXe asks before each request | The service you chose (Meshy, Tripo, OpenAI, Stability AI, ElevenLabs) or your local server |
| Bundled VibeUE tools with online features | Only when an AI calls such a tool, for example a web search query | The services listed in `Resources/THIRD_PARTY_NOTICES.md` |

Check your provider's data policy before you send confidential project content.

## Costs

- **eXe Agent:** one-time price on Fab. No subscription.
- **AI usage:** billed by your AI provider under your own account. The chat shows the token usage your provider reports.
- **Asset generation:** billed by the service you chose under your own account.
- **Tunnel and sign-in services** for remote access: billed by those services if they are not free.

## Local storage

- Project data (jobs, chats, settings, backups): `<YourProject>/Saved/eXe.Loading`
- API keys: Windows Credential Manager, for your Windows user
- Power Write and YOLO: a settings file of your Windows user

## Third-party software

eXe Agent includes third-party components, among them VibeUE (MIT license) and Python packages. The complete lists with licenses are in the plugin folder:

- `Resources/THIRD_PARTY_NOTICES.md`
- `Resources/THIRD_PARTY_SOFTWARE.json`
- `Resources/EXPERIMENTAL_DEPENDENCIES.md`

Unreal Engine plugins that eXe uses are part of your Engine installation and are not redistributed.

Previous: [Changelog](10_Changelog.md) · [Documentation Index](INDEX.md)
