# Connect AI Providers

eXe does not include an AI model. You connect the AI you want to use. You can combine the options below; they all work on the same project, jobs and approvals.

Without any AI, the **Tools** view still works ([Capabilities](05_Capabilities.md#without-an-ai-provider)).

## Option 1: The eXe chat with your API key

Providers in the chat: **OpenAI**, **Anthropic**, **Gemini**, **DeepSeek** and **Local model**.

1. In **Chat**, click the AI controller button at the top right (or **Connect an AI controller** on the start page).
2. Choose the provider.
3. Enter the model ID exactly as your provider lists it, without spaces. Use a current model from your provider's documentation. eXe needs a model that handles tool calls reliably.
4. Enter your API key. When a key is already saved, leaving the field blank keeps it.
5. Click **Save**.

Keys are saved for your Windows user in Windows Credential Manager. **Remove saved key** deletes the key of the selected provider. A new controller applies to new chats; an existing chat keeps the controller it started with.

Model usage is billed by your provider under your own account. The chat shows the token usage your provider reports. Optionally enter prices per 1M tokens (input; output; cached input; currency, for example `3; 15; 0.3; USD`) to see costs.

### Local models

Choose **Local model** and enter the address of your local server. The default is `http://127.0.0.1:11434/v1` (Ollama). Any server with an OpenAI-compatible `/v1` API and tool support works the same way. A key is only needed if your local server asks for one.

You install, start and choose local models yourself. Small local models plan less reliably than large hosted models. If eXe reports that the model did not produce a usable tool call, send the message again or choose a stronger model.

## Option 2: Claude Code, Codex or Claude Desktop

If you have the official **Claude Code**, **Codex** or **Claude Desktop** installed and signed in with your own account, you can connect it to eXe. No API key is needed in eXe.

1. Open **Settings → AI clients (Claude Code, Codex, Claude Desktop)**.
2. Under **Connections**, click **Connect / repair** once. This adds only the `exe-loading` entry to the user configuration of Claude Code, Codex and Claude Desktop. Other MCP entries stay unchanged and the access key is never shown. Restart command windows that are already open and Claude Desktop afterwards.
3. For Claude Code or Codex, click **Copy Claude Code command** or **Copy Codex command**. eXe shows the copied line.
4. Open a new **Command Prompt (cmd)**, paste the line and press Enter. Sign in there if the client asks.

The copied line opens the client in an eXe workspace folder for this project that contains the eXe planning workflow. Claude Desktop needs no command: after step 2, restart it and eXe is available there.

eXe never installs these clients and never starts them. They use your own subscription or login. Blueprint, asset and C++ changes still run only through plans you approve.

**Check status** shows the connection state. **Renew token** replaces the access key. **Revoke token** removes access until you connect again.

## Option 3: Other MCP clients on your PC

MCP clients on the same PC that support streamable HTTP can connect to `http://127.0.0.1:8798/mcp` (default). The exact address is shown under **Settings → Connection** as **Address for AI clients (MCP)**. Use your client's documented MCP setup. If a second editor is running, it uses the next free port.

## Option 4: ChatGPT from anywhere

See [Remote Access with ChatGPT](07_Remote_Access_ChatGPT.md).

## Which option should I use?

| You want... | Use |
|---|---|
| A quick start | The eXe chat with an API key |
| To use an existing Claude or ChatGPT subscription | Option 2 or Option 4 |
| No cloud AI at all | The eXe chat with a local model |

A plan approved in one place is the same plan everywhere.

Previous: [The eXe Agent Window](03_Agent_Window.md) · [Documentation Index](INDEX.md) · Next: [Capabilities](05_Capabilities.md)
