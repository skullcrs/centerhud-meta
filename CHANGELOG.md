# Changelog

All notable changes to this project are documented here. The format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and the project uses
[semantic versioning](https://semver.org/) independently of Minecraft's versions.

Every entry that is specific to one Minecraft version must name it.

## [Unreleased]

## [0.3.0] - 2026-08-09

Supported Minecraft: 26.2, 26.1.2, 1.21.11, 1.21.1.

### Added

- Configurable SCT / HUD number suffixes (e.g. XP as `+5xp`); per-kind strings
  in Cloth Config, plus optional bar and look-at suffixes.
- Absolute drag layout (Inventory HUD-style UX from public docs only): press O,
  drag any outlined module; labels show live X,Y. Positions stored as pixels
  from the top-left (Cloth exposes the same values).
- Mod Menu / Cloth: Edit layout and Reset layout buttons on the Core tab.
- Options to hide vanilla health, hunger, armor, air, and mount bars so they
  do not duplicate Center HUD bars.
- SCT critical hits (CRIT / ENCHANTED_HIT particles): color, prefix, suffix,
  scale, outline, glow; plus global SCT glow/outline toggles.
- HUD theme presets (Classic, Neon Aura, Ember, Ice, Toxic, Gold) with Apply
  theme; Neon Aura enables bar aura + gradients by default.
- Per-bar solid or two-color gradient fills (health, hunger, armor, air, mount).
- Configurable SCT stack gap, lane gap, and lifetime.
- Configurable speed meter (total / horizontal / vertical) with drag layout,
  now grown into an info panel with coordinates and compass facing rows and
  a configurable unit (blocks/s, km/h, mph).
- Elytra HUD: durability percent with threshold colors and low-durability
  blink (warn percent configurable), glide speed and pitch (optional fly-only).
- Elytra durability as an optional bar in the bar cluster while equipped
  (Elytra Bar HUD-inspired, public mod page only).
- Waypoint arrow (TomTom-inspired, public addon page only): rotating pointer
  with name, distance, and vertical delta; Waypoints screen (keybind or config
  button) to enter X/Y/Z, save locations, and pick or delete saved ones.
- Look-at detailed NPC/player stats (armor, absorb, effects, food/sat).
- SCT float effects: blink, wobble rotation, spin; crit horizontal spread and
  optional crit merge.
- Shader-aware fancy bars (Iris pack auto / always / off): sheen + pulsed aura.
- Info panel combat timer (`Combat Xs`) while in combat, with wear-off countdown.
- Option to hide vanilla status-effect icons (Core tab).

### Changed

- Layout positions migrated off center-relative offsets; existing configs reset
  to auto layout once (re-drag to place).
- Layout editor hint moved to the top of the screen (was under the hotbar).
- SCT kinds use horizontal lanes and stable slots so damage/heal/absorb (and
  similar pairs) no longer overlap on one column.
- Theme preset is a named dropdown (Classic, Neon Aura, Ember, Ice, Toxic,
  Gold) instead of a numeric id field.
- Speed readout is computed from per-tick position deltas instead of
  `getDeltaMovement()`, so it stays correct in creative flight, while riding,
  and across game-mode changes.
- Health number placement is configurable (left / under / right / above);
  default is under the health bar so extra left-side bars do not crowd it.
- Mod Menu action buttons (Edit layout, Reset layout, Apply theme, Waypoints)
  are Cloth list entries on the Core tab instead of footer widgets.

### Fixed

- Saving Mod Menu / Cloth Config no longer forces custom HUD positions to
  `(0,0)` (bars stuck on the top-left edge). Config v3 sanitizes broken
  custom flags on load; drag or the "use custom position" toggle still enables
  placement.
- Apply theme now flushes Cloth widgets first, so changing the theme id and
  pressing Apply theme updates bar/SCT colors immediately.
- Rapid crit SCT floats fan out / skip merge by default so they stop stacking
  on one pixel.
- A HUD module that throws during rendering is isolated and logged once
  instead of silently blanking every module registered after it (candidate
  cause of the speed meter / elytra HUD disappearing).
- Mod Menu Edit layout / Reset / Apply theme / Waypoints buttons work again
  (footer widgets sat under Cloth's list and never received clicks).
- Global scale no longer pushes modules under the hotbar or off-screen;
  positions clamp adaptively to the scaled viewport.
- Incoming SCT now counts absorption loss as damage (cactus / fire / magma
  often hit golden hearts first, so the bar moved with no float).
- Incoming SCT no longer marches off the top of the screen during sustained
  env damage: stack slots are reused, stacks grow opposite the scroll
  direction, and Y is clamped on-screen.
- Layout editor hit-testing inverse-transforms mouse under global scale, and
  every handle has a larger shaded grab box (fixes tiny Elytra / Info targets).
- Curved hunger bar no longer shows a straight saturation stub that filled the
  hollow of the curve (saturation now follows the same bow on the outer edge).
- Empty armor bars are hidden instead of drawing a second outline.

## [0.2.0] - 2026-08-08

Supported Minecraft: 26.2, 26.1.2, 1.21.11, 1.21.1.

### Added

- IceHUD-inspired curved player bars (default), with Cloth controls for style
  (straight/curved), thickness, length, gap, side gap, curve amount, borders,
  and per-stat colors (health, absorption, hunger, saturation, armor, air,
  freeze, mount, numbers, background).
- In-game HUD layout editor (keybind "Edit HUD layout"): drag bars, look-at,
  effects, SCT areas, and entity counters; Cloth Config exposes matching offsets.
- Optional suppression of vanilla `DAMAGE_INDICATOR` particles while SCT is on
  (Cloth toggle, default on).
- Cloth Config color pickers for all SCT event colors.

### Changed

- Global scale now applies to every HUD module (not only player bars), via a
  pose-stack scale around the HUD pivot.
- SCT effect-remove lines use the effect display name instead of the raw
  description id.

## [0.1.0] - 2026-08-08

Supported Minecraft: 26.2, 26.1.2, 1.21.11, 1.21.1.

### Added

- Project generated from the default_mod multi-version Fabric template,
  targeting Minecraft 26.2, 26.1.2, 1.21.11, 1.21.1.
- Client-only modular HUD with Cloth Config + Mod Menu integration.
- IceHUD-style bars: player health (with absorption), hunger/saturation, armor,
  air/freeze, mount health - each toggleable.
- Look-at target info and status-effect list modules.
- MobCount-style hostile/passive entity counters with radii and keybinds.
- MSBT-inspired scrolling combat text (incoming / outgoing / notify) with merge
  and spam controls, driven by client-visible state only.
- Mod icon (`assets/centerhud/icon.png`) referenced from `fabric.mod.json`.
- Floor join-smoke helpers: `testserver_extra_mods` pulls Cloth Config into the
  `1.21.1` standalone server; Loom `-PsmokeServer=<host>` quick-plays
  multiplayer on remap nodes.

[Unreleased]: https://github.com/skullcrs/centerhud-meta/compare/v0.3.0...HEAD
[0.3.0]: https://github.com/skullcrs/centerhud-meta/releases/tag/v0.3.0
[0.2.0]: https://github.com/skullcrs/centerhud-meta/releases/tag/v0.2.0
[0.1.0]: https://github.com/skullcrs/centerhud-meta/releases/tag/v0.1.0
