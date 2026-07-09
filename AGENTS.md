# Repository Guidelines

## Project Structure & Planning

HorrorGem is an Unreal Engine 5.7 C++ horror game. `HorrorGem.uproject` defines the project and plugins; runtime code belongs in `Source/HorrorGem/`. Shared game classes are at the module root, while horror and shooter variants live in `Variant_Horror/` and `Variant_Shooter/`, with feature folders such as `AI/`, `UI/`, and `Weapons/`. Settings are in `Config/`; Unreal assets, maps, and Blueprints are in `Content/`.

Treat `docs/` as the persistent project memory. Before substantial work, read the relevant documentation. Update `docs/progress.md` after meaningful work; track risks, dependencies, and open questions in `docs/blockers.md`; record consequential design or technical choices in `docs/decisions.md`. Update architecture or design documents when implementation changes the agreed plan. Label assumptions clearly.

## Build, Test, and Development

Open `HorrorGem.uproject` with Unreal Engine 5.7 for development, Blueprint compilation, and Play-in-Editor testing. In Visual Studio, open `HorrorGem.sln`, select `Development Editor | Win64`, and build `HorrorGemEditor`.

For command-line builds, set `UE_ROOT` to the installed engine path:

```powershell
& "$env:UE_ROOT\Engine\Build\BatchFiles\Build.bat" HorrorGemEditor Win64 Development -Project="D:\UE5_projects\HorrorGem\HorrorGem.uproject" -WaitMutex
```

Regenerate project files from the `.uproject` context menu after adding source files or modules. No automated test framework is committed yet: compile the Editor target and exercise affected gameplay in Play-in-Editor. Put future automation in `Source/HorrorGem/Tests/` and name it for its behavior, e.g. `HorrorGem.AI.AlertState`.

## Code, Content, and Configuration

Follow the existing Unreal C++ style: tabs, braces on their own line, and matching `.h`/`.cpp` pairs. Use PascalCase for types and methods; retain `A`, `U`, and `F` Unreal prefixes and `b` for booleans. Use `UPROPERTY` and `UFUNCTION` metadata for editor or Blueprint-facing APIs.

Do not edit `Binaries/`, `DerivedDataCache/`, `Intermediate/`, or `Saved/`. Do not move, rename, or delete Unreal assets without approval. Keep configuration changes minimal and explain their impact; preserve current conventions before introducing plugins or frameworks.

## Commits and Handoffs

Only the initial project commit exists, so use concise imperative messages with an area prefix, such as `ai: add stalking state`. Pull requests should explain player impact, link the relevant issue or design note, list validation, and include screenshots or video for visual changes. At handoff, state what changed, what was verified, and remaining risks or blockers.
