# Capabilities

This page lists what eXe can read and change in version 1.0.0. What works in a given project also depends on the enabled Engine plugins and on the AI model you use. When eXe has no capability for a task, it says so instead of guessing.

## Read and analyze (no approval needed)

- Project structure, modules, plugins and settings
- Blueprints: components, variables, functions and graphs
- C++ source files
- Assets, dependencies and references
- Levels and actors
- Output log, compile and build results

## Change (directly for small requests, otherwise after you approve the plan)

| Area | Examples |
|---|---|
| Blueprints | Add or change variables, default values, components, functions with parameters and graph nodes; compile, save and read back |
| C++ | Create and edit classes and source files; compile; full build of the project. Needs **Power Write** ([Permissions and Safety](06_Permissions_And_Safety.md)) |
| Assets | Create, rename, move, import and configure assets |
| Materials | Create materials and material instances, set parameters |
| UMG | Create and edit Widget Blueprints, texts and properties |
| Animation | Animation Blueprints, montages, sequences, skeletons |
| Gameplay | Enhanced Input, Gameplay Tags, State Trees, Behavior Trees, enums and structs |
| Levels | Place, move and configure actors; blockouts |
| Audio and VFX | MetaSounds, Sound Cues, Niagara systems and emitters |
| World | Landscape, landscape materials, foliage, PCG |
| Testing | Play in Editor runs with input, log and state checks and a screenshot after game steps; multiplayer runs with several clients |

Example requests:

- `Add a float variable Stamina with default 100 to BP_PlayerCharacter.`
- `Create a material instance of M_Base named MI_Red and set BaseColor to red.`
- `Place five point lights along the corridor in the open level.`
- `Find the errors in the output log and fix their cause.`

## Built-in workflow guides

eXe gives the AI five short workflow guides: plan, execute, verify, inspect and debug. The AI loads the matching guide only when it needs it, which keeps requests small.

## Without an AI provider

The **Tools** view works without any AI. It reads the Content Browser selection, the folder open there or the open level, and changes nothing (except **Build project**).

| Tool | What it does |
|---|---|
| **Check assets** | Blueprint compile state, unconnected events and folder conventions for the selected assets, or with nothing selected for the open folder and its subfolders |
| **Check open level** | Finds actors stacked on exactly the same spot |
| **Explain Blueprint** | Components, variables, functions and what each graph calls (select exactly one Blueprint) |
| **Dependencies** | What the selected asset uses and what uses it. Useful before deleting or moving (select exactly one asset) |
| **Clean-up report** | For the open Content Browser folder: broken references, leftover redirectors and assets nothing references |
| **Build project** | Closes the editor and builds the project with Unreal Build Tool (see below) |

Results come with buttons that take you there: **Show in Content Browser**, **Show unused in Content Browser**, **Open** an asset or **Select** stacked actors in the level.

Details:

- **Check assets** with nothing selected checks the first 200 assets of the open folder and its subfolders. In a larger folder it says so; open a subfolder to check the rest. The folder conventions it reports: not stored under `/Game`, a Blueprint stored in a `Data` folder, a Data Asset stored outside a `Data` folder, a Widget Blueprint stored outside a `UI` folder, an Animation Blueprint stored outside an `Animation` folder. Conventions are hints, not errors.
- **Clean-up report:** the list **Without any reference** shows candidates, not proof. Assets loaded by C++ path strings, config files or cooking rules look unused here; levels and primary assets are left out. Delete through the Content Browser, which checks references again. To remove leftover redirectors, right-click the folder in the Content Browser and choose **Fix Up Redirectors** (with source control, check the files out first).
- **Build project:** eXe asks first. Then the editor closes (Unreal asks you to save unsaved work) and Unreal Build Tool runs in a console window titled **eXe Full Build: Unreal Build Tool is running. When this window closes, reopen your project.** When that window has closed, open the project again. The **Tools** view then shows **Last build (...) succeeded.** or lists the compiler errors. If you click **Cancel** when Unreal asks to save, nothing is built and Unreal shows **Build cancelled: the editor stayed open, nothing was built.** In a Blueprint-only project eXe tells you that a build is usually only needed for C++ plugins in its `Plugins` folder.

## Asset generation

Optional, under **Settings → Asset generation**. eXe can generate assets with your own key and credits, or with a local server you start yourself:

| Kind | Services |
|---|---|
| 3D models (`.glb`) | **Meshy**, **Tripo**, **Local 3D server** (trellis.cpp trellis-server with TRELLIS.2) |
| Images (`.png`) | **OpenAI (images)**, **Stability AI (images)**, **Local image server** (OpenAI-compatible image server) |
| Sound effects (`.mp3`) | **ElevenLabs (sound effects)** |

How to generate an asset:

1. Choose the service. For a cloud service, paste your API key and click **Save key** (saved for your Windows user). For a local server, enter its address or leave the field empty for the default (`http://127.0.0.1:7860` for images, `http://127.0.0.1:8081` for 3D).
2. Optional: enter a model ID and click **Save settings**. Empty uses eXe's default for that service. For the local 3D server, this field is the resolution: `512` (default), `1024` or `1536`. Higher values take much longer.
3. Describe the asset, for example `a weathered wooden barrel with iron bands`, and optionally enter a **File name**.
4. Click **Generate**. For a cloud service, eXe names the service and asks you to confirm, because the provider bills your account. For a local server, eXe confirms that nothing leaves your PC.
5. eXe shows **Started · the result will be ... · click Check for progress**. Click **Check** to see the progress. A generation can take up to 15 minutes.
6. The file is saved in your project under `GeneratedAssets/<service>/`. **Copy folder path** copies the folder. To bring the file into `/Game`, ask eXe in the chat to import it; that runs as a normal approved plan.

Good to know:

- Meshy creates a preview model without the extra texture refinement step. Tripo reports the credits a run used.
- The local 3D server turns a text into a picture on your local image server first, so both must run.
- eXe has no cloud of its own and never starts these servers.

## Blender and your own MCP servers

Optional, under **Settings → Blender and your own MCP servers**.

### Blender

eXe can read your open Blender scene and bring models into the project. Changes run only through eXe, like every other change.

1. In Blender, install the free open-source add-on MCP for Blender (`blender-mcp`) and turn on its server.
2. Keep Blender open and click **Check Blender**.

Expected: **Blender is ready (port 9876). You can now ask eXe about your Blender scene.** If it says **Blender is not reachable**, open Blender and turn on the add-on's server. eXe never starts Blender.

### Your own MCP servers

You can give Claude Code and Codex extra tools from your own MCP servers when you start them with the copied command. The eXe chat does not use them.

1. Enter a **Name** (letters, numbers, `-` or `_`) and a **Command or local address**, for example the name `blender` with the command `uvx mcp-for-blender`, or a server on this PC such as `http://127.0.0.1:9000/mcp`.
2. Click **Add**. Up to 8 servers; **Remove** deletes one.
3. Copy the start command again under **AI clients** so the client gets the change.

These tools run outside eXe's plans: eXe cannot check, approve or revert what they do. Your client asks you before each use, so add only servers you trust. Only addresses on this PC are allowed, and never enter keys here.

Previous: [Connect AI Providers](04_Connect_AI_Providers.md) · [Documentation Index](INDEX.md) · Next: [Permissions and Safety](06_Permissions_And_Safety.md)
