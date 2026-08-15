# Complete Fire Red Upgrade — Mod

A personal mod built on top of the [Complete Fire Red Upgrade](https://github.com/Skeli789/Complete-Fire-Red-Upgrade) (CFRU) engine for Pokémon FireRed. The goal is a **single, complete playthrough** where every catchable Pokémon and every event legendary is obtainable, with a friendlier early-game experience.

> **Legal / License notice**
> By using this repository or any of its assets you consent to never making money off your game — that includes pay-walls **and optional donations** (ko-fi, Patreon, etc.). It is also illegal to profit off of an IP you don't own. This project is for personal/fan use only.

---

## Table of Contents

- [Mod Features](#mod-features)
- [Base CFRU Features](#base-cfru-features)
- [Getting Started](#getting-started)
- [Configuration](#configuration)
- [Notes](#notes)

---

## Mod Features

Everything below was added on top of the base CFRU engine.

### 1. All 151 Kanto Pokémon catchable in one game
LeafGreen-exclusive species were added to FireRed's wild tables (replacing duplicate slots, so no FireRed-exclusive was lost). Full dex completion is now possible with a single copy of the game.

| Species | Where to find |
|---|---|
| Sandshrew | Routes 4, 8, 11 |
| Vulpix | Route 7, Pokémon Mansion |
| Bellsprout / Weepinbell | Routes 5, 6, 7, 12, 24 |
| Pinsir | Safari Zone |
| Magmar | Mt. Ember |
| Slowpoke / Slowbro | Seafoam Islands (water) + fishing |
| Staryu | Fishing (common routes) |
| Kabuto | Fishing (rare, Route 4 & friends) |
| Marill | Ruin Valley (land + water) |
| Misdreavus | Lost Cave |
| Sneasel | Icefall Cave |
| Remoraid | Sevii Islands (fishing) |
| Mantine | Sevii Islands (water) |
| **Mew** | **Rare fishing in Cerulean Cave** |

### 2. Event legendaries without the events
FireRed already contains all the event maps, but the required items were only distributed between 2004–2009. They are now granted automatically **after your first Hall of Fame entry**:

- **Deoxys** (Lv. 30) — Birth Island, via the **Aurora Ticket**
- **Lugia** (Lv. 70) — Navel Rock, via the **Mystic Ticket**
- **Ho-Oh** (Lv. 70) — Navel Rock, via the **Mystic Ticket**

(The ferry to both islands departs from Vermilion City.)

### 3. 2.5× EXP for the player's Pokémon
Experience gain is multiplied by **2.5** (`×5 ÷ 2`) for all of your Pokémon, in every battle (wild, trainer and capture). The values can be tweaked in `src/config.h`.

### 4. Starter Pokémon on Route 1
**Bulbasaur, Charmander and Squirtle** appear as rare wild encounters (slots 9–11) on Route 1. Since Route 1 is only reachable after Professor Oak gives you your first partner, this naturally unlocks once you start your journey — letting you catch the other two starters.

### 5. Custom battle backgrounds
20 custom battle terrain backgrounds (Grass, Forest, Cave, Volcano, Space, etc.) were added under `graphics/Backgrounds/Battle_Terrain/`.

### 6. Applied patches (in `ips/`)
- **BW-style Menus** combo patch
- **Final Wood** tileset
- **EXP All**
- **HGSS-style tiles** (Omega Fix)

> The `Dynamic_Surfing_FR.ups` patch is kept in `ips/` but was **not** applied.

---

## Base CFRU Features

The mod is built on the CFRU engine, which upgrades FireRed to a Gen 8 battle system:

- Battle engine upgraded to Gen 8 (all moves, abilities, items and item effects through Gen 8)
- Complete move animations and vastly improved AI
- Z-Moves, Mega Evolution / Primal Reversion / Ultra Burst
- Ability pop-ups and Hidden Abilities
- Expanded Poké Balls and Battle Terrain
- Totem Pokémon, wild double battles, Multi Battles
- New evolution methods and expanded learnsets
- Updated Exp. Share, Shiny Charm + Oval Charm, level scaling
- Battle Frontier/Facilities, Swarms, Roaming Pokémon
- Day/Night/Seasons, DexNav, Follow Me, character customization
- Expanded PC Boxes (up to 25), expanded save-block
- Fairy Type, reusable TMs, move reminder up to 50 moves
- And much more — see the [official CFRU repo](https://github.com/Skeli789/Complete-Fire-Red-Upgrade)

---

## Getting Started

### Windows
See the [CFRU installation wiki](https://github.com/Skeli789/Complete-Fire-Red-Upgrade/wiki/Windows-Installation-Instructions).

### Linux / macOS
1. Install [devkitPro](https://devkitpro.org/wiki/Getting_Started) and add `${DEVKITARM}/bin/` to your `PATH`.
2. Install Python 3.6+.
3. Get a clean FireRed (U) ROM, put it in this directory and rename it to **`BPRE0.gba`** (a pre-built copy is also included in this repo).
4. Build:
   ```bash
   python3 scripts/make.py
   ```
5. The result is **`test.gba`** (plus a generated `offsets.ini`).

---

## Configuration

Personalized options live in **`src/config.h`** — just comment/uncomment lines. The most relevant for this mod:

```c
#define EXP_MULTIPLIER_NUM 5   // EXP multiplier numerator (5/2 = 2.5x)
#define EXP_MULTIPLIER_DEN 2   // EXP multiplier denominator
```

---

## Notes

- The compiler only recompiles the files you changed.
- Changes to header files require cleaning `build/` first (see "Engine Scripts" in the CFRU documentation).
- `BPRE0.gba` is the patched base ROM; `test.gba` is the build output and is **not** tracked.
