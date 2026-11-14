# Glossary

Short explanations of the words you meet in eXe and in this documentation, in alphabetical order. Questions are answered in the [FAQ](12_FAQ.md).

| Term | Meaning | More |
|---|---|---|
| **AI client** | A program from an AI company that you sign in to with your own account, such as Claude Code, Codex, Claude Desktop or ChatGPT. It can use eXe through MCP. | [Connect AI Providers](04_Connect_AI_Providers.md#option-2-claude-code-codex-or-claude-desktop) |
| **AI controller** | The AI that the eXe chat uses: a provider and a model ID. It is saved per project. Set it with **Connect AI** in the chat. | [Connect AI Providers](04_Connect_AI_Providers.md#option-1-the-exe-chat-with-your-api-key) |
| **AI provider** | The company that runs the AI model, for example OpenAI, Anthropic, Google (Gemini) or DeepSeek. It bills you for what you use. | [Privacy, Costs](11_Privacy_Costs_And_Third_Party.md) |
| **API key** | A secret code from your AI provider that lets a program use your account. Use is billed per request. A chat subscription such as ChatGPT Plus or Claude Pro is not an API key. | [Quick Start](02_Quick_Start.md#get-an-api-key) |
| **Approval** | Your yes to a plan. It covers exactly that one sealed plan and nothing else. | [Permissions and Safety](06_Permissions_And_Safety.md#what-an-approval-covers) |
| **Blueprint** | Unreal's visual scripting: game logic built from nodes instead of C++ code. eXe can read and change Blueprints without a build. | [Capabilities](05_Capabilities.md) |
| **Chat length** | The size at which the AI summarizes a long chat, so that each reply stays affordable. **Compact chat now** summarizes right away. | [Long chats and costs](03_Agent_Window.md#long-chats-and-costs) |
| **Context length** | How much text a model can read at once, counted in tokens. A local model needs at least 32,768 tokens for eXe. | [Local models](04_Connect_AI_Providers.md#local-models) |
| **Copy for support** | A button in **Jobs** that copies technical details about a job for a support request. It contains no API keys. | [Troubleshooting](08_Troubleshooting_And_FAQ.md#how-to-ask-for-help) |
| **Direct change** | A small, clear change you ask for, which eXe runs without showing a plan first: at most 5 steps and 5 changed assets or files, nothing deleted and no Python script. | [Plan before changes](06_Permissions_And_Safety.md#plan-before-changes) |
| **Dynamic client registration** | A setting in a sign-in service that lets apps register themselves. For ChatGPT access, turning it off is recommended. | [Remote Access with ChatGPT](07_Remote_Access_ChatGPT.md#step-2a-with-sign-in-recommended) |
| **eXe Core** | The part of eXe that plans, checks and records jobs. It runs inside the Unreal Editor and starts with it. | [Troubleshooting](08_Troubleshooting_And_FAQ.md#exe-does-not-start) |
| **Full build** | Compiling the whole C++ project with Unreal Build Tool. The editor must be closed for it. | [C++ and builds](06_Permissions_And_Safety.md#c-and-builds) |
| **Job** | One task in eXe, with its plan, steps, changes and result. Every job is listed under **Jobs**. | [Jobs](03_Agent_Window.md#jobs) |
| **Live Coding** | An Unreal feature that updates C++ code in the running editor without closing it. The change is not in the files Unreal loads at the next start until you build in your IDE. | [Live Coding](06_Permissions_And_Safety.md#live-coding) |
| **Local model** | An AI model that runs on your own PC, for example with Ollama or LM Studio. Nothing is sent to a cloud provider. | [Local models](04_Connect_AI_Providers.md#local-models) |
| **MCP (Model Context Protocol)** | A common standard that lets AI programs use tools. Unreal uses it to offer editor tools, and AI clients use it to reach eXe. | [Installation](01_Installation.md#step-2-start-unreals-mcp-server) |
| **Model ID** | The exact technical name of a model as your provider lists it, for example `claude-sonnet-5-5`. A display name such as "Claude Sonnet 5.5" does not work. | [Connect AI Providers](04_Connect_AI_Providers.md#option-1-the-exe-chat-with-your-api-key) |
| **OAuth, sign-in service** | A service such as Auth0, Microsoft Entra or Keycloak that checks who you are before ChatGPT may use eXe through a tunnel. | [Remote Access with ChatGPT](07_Remote_Access_ChatGPT.md) |
| **PIE (Play in Editor)** | Playing your game inside the Unreal Editor. eXe can run PIE tests and take a screenshot after game steps. | [Jobs](03_Agent_Window.md#jobs) |
| **Plan** | The list of steps eXe will run for a larger task, with the targets that may change and the targets that must not change. | [How a job works](03_Agent_Window.md#how-a-job-works) |
| **Plan before changes** | The setting that decides when eXe shows a plan before it changes something: **Automatic**, **Only when I ask** or **Always**. | [Permissions and Safety](06_Permissions_And_Safety.md#plan-before-changes) |
| **Power Write** | A switch that lets approved plans also change C++ and other source files and run Python scripts. Off after installation. | [Power Write](06_Permissions_And_Safety.md#power-write) |
| **Project rules** | Short instructions in `ProjectDocs/eXe/Rules` that the AI gets for every new plan in a project, for example naming rules. | [Project rules](03_Agent_Window.md#project-rules) |
| **Read back** | eXe checks a change by reading the new value from the editor or the file itself instead of trusting the AI's report. | [Result levels](03_Agent_Window.md#result-levels) |
| **Redirector** | A small leftover file Unreal creates when you move or rename an asset, so old references still work. **Fix Up Redirectors** in the Content Browser removes them. | [Capabilities](05_Capabilities.md#without-an-ai-provider) |
| **Result level** | How far eXe proved that a job reached its goal, from **Goal verified** down to **Execution finished** or **Failure**. | [Result levels](03_Agent_Window.md#result-levels) |
| **Revert** | Putting a changed file or asset back to the state before the job, from the copy eXe saved. | [Reverting changes](06_Permissions_And_Safety.md#reverting-changes) |
| **Scope** | Everything an approved plan may touch. eXe works inside it without asking again and asks you again for anything outside it. | [What an approval covers](06_Permissions_And_Safety.md#what-an-approval-covers) |
| **Sealed plan** | A plan that eXe has checked and fixed. Nothing in it can change anymore; a change needs a new or extended plan. | [How a job works](03_Agent_Window.md#how-a-job-works) |
| **Token** | The unit AI providers count and bill text in. A word is often one or two tokens. | [See what a chat costs](04_Connect_AI_Providers.md#see-what-a-chat-costs) |
| **Toolset** | A group of editor tools that an Unreal Engine plugin offers through Unreal's MCP server, for example for Blueprints or materials. | [Installation](01_Installation.md) |
| **Tunnel** | A program such as Cloudflare Tunnel that makes eXe on your PC reachable from the internet, so ChatGPT can use it. You run it yourself. | [Remote Access with ChatGPT](07_Remote_Access_ChatGPT.md#step-1-start-a-tunnel) |
| **Unreal Build Tool (UBT)** | Unreal's program that compiles C++ code. eXe starts it from your Engine installation for a full build. | [Full builds](06_Permissions_And_Safety.md#full-builds) |
| **Unreal MCP server** | The MCP server built into Unreal Engine 5.8. eXe works in the editor through it, so it must be running. | [Installation](01_Installation.md#step-2-start-unreals-mcp-server) |
| **World Partition, One File Per Actor** | An Unreal level setup that stores each actor in its own file. eXe keeps no copy of these files, so it cannot revert them. | [Reverting changes](06_Permissions_And_Safety.md#reverting-changes) |
| **YOLO** | A switch that lets eXe approve and run plans from local or signed-in AI clients without asking you, for up to 90 minutes per job. Off after installation. | [YOLO](06_Permissions_And_Safety.md#yolo) |

Previous: [FAQ](12_FAQ.md) · [Documentation Index](INDEX.md)
