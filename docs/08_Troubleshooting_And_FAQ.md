# Troubleshooting and FAQ

## The header stays on "Starting..." or Settings shows "The eXe core is not running"

**Likely causes:** a required Engine plugin is disabled, or a Python dependency conflict with another plugin.

1. Check **Edit → Plugins**: Python Editor Script Plugin, Model Context Protocol and Toolset Registry are enabled.
2. Open **Window → Output Log** and filter for `eXe`. A dependency conflict is named there.
3. Close the editor and open the project again. Do not run `pip install` and do not reload Python modules by hand.

## "Unreal MCP server not running"

Unreal's MCP server is not started.

1. Open **Edit → Editor Preferences → Model Context Protocol** and enable **Auto Start Server**.
2. To start it right away, run the console command `ModelContextProtocol.StartServer`.
3. Check that the port and path match the address shown under **Settings → Connection**.

Hover over the **Unreal MCP** line in **Settings → Connection** to see the exact steps for your case, also when toolsets are missing.

## The chat says no AI is connected or the key was rejected

Open the AI controller in **Chat**, choose the provider, enter the model ID and key and click **Save**. Check that the model ID is spelled exactly as your provider lists it.

## "The AI provider could not be reached"

Check the address and your internet connection. For a local model, check that your local server is running and the address is correct.

## "The model did not produce a usable tool call"

Small or older models often struggle with planning. Send the message again or choose a stronger model.

## "No plan has been submitted yet"

The AI talked about a plan but did not submit it. Ask it to submit its plan, or choose a stronger model.

## Claude Code, Codex or Claude Desktop does not see eXe

1. In **Settings → AI clients**, click **Connect / repair**, then **Check status**.
2. Close command windows that were already open and restart Claude Desktop.
3. Start Claude Code or Codex with the copied line (**Copy Claude Code command** or **Copy Codex command**) in a new Command Prompt (cmd). Install and sign in to the client yourself.

## The editor did not reopen after a build

This is expected. eXe never restarts the editor. Open the project yourself; the job then continues. If the build failed, eXe shows the compiler errors (for **Build project**, in the **Tools** view).

## A job ended with "Goal not independently verified"

eXe did the work but could not confirm the goal with its own read-back, for example a visual change. Check the result in the editor.

## An editor step was interrupted

If the editor closed or crashed during a step, eXe shows **Inspect interrupted step** and repeats nothing automatically. Check the project, then continue or start a new task.

## Two editors are open

Each editor runs its own eXe with its own jobs and port. **Settings → Connection** shows the address of each.

## FAQ

**Do I need an eXe account?** No.

**Does eXe send my project to eXe servers?** No. There are no eXe servers. Data goes only to the AI provider and services you configure. See [Privacy, Costs and Third-Party Software](11_Privacy_Costs_And_Third_Party.md).

**What does it cost to use?** The plugin price once on Fab. AI usage is billed by your provider.

**Can I use it without an AI provider?** Yes, the **Tools** view works without any AI.

**Does it work on macOS or Linux?** Not in version 1.0.0.

**Does it work when the editor is closed?** No. eXe runs inside the editor.

## How to ask for help

Post in the `#support` channel on [Discord](https://discord.gg/ebW7kKCC25) or write to [exeagent.support@gmail.com](mailto:exeagent.support@gmail.com). Please include:

- eXe Agent version and Unreal Engine version
- AI provider and model, or the AI client you used
- What you did, what you expected and what happened
- For a job: the text from **Copy for support** in **Jobs**
- Relevant lines from the Output Log (filter for `eXe`)

Do not post API keys or private project content.

Previous: [Remote Access with ChatGPT](07_Remote_Access_ChatGPT.md) · [Documentation Index](INDEX.md) · Next: [Known Issues and Limitations](09_Known_Issues_And_Limitations.md)
