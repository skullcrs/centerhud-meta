# Center HUD

Modular **client-side** HUD for Fabric. Curved bars around the crosshair,
floating combat numbers, nearby mob counts, speed/coords, elytra status, and
waypoints - drag everything into place in-game.

**License:** MIT (jars include the license text). Source is not published;
this repo is docs, changelog, issues, and release downloads only.

![Center HUD in combat](media/hud-desert-night.png)

## Why use it

Vanilla hearts and food sit in the way. Center HUD moves vitals next to the
crosshair, shows damage as scrolling text, and keeps awareness (mobs, look-at
target, combat timer) readable without covering the world.

## Features

- Player bars (health + absorption, hunger, armor, air/freeze, mount) - curved or straight, themes/gradients
- Scrolling combat text (damage, heal, crits, XP, effects)
- Hostile/passive counters and look-at stats
- Info panel: speed, coordinates, facing, combat timer
- Elytra durability / glide readout
- Waypoint arrow + waypoints screen
- Layout editor (**O**) - drag modules live
- Optional hide for overlapping vanilla HUD pieces

## Install

1. Fabric Loader for your Minecraft version
2. [Fabric API](https://modrinth.com/mod/fabric-api) and [Cloth Config](https://modrinth.com/mod/cloth-config)
3. Grab the matching jar from [Releases](https://github.com/skullcrs/centerhud-meta/releases) or [Modrinth](https://modrinth.com/mod/centerhud)
4. Optional: [Mod Menu](https://modrinth.com/mod/modmenu)

Config: Mod Menu → Center HUD, or `config/centerhud.json`.

## Supported Minecraft

| Minecraft | Notes |
| --- | --- |
| 26.2 | Java 25 |
| 26.1.2 | also listed for 26.1 / 26.1.1 |
| 1.21.11 | Java 21 |
| 1.21.1 | Java 21 (floor) |

## Links

- [Modrinth](https://modrinth.com/mod/centerhud)
- [Changelog](CHANGELOG.md)
- [Issues](https://github.com/skullcrs/centerhud-meta/issues)
