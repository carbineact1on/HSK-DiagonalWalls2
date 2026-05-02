# HSK-DiagonalWalls2

HSK-balanced fork of [Diagonal Walls 2](https://steamcommunity.com/sharedfiles/filedetails/?id=2859965620) by Chevreau.

Drop-in replacement that brings the mod's wall/embrasure/sandbag stats in line with HSK's vanilla wall pattern (`Core_SK/Defs/ThingDefs_Buildings/Buildings_Walls.xml` and `Buildings_Defences.xml`).

## Conversions applied

### Walls (`DiagonalWallBase`)
| Stat | Upstream | HSK fork |
|---|---|---|
| MaxHitPoints | 300 | **350** |
| WorkToBuild | 135 | **350** |
| costStuffCount | 5 | **6** |

Matches HSK's vanilla `Wall` (300→350 HP, 35→350 work, costStuffCount 6).

### Embrasures (`DiagonalEmbrasureBase`)
| Stat | Upstream | HSK fork |
|---|---|---|
| MaxHitPoints | 350 (inherited) | **480** |
| WorkToBuild | 150 | **800** |
| costStuffCount | 6 (inherited) | **8** |
| costList | — | **ComponentIndustrial 2** |
| stuffCategories | Metallic / Woody / Stony | **Woody / Stony / Bricks** |

Matches HSK's vanilla `Embrasure` (480 HP, 800 work, 8 stuff, 2 ComponentIndustrial, no metal stuffing).

### Sandbags (`DiagonalSandbags`)
| Stat | Upstream | HSK fork |
|---|---|---|
| WorkToBuild | 180 | **450** |

Matches HSK's vanilla `Sandbags` work cost.

### Fences (`DiagonalFence`, `ConnectorFenceL/R`)
Already matched HSK pattern — left untouched.

### Conduit (`diagonalConduit`)
Inherits from vanilla `BuildingBase` — left untouched.

### Floors
Costs already matched HSK vanilla equivalents — left untouched.

## Drop-in replacement

`<incompatibleWith>chv.DiagonalWalls2</incompatibleWith>` — RimWorld will reject loading both at once. Disable the upstream Workshop mod and enable this fork.

## When to remove

If you stop playing HSK, switch back to the upstream Workshop version.

## Credits

- Original mod: **Chevreau** ([Workshop](https://steamcommunity.com/sharedfiles/filedetails/?id=2859965620))
- HSK conversion: **CarbineAction**
