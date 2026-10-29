# eXe Agent

eXe Agent is an AI development assistant inside the Unreal Editor. It reads your project, proposes a plan, works only inside the plan you approve and checks the result in the editor before it reports success. You bring your own AI provider or local model. There is no eXe account, no eXe cloud and no subscription.

```text
Version: 1.0.0
Unreal Engine: 5.8 (tested with 5.8.3)
Plugin type: Editor-only code plugin with an embedded Python core
Supported platform: Win64
Publisher: eXe.Loading
```

## What you can do with it

- **Ask about your project.** eXe reads Blueprints, C++, assets, levels and settings of the open project and answers in the chat.
- **Plan before anything changes.** A change starts as a plan with exact targets. Nothing is written until you approve that plan.
- **Let it do the work.** After approval, eXe edits Blueprints, assets, levels and (with Power Write) C++ source, saves, compiles and repairs failed steps inside the approved scope.
- **See what was proven.** Every job ends with a result level, for example **Goal verified** when eXe read the changed values back from the editor.
- **Review and undo changes.** Finished jobs list the files and assets they changed, with diff, keep and revert.
- **Use the AI you already have.** Chat inside Unreal with your own OpenAI, Anthropic, Gemini or DeepSeek key or a local model, or connect Claude Code, Codex, Claude Desktop or ChatGPT.
- **Useful without any AI provider.** The **Tools** view checks assets, finds stacked actors, explains a Blueprint, lists dependencies and builds the project.

## Requirements

- Windows 64-bit
- Unreal Engine 5.8 with the Engine plugins listed in [Installation](docs/01_Installation.md)
- For AI features: your own API key, a local model or an official AI client. Usage is billed by that provider, not by eXe.

## Quick start

1. Install eXe Agent from the Fab Library to Unreal Engine 5.8, enable it in **Edit → Plugins** and restart the editor.
2. Make sure Unreal's MCP server runs: **Editor Preferences → Model Context Protocol → Auto Start Server**.
3. Open eXe Agent with the **eXe Agent** toolbar button, **Window → eXe Agent** or **Ctrl+Shift+Space**.
4. In **Chat**, click **Connect an AI controller**, choose a provider, enter a model ID and your key, click **Save** and ask: `Give me a short overview of this project.`

Full walkthrough: [Quick Start](docs/02_Quick_Start.md)

## Documentation

- [Documentation Index](docs/INDEX.md)
- [Installation](docs/01_Installation.md)
- [Quick Start](docs/02_Quick_Start.md)
- [The eXe Agent Window](docs/03_Agent_Window.md)
- [Connect AI Providers](docs/04_Connect_AI_Providers.md)
- [Capabilities](docs/05_Capabilities.md)
- [Permissions and Safety](docs/06_Permissions_And_Safety.md)
- [Remote Access with ChatGPT](docs/07_Remote_Access_ChatGPT.md)
- [Troubleshooting and FAQ](docs/08_Troubleshooting_And_FAQ.md)
- [Known Issues and Limitations](docs/09_Known_Issues_And_Limitations.md)
- [Changelog](docs/10_Changelog.md)
- [Privacy, Costs and Third-Party Software](docs/11_Privacy_Costs_And_Third_Party.md)

## Good to know

- eXe Agent depends on experimental Unreal Engine 5.8 features (Model Context Protocol, Toolset Registry). A future engine version may require a plugin update.
- eXe runs inside the Unreal Editor. When the editor is closed, eXe is not running.
- eXe never restarts the editor and never starts AI clients or other programs for you. The only program it can start is Unreal Build Tool from your own Engine, for a build you allowed.
- AI results depend on the provider and model you choose. eXe reports what it could verify and does not claim success it could not check.

## Support

- Discord: [eXe Agent Discord](https://discord.gg/ebW7kKCC25) for questions, bug reports and feature requests
- Email: [exeagent.support@gmail.com](mailto:exeagent.support@gmail.com)

## License

eXe Agent is sold on Fab under the Fab Standard License. Third-party components and their licenses are listed in `Resources/THIRD_PARTY_NOTICES.md` inside the plugin.

Copyright (c) 2026 eXe.Loading. All rights reserved.
