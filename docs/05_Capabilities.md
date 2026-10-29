# Capabilities

This page lists what eXe can read and change in version 1.0.0. What works in a given project also depends on the enabled Engine plugins and on the AI model you use. When eXe has no capability for a task, it says so instead of guessing.

## Read and analyze (no approval needed)

- Project structure, modules, plugins and settings
- Blueprints: components, variables, functions and graphs
- C++ source files
- Assets, dependencies and references
- Levels and actors
- Output log, compile and build results

## Change (after approval)

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

## Built-in skills

eXe ships with skill guides for common Unreal tasks, for example Blueprints, materials, UMG, Niagara, State Trees, landscapes and PIE testing. The AI loads the matching guide when it needs it, which improves results with fewer tokens.

## Without an AI provider

The **Tools** view works without any AI. It reads the Content Browser selection, the folder open there or the open level, and changes nothing (except **Build project**).

| Tool | What it does |
|---|---|
| **Check assets** | Blueprint compile state, unconnected events and folder conventions for the selected assets, or for the open folder and its subfolders |
| **Check open level** | Finds actors stacked on exactly the same spot |
| **Explain Blueprint** | Components, variables, functions and what each graph calls (select exactly one Blueprint) |
| **Dependencies** | What the selected asset uses and what uses it. Useful before deleting or moving |
| **Clean-up report** | For the open Content Browser folder: broken references, leftover redirectors and assets nothing references |
| **Build project** | Closes the editor (Unreal asks to save) and builds the project with Unreal Build Tool. Open the project again yourself when the build has finished. If it failed, the view lists the compiler errors |

## Asset generation

Optional, under **Settings → Asset generation**. eXe can generate assets with your own key and credits:

- 3D models: **Meshy**, **Tripo**
- Images: **OpenAI**, **Stability AI**
- Sound effects: **ElevenLabs**
- Local servers you start yourself: `LOCAL_IMAGE` (OpenAI-compatible image server) and `LOCAL_3D` (trellis.cpp trellis-server with TRELLIS.2, textured GLB)

Before each generation, eXe names the service and asks you to confirm. Results are saved in the project's `GeneratedAssets` folder. To bring one into `/Game`, ask eXe to import it; that runs as a normal approved plan. eXe has no cloud of its own and never starts these servers.

Previous: [Connect AI Providers](04_Connect_AI_Providers.md) · [Documentation Index](INDEX.md) · Next: [Permissions and Safety](06_Permissions_And_Safety.md)
