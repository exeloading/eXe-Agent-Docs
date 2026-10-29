# Remote Access with ChatGPT

You can use eXe from ChatGPT on the web or on your phone. ChatGPT then talks to the eXe instance on your PC through a tunnel that you run yourself. eXe does not provide or start a tunnel, a sign-in service or any cloud service. Remote access is off after installation.

Claude Code, Codex and Claude Desktop on the same PC do not need a tunnel ([Connect AI Providers](04_Connect_AI_Providers.md)).

## What you need

- A ChatGPT plan that supports custom MCP connectors. Check OpenAI's current plan details.
- A tunnel program, for example Cloudflare Tunnel (`cloudflared`).
- Recommended: your own sign-in service (OAuth), for example Auth0, Microsoft Entra or Keycloak, so only you can use the connection.

## Step 1: Start a tunnel

Point the tunnel to the local eXe address. Example with a Cloudflare quick tunnel:

```text
cloudflared tunnel --url http://127.0.0.1:8798
```

The tunnel shows an address like `https://<name>.trycloudflare.com`. Your **tunnel address** for eXe and ChatGPT is that address with `/mcp` at the end, without a port. A quick tunnel gets a new address on every start; a named tunnel with your own domain keeps it.

The tunnel must point to eXe (port 8798 by default), never directly to Unreal's MCP server.

## Step 2a: With sign-in (recommended)

In your sign-in service:

1. Create an API whose identifier is exactly your tunnel address, for example `https://<name>.trycloudflare.com/mcp`.
2. Add the permission `exe.mcp` to that API.
3. Create an application for ChatGPT and allow it to use the API with `exe.mcp`. Its client ID and secret go into ChatGPT, not into eXe.

In eXe, under **Settings → ChatGPT and remote access → ChatGPT / tunnel access with sign-in (OAuth)**:

1. Enter the **Tunnel address** and the **Sign-in service** (for example `dev-abc123.eu.auth0.com`).
2. Click **Check**. eXe reads the sign-in service and tells you in plain text what is missing.
3. Click **Save**, then close the editor and open the project again. Sign-in takes effect when the editor starts.

eXe stores no client secrets or tokens. **Status** shows the saved setting. **Remove sign-in** removes it; after the next editor start, the setting without sign-in applies again.

If **Check** reports that dynamic client registration is on, ChatGPT creates a new third-party app on every connection, and each one must be allowed to use the API separately. Recommended: turn it off in the sign-in service and enter your own client in ChatGPT.

## Step 2b: Without sign-in (short tests only)

Under **ChatGPT / tunnel access without sign-in**, choose a level. It applies immediately and stays after restarts.

| Level | What anyone with the tunnel address can do |
|---|---|
| **Off** | Nothing (default) |
| **Read + plan** | Read the project and prepare plans. Approval stays with you in Unreal. |
| **Approve + execute** | Also approve plans and run changes. eXe shows a warning and you must confirm it before this level applies. |

When sign-in is active, this switch does not apply. YOLO never covers access without sign-in.

## Step 3: Connect ChatGPT

1. In ChatGPT, add a custom MCP connector with your tunnel address (ending in `/mcp`).
2. Choose OAuth if you set up sign-in, otherwise no authentication.
3. Ask: `Run exe_loading_health.`

Expected result: ChatGPT reports a healthy connection to your project.

## Security

- Without sign-in, anyone who knows the tunnel address gets the level you chose. Use it only for short tests and set it back to **Off**.
- Changes still need an approved plan, unless you chose **Approve + execute**.
- Stop the tunnel when you do not need it.

## Common problems

| Symptom | Cause | Fix |
|---|---|---|
| Sign-in works, eXe answers `invalid_token` | API identifier is not exactly the tunnel address | Set the identifier to exactly `https://<address>/mcp` |
| Nothing works after restarting the tunnel | A quick tunnel got a new address | Enter the new address in eXe, the sign-in service and ChatGPT, or use a named tunnel |
| Setting saved, but no effect | Editor not restarted after saving sign-in | Close the editor and open the project again |
| eXe says environment variables override the setting | Old `EXE_LOADING_*` variables in Windows | Remove them and restart the editor |

Previous: [Permissions and Safety](06_Permissions_And_Safety.md) · [Documentation Index](INDEX.md) · Next: [Troubleshooting and FAQ](08_Troubleshooting_And_FAQ.md)
