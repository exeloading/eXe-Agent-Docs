# Quick Start

In about ten minutes you get a first answer about your project and make a first small, approved change.

## Before you start

- eXe Agent is installed and enabled, and Unreal's MCP server is running ([Installation](01_Installation.md)).
- You have an API key from OpenAI, Anthropic, Google Gemini or DeepSeek, or a local model with an OpenAI-compatible endpoint. If you prefer Claude Code, Codex or Claude Desktop, see [Connect AI Providers](04_Connect_AI_Providers.md).
- Use a test project or a copy of your project for your first change.

## Part 1: Ask about your project

1. Open the **eXe Agent** window (toolbar button, **Window → eXe Agent** or **Ctrl+Shift+Space**). It opens on **Chat**.
2. Click **Connect an AI controller**. Choose the provider, enter the model ID exactly as your provider lists it and enter your API key. Click **Save**.
3. Type `Give me a short overview of this project: modules, main Blueprints and game mode.` and press **Enter** (or click **Send**).

Expected result: eXe answers with an overview based on your actual project. Nothing in the project changes.

## Part 2: Make an approved change

1. Pick a Blueprint you can safely change, for example a test actor with a numeric variable.
2. In the chat, type: `In BP_TestActor, change the default value of Health to 150.` Use your own Blueprint and variable name.
3. eXe reads the project and writes a plan. Below the reply you see **The plan above is ready for your approval**.
4. Read the plan: target asset, expected change, what must not change.
5. Click **Approve plan**. To review the full plan with all details first, click **Details in Jobs**.
6. eXe applies the change, saves the asset and reads the value back. The chat shows the progress.

Expected result: the job ends with **Goal verified**. Open the Blueprint: the default value is 150. Above the chat input, the changes list shows the changed asset with **Keep** and **Revert**.

## Part 3: Try the tools without AI

1. In the eXe Agent window, switch to **Tools**.
2. Select one Blueprint in the Content Browser and click **Explain Blueprint**.

Expected result: a summary of components, variables, functions and what each graph calls. No AI provider is used and nothing changes.

## Next steps

- Learn the window and the job lifecycle: [The eXe Agent Window](03_Agent_Window.md)
- Decide how much eXe may do on its own: [Permissions and Safety](06_Permissions_And_Safety.md)

Previous: [Installation](01_Installation.md) · [Documentation Index](INDEX.md) · Next: [The eXe Agent Window](03_Agent_Window.md)
