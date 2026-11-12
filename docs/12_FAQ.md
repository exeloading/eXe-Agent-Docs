# FAQ

Short answers to the questions we hear most often. For a message you see on screen, look at [Troubleshooting](08_Troubleshooting_And_FAQ.md). Words you do not know are explained in the [Glossary](13_Glossary.md).

On this page:

- **[Getting started](#getting-started)**
  - [What is eXe Agent?](#what-is-exe-agent)
  - [Which Unreal Engine versions and platforms are supported?](#which-unreal-engine-versions-and-platforms-are-supported)
  - [Will eXe Agent support Unreal Engine 5.9?](#will-exe-agent-support-unreal-engine-59)
  - [How do I install eXe Agent, and what if I cannot see its button?](#how-do-i-install-exe-agent-and-what-if-i-cannot-see-its-button)
  - [Do I need Python, Node.js or Visual Studio?](#do-i-need-python-nodejs-or-visual-studio)
  - [Does eXe work with Blueprint-only projects?](#does-exe-work-with-blueprint-only-projects)
  - [What is Unreal's MCP server, and why does eXe need it?](#what-is-unreals-mcp-server-and-why-does-exe-need-it)
  - [Can I open two projects with eXe at the same time?](#can-i-open-two-projects-with-exe-at-the-same-time)
- **[Costs and AI providers](#costs-and-ai-providers)**
  - [What does eXe Agent cost?](#what-does-exe-agent-cost)
  - [Is my ChatGPT Plus or Claude Pro subscription an API key?](#is-my-chatgpt-plus-or-claude-pro-subscription-an-api-key)
  - [Can I use eXe without an API key?](#can-i-use-exe-without-an-api-key)
  - [Which AI providers work in the eXe chat?](#which-ai-providers-work-in-the-exe-chat)
  - [Which model should I choose?](#which-model-should-i-choose)
  - [How can I see what a chat costs?](#how-can-i-see-what-a-chat-costs)
  - [Can I use a local model such as Ollama or LM Studio, also offline?](#can-i-use-a-local-model-such-as-ollama-or-lm-studio-also-offline)
  - [Why does eXe answer in English?](#why-does-exe-answer-in-english)
  - [Do I have to enter my key again in another project?](#do-i-have-to-enter-my-key-again-in-another-project)
- **[Privacy and data](#privacy-and-data)**
  - [Does eXe send my project to eXe servers?](#does-exe-send-my-project-to-exe-servers)
  - [Where are my API keys stored, and how do I remove them?](#where-are-my-api-keys-stored-and-how-do-i-remove-them)
  - [Does eXe work behind a company proxy?](#does-exe-work-behind-a-company-proxy)
  - [Should I commit the ProjectDocs/eXe folder?](#should-i-commit-the-projectdocsexe-folder)
- **[Approvals, safety and undo](#approvals-safety-and-undo)**
  - [Will eXe break my project?](#will-exe-break-my-project)
  - [Why does eXe ask me to approve a plan?](#why-does-exe-ask-me-to-approve-a-plan)
  - [How do I approve a plan?](#how-do-i-approve-a-plan)
  - [Can I make eXe ask before every change?](#can-i-make-exe-ask-before-every-change)
  - [How do I stop a running task?](#how-do-i-stop-a-running-task)
  - [How do I undo a change?](#how-do-i-undo-a-change)
  - [What are Power Write and YOLO?](#what-are-power-write-and-yolo)
  - [Does eXe commit to Git or Perforce for me?](#does-exe-commit-to-git-or-perforce-for-me)
- **[Builds and C++](#builds-and-c)**
  - [Can eXe change C++ code?](#can-exe-change-c-code)
  - [Why did the editor close, why does it not open again, and what if the build failed?](#why-did-the-editor-close-why-does-it-not-open-again-and-what-if-the-build-failed)
- **[Error messages](#error-messages)**
  - [The chat says "The model did not produce a usable tool call". What can I do?](#the-chat-says-the-model-did-not-produce-a-usable-tool-call-what-can-i-do)
  - [The chat says the provider refused the request because of a rate limit or no credit. What does that mean?](#the-chat-says-the-provider-refused-the-request-because-of-a-rate-limit-or-no-credit-what-does-that-mean)
  - [The header says "Unreal MCP is off" or "check Unreal MCP in Settings". What should I do?](#the-header-says-unreal-mcp-is-off-or-check-unreal-mcp-in-settings-what-should-i-do)
  - [Where do I find the other messages?](#where-do-i-find-the-other-messages)
- **[AI clients and ChatGPT](#ai-clients-and-chatgpt)**
  - [How do I connect Claude Code or Codex?](#how-do-i-connect-claude-code-or-codex)
  - [Claude Desktop does not show eXe. What can I check?](#claude-desktop-does-not-show-exe-what-can-i-check)
  - [Why can Claude Code or Codex not run commands or edit my files in the eXe session?](#why-can-claude-code-or-codex-not-run-commands-or-edit-my-files-in-the-exe-session)
  - [How do I use eXe from ChatGPT?](#how-do-i-use-exe-from-chatgpt)
- **[Product, license, updates and support](#product-license-updates-and-support)**
  - [How is eXe Agent different from the AI assistant in Unreal Engine 5.9?](#how-is-exe-agent-different-from-the-ai-assistant-in-unreal-engine-59)
  - [Which Fab license do I need, Personal or Professional?](#which-fab-license-do-i-need-personal-or-professional)
  - [How do I get updates, and where do I get help?](#how-do-i-get-updates-and-where-do-i-get-help)
  - [Where can I suggest a feature or report a bug?](#where-can-i-suggest-a-feature-or-report-a-bug)

## Getting started

### What is eXe Agent?
eXe Agent is an AI assistant inside the Unreal Editor. You describe a task in your own words. eXe reads your project, makes small changes directly or shows a plan for larger work, works only inside what you approved, and checks the result in the editor. Every change is listed so you can undo it. You bring your own AI: an API key, a local model, Claude Code, Codex or ChatGPT.

### Which Unreal Engine versions and platforms are supported?
eXe Agent 1.0.0 supports Unreal Engine 5.8 on Windows 64-bit. It was tested with 5.8.3. macOS, Linux and other engine versions are not supported in this version. eXe uses experimental engine features, so a future engine version may need a plugin update.

### Will eXe Agent support Unreal Engine 5.9?
Yes, support for Unreal Engine 5.9 is planned as a free update after Epic releases 5.9 and Fab accepts it. Until then, use eXe Agent with Unreal Engine 5.8.

### How do I install eXe Agent, and what if I cannot see its button?
Close Unreal, open the Fab Library in the Epic Games Launcher, click **Install to Engine** and choose Unreal Engine 5.8. Open your project, make sure **eXe Agent** is enabled under **Edit → Plugins** and restart the editor. Open the window with the **eXe Agent** toolbar button, **Window → eXe Agent** or **Ctrl+Shift+Space**. If you cannot find it, check under **Edit → Plugins** that eXe Agent is enabled and restart the editor. Step by step: [Installation](01_Installation.md).

### Do I need Python, Node.js or Visual Studio?
You do not install Python: eXe uses the Python that comes with Unreal. Node.js is only needed if you connect Claude Desktop. To build C++ code, your PC needs the Visual Studio C++ tools and the Windows SDK that Unreal Engine 5.8 requires. Blueprint, asset and level work does not need a build.

### Does eXe work with Blueprint-only projects?
Yes. eXe reads and changes Blueprints, assets, levels, materials, UMG and more without any C++. C++ editing and full builds need a project with C++ source code.

### What is Unreal's MCP server, and why does eXe need it?
MCP (Model Context Protocol) is the way eXe works inside the Unreal Editor. Unreal ships its own MCP server, but its automatic start can be off. Turn it on under **Edit → Editor Preferences → Model Context Protocol → Auto Start Server**. While it is off, the header shows **eXe running · Unreal MCP is off, see Settings**. See [Installation, Step 2](01_Installation.md#step-2-start-unreals-mcp-server).

### Can I open two projects with eXe at the same time?
Yes. Each editor runs its own eXe with its own jobs and its own address. Each project also needs its own Unreal MCP port: in the second project, set **Editor Preferences → Model Context Protocol → Server Port Number** to a free port, for example `8001`, and restart that editor. If you use Claude Desktop, click **Connect / repair** in the project you work on and restart Claude Desktop.

## Costs and AI providers

### What does eXe Agent cost?
You pay the plugin price on Fab once. There is no eXe subscription and no eXe account. AI use is billed by the AI provider you connect, under your own account. Asset generation services, tunnels and sign-in services bill you directly if they charge.

### Is my ChatGPT Plus or Claude Pro subscription an API key?
No. A chat subscription and API access are separate products at OpenAI and Anthropic. The eXe chat needs an API key, which the provider bills separately. With your Claude or ChatGPT login you can use Claude Code, Codex or Claude Desktop instead (see the next question). Check with your provider which plan includes these clients.

### Can I use eXe without an API key?
Yes. The **Tools** view checks assets, the open level and Blueprints and can build the project without any AI. For AI work without an API key, connect Claude Code or Codex with your own login ([Option 2](04_Connect_AI_Providers.md#option-2-claude-code-codex-or-claude-desktop)), or use a local model on your PC.

### Which AI providers work in the eXe chat?
OpenAI, Anthropic, Gemini and DeepSeek with your own API key, and a local model on your PC (for example Ollama or LM Studio). The cloud providers always use their official address. Other cloud services, for example another OpenAI-compatible service, cannot be entered in version 1.0.

### Which model should I choose?
Choose a current model from your provider that handles tool calls reliably. Larger hosted models plan more reliably than small local models; smaller and cheaper models are fine for simple questions. Enter the model ID exactly as your provider lists it, without spaces. The field shows an example, for example `claude-sonnet-5-5` for Anthropic. A display name such as "Claude Sonnet 5.5" is rejected.

### How can I see what a chat costs?
The top of each chat shows the tokens your provider reported. If you enter your provider's prices per 1M tokens in the AI controller, for example `3; 15; 0.3; USD`, it also shows an estimate. A longer chat costs more per reply, because the model reads the whole chat again each time. **Chat length** sets when the AI summarizes a chat; **Compact chat now** does it right away. See [Costs](04_Connect_AI_Providers.md#see-what-a-chat-costs).

### Can I use a local model such as Ollama or LM Studio, also offline?
Yes. In the AI controller choose **Local model** and enter the address of your server, for example `http://127.0.0.1:11434/v1` for Ollama. The server must run on this PC, offer an OpenAI-compatible `/v1` API with tool support and use a context length of at least 32,768 tokens. With a local model and the **Tools** view, nothing leaves your PC. Small local models plan less reliably than large hosted models.

### Why does eXe answer in English?
The reply language is separate from the window language and starts on English. Change it under **Settings → General → eXe replies in**. Choose **Automatic (language of your message)** to get answers in the language you write in. Plan headings exist only in English and German, and some detail messages from the eXe core are always in English.

### Do I have to enter my key again in another project?
No. Your key is saved for your Windows user. The AI controller (provider and model) is saved per project, so in a new project choose provider and model once and leave the key field blank to use the saved key.

## Privacy and data

### Does eXe send my project to eXe servers?
No. There are no eXe servers, no eXe account and no telemetry to the developer. Data leaves your PC only for services you set up. The AI provider receives your messages, attached images and the project information the AI requests, such as file contents, asset data and logs. Check your provider's data policy before you send confidential content. Details: [Privacy](11_Privacy_Costs_And_Third_Party.md).

### Where are my API keys stored, and how do I remove them?
Keys are stored in Windows Credential Manager for your Windows user, not in the project folder. eXe does not show them to AI clients and does not include them in **Copy for support**. To remove the chat key, open the AI controller and click **Remove saved key**. To remove an asset generation key, open **Settings → Asset generation**, choose the provider, leave the key field empty and click **Save key**.

### Does eXe work behind a company proxy?
The eXe chat and asset generation connect to the provider directly and do not use a system proxy. In a network that reaches the internet only through a proxy, use Claude Code or Codex instead.

### Should I commit the ProjectDocs/eXe folder?
eXe creates `ProjectDocs/eXe` only when it saves a plan copy, a note, a decision or a project rule there. It contains only Markdown, and eXe refuses to save keys there. Commit `ProjectDocs/eXe/Rules` if your team should share the same project rules. Plans, notes and decisions are your choice. The `Saved/eXe.Loading` folder belongs to `Saved/`, which is usually not committed.

## Approvals, safety and undo

### Will eXe break my project?
eXe changes only what you asked for or approved, saves only the assets a step changed and reads results back. Every change is listed for undo, and eXe keeps a copy of each changed file for 14 days. Some things cannot be put back, for example World Partition actor files and files over 64 MB. Use version control and commit before large jobs, and keep Power Write and YOLO off until you know how eXe works in your project.

### Why does eXe ask me to approve a plan?
eXe runs a small, clear change you ask for directly: at most 5 steps and 5 changed assets or files, nothing deleted and no Python script. Larger work, deletes and Python scripts first show a plan, and eXe runs it only after you approve it. The plan names what may change and what must not change. You can change this under **Settings → Permissions → Plan before changes**.

### How do I approve a plan?
Click **Approve plan** on the card below the reply, or type a short answer such as `approve`, `ok` or `go ahead`. Approving runs exactly what the plan shows; anything else needs a new plan. In Claude Code, Codex or ChatGPT you approve in that chat. **Jobs** shows the full plan, but you cannot approve there.

### Can I make eXe ask before every change?
Yes. Set **Settings → Permissions → Plan before changes** to **Always**. Then every change shows its plan first, also while YOLO is on.

### How do I stop a running task?
In the chat, click **Stop** to stop the current reply. In **Jobs**, select the job and click **Stop work** or **Cancel work**; both end the job the same way. While the job runs, they only record a different word (**Stopped** or **Cancelled**); a plan that has not started is recorded as **Cancelled**. Changes from finished steps stay listed under **Changes**, and you can revert them where eXe kept a copy.

### How do I undo a change?
Above the chat input, **Changes** lists what finished jobs changed. Select a row and click **Revert** to put it back to the state before the job; the current version is kept as a backup. In **Jobs**, **Undo this job's changes** reverts a whole job. eXe keeps its copies for 14 days and keeps none for World Partition actor files or files over 64 MB, so also use version control.

### What are Power Write and YOLO?
**Power Write** lets approved plans change C++ and other source files and run Python scripts. Unreal's Undo does not cover these changes. **YOLO** lets eXe approve and run plans from local or signed-in AI clients without asking you, for up to 90 minutes per job. Both are off after installation and apply to all your projects. The header shows a warning while YOLO is on.

### Does eXe commit to Git or Perforce for me?
No. eXe does not commit, push or merge. Use your version control as usual, and commit before large jobs so you can always go back.

## Builds and C++

### Can eXe change C++ code?
Yes, after you turn on **Power Write**. For a change inside existing `.cpp` files, eXe can use Live Coding when the optional `LiveCodingToolset` Engine plugin is enabled. New classes and changes to headers, `Build.cs` files or constructors need a full build. After a Live Coding change, build the project in your IDE before you restart Unreal, or the change is lost.

### Why did the editor close, why does it not open again, and what if the build failed?
A full build needs the editor to be closed, so eXe closes it and Unreal Build Tool runs in a console window. eXe never restarts the editor. When the console window has closed, open your project again and eXe continues the job. If the build failed, open `Saved/eXe.Loading/LAST_FULL_BUILD.md` in your project: it names the build log and the next steps.

## Error messages

### The chat says "The model did not produce a usable tool call". What can I do?
The model could not answer in the form eXe needs, even on a second try. This happens often with small local models. Send the message again, or choose a stronger model in the AI controller.

### The chat says the provider refused the request because of a rate limit or no credit. What does that mean?
Your provider refused the request for now. Either too many requests arrived in a short time, or your account has no credit left. Try again later, or check your plan and balance with the provider. eXe cannot change this limit.

### The header says "Unreal MCP is off" or "check Unreal MCP in Settings". What should I do?
Open **Settings → Connection** and hover over the **Unreal MCP** line to see the steps for your case. Usually you turn on **Auto Start Server** under **Edit → Editor Preferences → Model Context Protocol**. If the line says the address belongs to another Unreal editor, give this project its own **Server Port Number** and restart the editor. All messages: [Unreal MCP messages](08_Troubleshooting_And_FAQ.md#unreal-mcp-messages).

### Where do I find the other messages?
The [Troubleshooting](08_Troubleshooting_And_FAQ.md) page lists every chat message with its cause and what to do. Search it for the words you see (**Ctrl+F**).

## AI clients and ChatGPT

### How do I connect Claude Code or Codex?
Install Claude Code or Codex yourself and sign in. In eXe, open **Settings → AI clients**, click **Connect / repair** once, then click **Copy Claude Code command** or **Copy Codex command**. Open a new PowerShell or Command Prompt window, paste the line and press **Enter**; this starts the client. eXe never starts these programs itself.

### Claude Desktop does not show eXe. What can I check?
Open Claude Desktop once so it creates its configuration file, and install Node.js, because Claude Desktop reaches eXe through the npm package `mcp-remote`. Then click **Connect / repair** under **Settings → AI clients** and restart Claude Desktop. The status line next to Claude Desktop tells you what is missing. If you switch to another project, click **Connect / repair** there again.

### Why can Claude Code or Codex not run commands or edit my files in the eXe session?
The copied start command opens the client with a reduced set of tools on purpose. Claude Code can read files and use eXe, and Codex runs read-only without shell commands or web search. Project changes go through eXe, so they are checked, backed up and listed for undo. If you start the client another way, its own tools work, but eXe cannot check or revert what they change.

### How do I use eXe from ChatGPT?
ChatGPT reaches eXe on your PC through a tunnel that you run yourself, for example Cloudflare Tunnel, and you need a ChatGPT plan that supports custom MCP connectors. Set up your own sign-in service (OAuth) so only you can use the connection. Enter the tunnel address and the sign-in service under **Settings → ChatGPT and remote access**, click **Check** and **Save**, and restart the editor. Access without sign-in is not supported in version 1.0. Step by step: [Remote Access with ChatGPT](07_Remote_Access_ChatGPT.md).

## Product, license, updates and support

### How is eXe Agent different from the AI assistant in Unreal Engine 5.9?
Epic's assistant is part of Unreal Engine 5.9; for its features, see Epic's documentation. eXe Agent 1.0.0 runs on Unreal Engine 5.8. What eXe adds: you choose the AI (your own key, a local model, Claude Code, Codex or ChatGPT), larger changes wait for a plan you approve, eXe reads the result back and shows how far it is proven, every change is listed with revert, and the **Tools** view works without any AI.

### Which Fab license do I need, Personal or Professional?
eXe Agent is sold on Fab under the Fab Standard License, which has two price tiers. According to [Fab's license page](https://dev.epicgames.com/documentation/fab/licenses-and-pricing-in-fab), **Personal** is for buyers who have not generated more than 100,000 USD in gross revenue from commercial activity in the last 12 months, and **Professional** is for buyers above that. Both tiers grant the same rights. Fab's End User License Agreement is binding. If you are unsure, ask us on Discord or by email.

### How do I get updates, and where do I get help?
Updates arrive through the Epic Games Launcher; close the editor before you update. Your project data in `Saved/eXe.Loading` is kept, and the [Changelog](10_Changelog.md) lists what changed. For help, post in `#support` on [Discord](https://discord.gg/ebW7kKCC25) or write to [exeagent.support@gmail.com](mailto:exeagent.support@gmail.com). Include the text from **Copy for support** in **Jobs** and never post API keys.

### Where can I suggest a feature or report a bug?
On [Discord](https://discord.gg/ebW7kKCC25): `#support` for problems, and the channels for feature requests and bug reports. Known problems are collected in `#known-issues` and in [Known Issues and Limitations](09_Known_Issues_And_Limitations.md).

Previous: [Privacy, Costs and Third-Party Software](11_Privacy_Costs_And_Third_Party.md) · [Documentation Index](INDEX.md) · Next: [Glossary](13_Glossary.md)
