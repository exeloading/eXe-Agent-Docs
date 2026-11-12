# Quick Start

On this page you get a first answer about your project, make a first small change and try the tools that work without AI.

## Before you start

- eXe Agent is installed and enabled, and Unreal's MCP server runs ([Installation](01_Installation.md), Steps 1 to 3). The header of the eXe Agent window shows a green dot and **eXe running**.
- Use a test project or a copy of your project for your first change.
- You need one way to reach an AI. Pick one:

| You have... | Do this |
|---|---|
| An API key from OpenAI, Anthropic, Google Gemini or DeepSeek | Follow this page |
| A local model on your PC (for example Ollama or LM Studio) | Follow this page and choose **Local model**. Read [Local models](04_Connect_AI_Providers.md#local-models) first |
| A Claude or ChatGPT subscription and Claude Code or Codex installed, but no API key | Follow [Option 2 in Connect AI Providers](04_Connect_AI_Providers.md#option-2-claude-code-codex-or-claude-desktop), then come back to Part 2 |
| No AI at all | Skip to [Part 3](#part-3-try-the-tools-without-ai) |

### Get an API key

An API key is a password that lets eXe use an AI provider on your account. A chat subscription such as ChatGPT Plus or Claude Pro is **not** an API key; API use is billed separately by the provider.

1. Open the developer website of your provider and sign in: [OpenAI](https://platform.openai.com), [Anthropic](https://console.anthropic.com), [Google AI Studio](https://aistudio.google.com) (Gemini) or [DeepSeek](https://platform.deepseek.com).
2. Set up billing or buy credit there. Without credit, the provider refuses requests and the chat says that there is a rate limit or no credit left.
3. Create an API key and copy it. Keep it private.

eXe saves the key in Windows Credential Manager for your Windows user, never in the project.

## Part 1: Ask about your project

1. Open the **eXe Agent** window (toolbar button, **Window → eXe Agent** or **Ctrl+Shift+Space**). It opens on **Chat** and asks **What should eXe Agent do?**
2. Click **Connect an AI controller**.
3. In the first field, choose your provider (the list starts on **Local model**).
4. Enter the **model ID** exactly as your provider lists it, without spaces. The field shows an example for the chosen provider. Examples of the form, not recommendations:

   | Provider | Example of a model ID |
   |---|---|
   | Anthropic | `claude-sonnet-5-5` |
   | OpenAI | `gpt-6.1-sol` |
   | Gemini | `gemini-3.8-flash` |
   | DeepSeek | `deepseek-flash` |
   | Local model (Ollama) | `qwen3:8b` |

   A display name such as `Claude Sonnet 5.5` is not a model ID and is rejected. Check your provider's model list for current models; eXe needs a model that handles tool calls reliably.
5. Paste your API key. Leave **Chat length** at **200k tokens · recommended**.
6. Click **Save**.
7. Type a narrow question, for example `Give me a short overview of this project: modules, main Blueprints and game mode.`, and press **Enter**.

Expected result: eXe answers with an overview based on your actual project. Nothing in the project changes. While eXe works, the chat shows lines such as **Thinking...** and **Working in the editor · reading the project**.

Good to know:

- Answers come in **English** unless you change it under **Settings → General → eXe replies in**. Choose **Automatic (language of your message)** to get answers in the language you write in.
- Broad requests such as `Analyze this project and suggest the most useful improvements` read a large part of the project and use more tokens than a narrow question. The line below the chat shows the tokens your provider reported ([Costs](04_Connect_AI_Providers.md#see-what-a-chat-costs)).

## Part 2: Make a first change

### Prepare a test Blueprint

If you do not have a Blueprint you can safely change, create one:

1. In the Content Browser, click **Add → Blueprint Class** and choose **Actor**. Name it `BP_TestActor`.
2. Open it, add a variable named `Health`, set its type to **Float**, click **Compile** and **Save**.

You can also ask eXe to create it: `Create a Blueprint actor BP_TestActor with a float variable Health.` That task is larger, so eXe may show you a plan first, which is a good way to see the approval step.

### Ask for the change

1. In the chat, type: `In BP_TestActor, change the default value of Health to 150.`
2. This is a small, clear change, so with the default setting (**Plan before changes: Automatic**) eXe usually runs it directly: it changes the value, saves the asset and reads the value back.
3. If you see **The plan above is ready for your approval** instead, read the plan (target asset, expected change, what must not change) and click **Approve plan**, or type `approve`. Larger tasks always show a plan like this first.

Expected result:

- Open the Blueprint: the default value of `Health` is 150.
- Above the chat input, **Changes (1)** lists the changed asset with **Keep** and **Revert**.
- Click **Details in Jobs** under the reply. Under **Result and checks**, **How far the result is proven** shows **Goal verified**: eXe read the new value back from the editor.

To undo it, select the row in **Changes** and click **Revert**.

## Part 3: Try the tools without AI

1. In the eXe Agent window, switch to **Tools**.
2. Select one Blueprint in the Content Browser and click **Explain Blueprint**.

Expected result: a summary of components, variables, functions and what each graph calls. No AI provider is used and nothing changes.

## Next steps

- What you see in the window and what each button does: [The eXe Agent Window](03_Agent_Window.md)
- How much eXe may do on its own: [Permissions and Safety](06_Permissions_And_Safety.md)
- Answers to common questions: [FAQ](12_FAQ.md)

Previous: [Installation](01_Installation.md) · [Documentation Index](INDEX.md) · Next: [The eXe Agent Window](03_Agent_Window.md)
