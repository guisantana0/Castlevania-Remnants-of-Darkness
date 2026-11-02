# AGENTS.md

Godot 4.7 2D metroidvania ("Castlevania: Remnants of Darkness"), GDScript. Most game code lives in `SampleProject/`.

## Run / verify

- Open `project.godot` in **Godot 4.7.x** (installed here is 4.7.2). README's "4.6" is stale; `config/features` requires 4.7.
- Main scene: `res://SampleProject/extra_scenes/title_screen.tscn` (`run/main_scene`).
- CLI run: `godot --path .` (or `godot4`). No automated tests/lint/typecheck exist; verification is running the game and checking Godot's debug output.
- Export presets in `export_presets.cfg` (Windows/Android/Linux/macOS/Web); export path is outside the repo (`../../Castlevania.exe`).

## Structure

- `SampleProject/` — bulk of the game: scripts (`Scripts/`), scenes, enemies, items, menus, maps, resources.
- `scenes/` — a few top-level scenes (HUD, player).
- `rooms/` — legacy/old room builds; low value.
- `assets/` — images, spritesheets, audio.
- `addons/` — vendored Godot addons (Metroidvania System, G.U.I.D.E, input_helper, input_buffer, AsepriteWizard, kanban_tasks, levelshot, GDTerminal, godot-rapier2d). Treat as third-party; edit only when necessary.
- `guide_examples/` — G.U.I.D.E addon examples.

## Key wiring (from `project.godot`)

- Autoloads: `MetSys`, `Global` (`SampleProject/Scripts/Global.gd`), `InputBuffer`, `InputHelper`.
- Metroidvania System settings: `res://SampleProject/Resources/Settings.tres`.
- Enabled editor plugins: AsepriteWizard, GDTerminal, MetroidvaniaSystem (+EditorExtension), input_helper, kanban_tasks, levelshot.
- Physics engine is `GodotPhysics2D`; physics layers are named in `project.godot` (`[layer_names]`).

## Conventions / gotchas

- **Line endings: LF in git.** `core.autocrlf` set to `false` locally; committed `.gd`/`.tscn`/`.import` files are LF. Preserve existing line endings when editing.">
- **GDScript warnings are all disabled** (`gdscript/warnings/*=0` in `project.godot`) — do not treat warnings as failures or "fix" them wholesale.
- `.uid` files sit beside scripts; leave them; Godot regenerates/updates them.
- `.godot/` and `android/**` are gitignored (generated/build artifacts) — never commit them.
- Debug output / errors surface via Godot's console; there is no separate test suite.

## Remotes

- Origin now points to the personal mirror `git@github.com:guisantana0/Castlevania-Remnants-of-Darkness.git` (SSH). The original upstream `GianImpr/Castlevania-Remnants-of-Darkness` is no longer configured.
