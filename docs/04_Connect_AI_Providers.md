# Connect AI Providers

eXe does not include an AI model. You connect the AI you want to use. You can combine the options below; they all work on the same project, jobs and approvals.

Without any AI, the **Tools** view still works ([Capabilities](05_Capabilities.md#without-an-ai-provider)).

## Which option should I use?

| You want... | Use |
|---|---|
| A quick start with an API key | [Option 1](#option-1-the-exe-chat-with-your-api-key): the eXe chat |
| To use an existing Claude or ChatGPT subscription | [Option 2](#option-2-claude-code-codex-or-claude-desktop) (Claude Code, Codex, Claude Desktop) or [Option 4](#option-4-chatgpt-from-anywhere) (ChatGPT) |
| No cloud AI at all | [Option 1](#local-models) with a local model |

A plan approved in one place is the same plan everywhere.

## Option 1: The eXe chat with your API key

Providers in the chat: **OpenAI**, **Anthropic**, **Gemini**, **DeepSeek** and **Local model**. How to get an API key: [Quick Start](02_Quick_Start.md#get-an-api-key).

1. In **Chat**, click the AI controller button at the top right (**Connect AI**), or **Connect an AI controller** on the start page.
2. Choose the provider. The list starts on **Local model**.
3. Enter the model ID exactly as your provider lists it, without spaces. The field shows an example, for example `claude-sonnet-5-5` for Anthropic. A display name such as `Claude Sonnet 5.5` is rejected. Use a current model from your provider's documentation; eXe needs a model that handles tool calls reliably.
4. Enter your API key. When a key is already saved, leaving the field blank keeps it.
5. Optional: choose **Chat length** and enter your prices (see below).
6. Click **Save**.

What is saved where:

- The **key** is saved for your Windows user in Windows Credential Manager, one per provider. In another project you do not need to enter it again.
- The **AI controller** (provider and model) is saved per project. In a new project, choose provider and model once and leave the key field blank to use the saved key.
- A new controller applies to new chats. An existing chat keeps the controller it started with; the chat then says which controller it uses.
- **Remove saved key** deletes the key of the selected provider.

The cloud providers always use their official address. Other cloud services, for example another OpenAI-compatible service, cannot be entered in version 1.0.

Images: OpenAI, Anthropic and Gemini models that read images accept attached images. With DeepSeek, only `deepseek-flash` reads images. A local model reads images only if it supports them.

### See what a chat costs

Model usage is billed by your provider under your own account. eXe has no costs of its own.

- The line at the top of a chat shows the tokens your provider reported, for example `tokens in 120,000, out 3,400`, and how long the chat is: `chat length about 45k of 200k tokens`.
- Optional: enter your provider's prices per 1M tokens in the AI controller, in the order input; output; cached input; currency, for example `3; 15; 0.3; USD`. The line then also shows an estimate such as `about 0.42 USD with your prices`. Your provider's bill is what counts.
- A longer chat costs more per reply, because the model reads the whole chat again each time. **Chat length** (100k to 900k tokens, recommended 200k) sets when the AI summarizes the chat. **Compact chat now** and **Continue in a new chat** in the **…** menu make the chat short again ([Long chats](03_Agent_Window.md#long-chats-and-costs)).
- Broad requests ("analyze the whole project") read more of the project and use more tokens than narrow ones.

### Local models

Choose **Local model** and enter the address of your local server. The default is `http://127.0.0.1:11434/v1` (Ollama). Any server on this PC with an OpenAI-compatible `/v1` API and tool support works the same way, for example LM Studio. The address must be on this PC (`127.0.0.1` or `localhost`) and end in `/v1`. Version 1.0 does not accept a server on another computer. A key is only needed if your local server asks for one.

You install, start and choose local models yourself. eXe sends about 15,000 to 16,000 tokens of instructions and tool descriptions with every request, so set the context length of your local server to at least 32,768 tokens:

- Ollama: the **Context length** setting or the environment variable `OLLAMA_CONTEXT_LENGTH`.
- LM Studio: the context length the model is loaded with.

eXe reads the context length your server reports. If it is too small, the chat says `The local model runs with a context length of ... tokens. eXe needs at least 32768 ...`. Set a larger value, load the model again and send the message again.

Small local models plan less reliably than large hosted models. If eXe reports that the model did not produce a usable tool call, send the message again or choose a stronger model. With a local model and the **Tools** view, nothing leaves your PC.

## Option 2: Claude Code, Codex or Claude Desktop

If you have the official **Claude Code**, **Codex** or **Claude Desktop** installed and signed in with your own account, you can connect it to eXe. No API key is needed in eXe. eXe never installs or starts these programs. Get them from their makers: [Claude Code](https://code.claude.com/docs), [Codex](https://github.com/openai/codex), [Claude Desktop](https://claude.ai/download).

### Connect once

1. Open **Settings → AI clients (Claude Code, Codex, Claude Desktop)**.
2. Under **Connections**, click **Connect / repair**. This adds only an `exe-loading` entry to the user configuration of Claude Code, Codex and Claude Desktop and saves an access key in your Windows user environment. Other MCP entries stay unchanged and the key is never shown.
3. Close command windows that are already open, and restart Claude Desktop. Programs only see the new key after they start again.

**Check status** shows one line per client:

| Status | Meaning and next step |
|---|---|
| **connected** | Ready. **access checked** means eXe confirmed the key works |
| **not connected yet** | Click **Connect / repair** |
| **needs repair: click Connect / repair** | The entry is outdated or points to an old address. Click **Connect / repair** |
| **already has an exe-loading entry for another address, which eXe leaves alone** | You set up an `exe-loading` entry yourself. eXe does not overwrite it. Remove it in the client if you want eXe's entry |
| **not installed** | eXe did not find the client. Install it, then click **Connect / repair** |
| **no config file yet: open Claude Desktop once (Settings > Developer > Edit Config), then click Connect / repair** | Do what it says |
| **needs Node.js (npx): install Node.js LTS, then click Connect / repair** | Claude Desktop needs [Node.js](https://nodejs.org) |
| **access not confirmed, is eXe running?** | eXe could not test the key. Check the header shows **eXe running** and try again |
| **Access key: set up** / **not set up yet** | Whether the access key exists |

**Renew token** replaces the access key, also in Claude Desktop's entry; close open terminals and restart Claude Desktop afterwards. **Revoke token** blocks all clients until you click **Connect / repair** again.

### Start Claude Code or Codex

1. Click **Copy Claude Code command** or **Copy Codex command**. eXe shows the copied line.
2. Open a new terminal (**PowerShell** or **Command Prompt**), paste the line and press **Enter**. This starts the client, so you do not open it first. Sign in there if the client asks.

The line starts the client in an eXe workspace folder for this project. That folder contains the eXe workflow guides and a start file. If the terminal says:

| Terminal message | What to do |
|---|---|
| `eXe is not connected yet. In eXe open Settings, AI clients, click Connect / repair, then open a new terminal.` | Do what it says. A terminal that was open before **Connect / repair** does not see the key |
| `Claude Code was not found. Install it, then open a new terminal.` (or `Codex was not found...`) | Install the client, then open a new terminal |

If eXe says **Your Windows user folder contains characters a command line cannot handle**, click **Connect / repair** and start the client yourself in any folder.

**What the eXe session can do.** The copied line starts the client with a reduced set of tools on purpose. Claude Code can read files and use eXe; Codex runs read-only, without shell commands or web search. Project changes go through eXe, so they are checked, backed up and listed for undo: small requests run directly, larger ones after you approve the plan in that chat. The line signs in with your Claude or ChatGPT account. If your client uses an API key instead, start it yourself as usual: the `exe-loading` entry from **Connect / repair** is already in its configuration. Its own tools then work too, but eXe cannot check or revert what they change.

### Claude Desktop

Claude Desktop needs no command. Before **Connect / repair**: start Claude Desktop at least once, and install [Node.js](https://nodejs.org). Claude Desktop reaches eXe through the small npm package `mcp-remote`, which it downloads from the npm registry and runs itself; eXe never starts it. After **Connect / repair**, restart Claude Desktop and eXe is available there.

### After a full build

The editor closes for a full build, so clients lose their connection. After you open the project again: in Claude Code type `/mcp`, choose **exe-loading** and click **Reconnect**. Restart Claude Desktop if it does not reconnect by itself.

## Two projects and switching projects

- Each open editor runs its own eXe with its own jobs and its own address (`8798` for the first editor, the next free port for the next one). **Settings → Connection** shows the address.
- Each open project also needs its own Unreal MCP port ([Installation](01_Installation.md#step-2-start-unreals-mcp-server)).
- Clients are bound to a project. A client that reaches the wrong editor gets the error `EXE_PROJECT_MISMATCH` and eXe does nothing.
  - Claude Desktop and clients you start yourself use the project of the last **Connect / repair**. When you switch projects, click **Connect / repair** in the project you work on and restart Claude Desktop.
  - For Claude Code and Codex, copy the start command in the project you work on. Copy it again after you reopen editors in a different order, because the address can change.

## Option 3: Other MCP clients on your PC

MCP clients on the same PC that support streamable HTTP can connect to `http://127.0.0.1:8798/mcp` (default). The exact address is shown under **Settings → Connection** as **Address for AI clients (MCP)**. Use your client's documented MCP setup and send the header `Authorization: Bearer <token>`. After **Connect / repair** (Option 2), the token is in the Windows user environment variable `EXE_LOADING_LOCAL_TOKEN`; reference the variable in your client's configuration instead of copying the value.

## Option 4: ChatGPT from anywhere

See [Remote Access with ChatGPT](07_Remote_Access_ChatGPT.md). This is the most technical option; if you are new, start with Option 1 or 2.

Previous: [The eXe Agent Window](03_Agent_Window.md) · [Documentation Index](INDEX.md) · Next: [Capabilities](05_Capabilities.md)
