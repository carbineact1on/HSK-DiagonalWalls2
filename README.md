# HSK-DiagonalWalls2

HSK-balanced fork of **[Diagonal Walls 2](https://steamcommunity.com/sharedfiles/filedetails/?id=2859965620)** by Chevreau, tuned for the [Hardcore SK](https://github.com/skyarkhangel/Hardcore-SK) modpack.

Drop-in replacement that brings every wall, embrasure, sandbag, and floor variant in line with HSK's vanilla building patterns from `Core_SK/Defs/ThingDefs_Buildings/Buildings_Walls.xml` and `Buildings_Defences.xml` — same hit-points, work-to-build, stuff cost, and refined-alloy pipeline as native HSK walls.

## Requirements

- **RimWorld 1.5** (1.6 supported as well)
- **Hardcore SK Modpack**
- **Combat Extended** (no CE-specific changes — purely cosmetic walls/floors, but loads cleanly under CE)

## What Got Patched

### 🧱 Diagonal Walls (`DiagonalWallBase`)
| Stat | Upstream | HSK fork |
|---|---|---|
| MaxHitPoints | 300 | **350** |
| WorkToBuild | 135 | **350** |
| costStuffCount | 5 | **6** |

Matches HSK vanilla `Wall` — same defensive value as a native HSK straight wall.

### 🔫 Embrasures (`DiagonalEmbrasureBase`)
| Stat | Upstream | HSK fork |
|---|---|---|
| MaxHitPoints | 300 (inherited) | **480** |
| WorkToBuild | 150 | **800** |
| costStuffCount | 5 (inherited) | **8** |
| costList | — | **ComponentIndustrial 2** |
| stuffCategories | Metallic / Woody / Stony | **Woody / Stony / Bricks** |

Matches HSK vanilla `Embrasure` — proper sturdiness gate, requires components, no metal stuffing (HSK convention).

### 🛡 Sandbags (`DiagonalSandbags`)
| Stat | Upstream | HSK fork |
|---|---|---|
| WorkToBuild | 180 | **450** |
| costList | — | **SandResource 3** |

Matches HSK vanilla `Sandbags` — costs sand on top of fabric, takes proper time to build.

### 🟫 Floors
- **Paved Tile**: `Steel 1` → **`ConcreteResource 2 + ComponentIndustrial 1`**, research `Stonecutting` → **`Concrete_floor_C1`** (matches HSK `PavedTile`)
- **Steel Tile**: `Steel 4` → **`SteelBar 4`**
- **Silver Tile**: `Silver 35` → **`SilverBar 35`**
- **Gold Tile**: `Gold 35` → **`GoldBar 35`**
- **Stone tiles** (sandstone/granite/limestone/slate/marble): unchanged — already use `BlocksXxx` (HSK pattern ✓)

### ⚡ Conduit (`diagonalConduit`)
Inherits from HSK's `PowerConduit` directly — automatically gets `Wire 1` cost. Unchanged.

### 🚧 Fences
Already matched HSK pattern — unchanged.

## Installation

1. Subscribe to **[Diagonal Walls 2](https://steamcommunity.com/sharedfiles/filedetails/?id=2859965620)** on the Workshop (texture/asset content) and then disable it in your modlist
2. Clone or download this repo into your RimWorld `Mods/` directory
3. Enable `HSK-DiagonalWalls2` in your modlist (load order doesn't matter — pure XML-only fork)

⚠ **Do not enable the upstream Workshop version alongside this fork.** It's marked `<incompatibleWith>chv.DiagonalWalls2</incompatibleWith>` in `About.xml` — RimWorld will reject loading both.

When you stop playing HSK, switch back to the upstream Workshop version.

## How It Works

Pure XML edits to the def files in `1.5/Defs/` and `1.6/Defs/` — no DLL changes, no Harmony patches, no patch operations. Each wall/embrasure/sandbag/floor def has its `<statBases>`, `<costStuffCount>`, `<costList>`, and `<stuffCategories>` rewritten to match the equivalent HSK vanilla building's values. Raw ores (`Steel`, `Silver`, `Gold`) are swapped for refined alloys (`SteelBar`, `SilverBar`, `GoldBar`) so floors craft from HSK's smelter output instead of mining drops.

## Credits

- Original mod: **Chevreau** ([Workshop](https://steamcommunity.com/sharedfiles/filedetails/?id=2859965620))
- HSK conversion: **CarbineAction**
