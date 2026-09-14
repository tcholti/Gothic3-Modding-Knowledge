# Gothic 3 UseType to Animation-Token Reference

**Knowledge status:** Verified / established reference  
**Scope:** Raw `gEUseType` values and their serialized animation filename categories

## Purpose

Document cases where the engine's raw `gEUseType` spelling and the animation filename token are not 1:1.

This matters because mods that build or interpret animation names must use the serialized animation category rather than blindly inserting the raw enum name.

## Filename order

Animation filenames serialize the two animation-use fields in this order:

```text
LeftAnimationUseType_RightAnimationUseType
```

## Normalization table

| Raw `gEUseType` | Animation token |
|---|---|
| None | None |
| Action | Action |
| 1H | 1H |
| 2H | 2H |
| Arrow | Arrow |
| Bow | Bow |
| CrossBow | CrossBow |
| Bolt | Bolt |
| Fist | Fist |
| Shield | Shield |
| Armor | Armor |
| Helmet | Helmet |
| Staff | Staff |
| Amulet | Amulet |
| Ring | Ring |
| Cast | Cast |
| Potion | Potion |
| Plant | Bread |
| Meat | Meat |
| Fruit | Fruit |
| Bread | Bread |
| Bottle | Potion |
| Cup | Cup |
| Bowl | Bowl |
| Torch | Torch |
| Alarmhorn | Alarmhorn |
| Broom | Staff |
| Brush | Block |
| Lute | Lute |
| Rake | Staff |
| TrophyTeeth | TrophyTeeth |
| Valuable | Valuable |
| Smoke | Smoke |
| OrcPipe | OrcPipe |
| Scoop | Tool |
| Stick | Tool |
| Shovel | Staff |
| Hammer | Tool |
| Fan | Staff |
| Pan | Tool |
| Saw | Tool |
| TrophySkin | TrophySkin |
| Map | Letter |
| Book | Letter |
| Letter | Letter |
| Key | Key |
| Lockpick | Key |
| CarryFront | CarryFront |
| CarryShoulder | CarryShoulder |
| Pickaxe | 2H |
| TrophyFur | TrophyFur |
| Halberd | Staff |
| Axe | 2H |
| ITEM_E | ITEM_E |
| Modify | Modify |
| PhysicalFist | Fist |
| ITEM_H | ITEM_H |
| Anvil | Anvil |
| Forge | Forge |
| GrindStone | GrindStone |
| Cauldron | Cauldron |
| Barbecue | Barbecue |
| Alchemy | Alchemy |
| Bookshelf | Bookshelf |
| Bookstand | Bookstand |
| TakeStone | TakeStone |
| DropStone | DropStone |
| PickOre | PickOre |
| PickGround | PickGround |
| DigGround | DigGround |
| Field | Field |
| Repair | Repair |
| SawLog | SawLog |
| Lumberjack | Lumberjack |
| Bed | Bed |
| SleepGround | SleepGround |
| CleanFloor | CleanFloor |
| Dance | Dance |
| FanBoss | FanBoss |
| Boss | Boss |
| Throne | Throne |
| Pace | Pace |
| Bard | Bard |
| Stool | Stool |
| Bench | Bench |
| Waterpipe | Waterpipe |
| WaterBarrel | WaterBarrel |
| PirateTreasure | Stove |
| Campfire | Campfire |
| SitCampfire | SitCampfire |
| SitGround | SitGround |
| Smalltalk | Smalltalk |
| Preach | Preach |
| Spectator | Spectator |
| Stand | Stand |
| Guard | Guard |
| Trader | Trader |
| Listener | Listener |
| OrcDance | OrcDance |
| Stoneplate | Stoneplate |
| OrcDrum | OrcDrum |
| Door | Door |
| OrcBoulder | OrcBoulder |
| EatGround | EatGround |
| DrinkWater | DrinkWater |
| Pee | Pee |
| Chest | Chest |
| Shrine | Shrine |
| AttackPoint | AttackPoint |
| Roam | Roam |
| BODY_A | BODY_A |
| Beard | Beard |
| Hair | Hair |
| Head | Head |
| Body | Body |
| Flee | Flee |
| Talk | Talk |

## High-value non-identity mappings

The mappings most likely to surprise a modder include:

```text
Axe / Pickaxe                          -> 2H
Halberd / Rake / Shovel / Broom / Fan -> Staff
PhysicalFist                           -> Fist
Plant                                  -> Bread
Bottle                                 -> Potion
Map / Book                             -> Letter
Lockpick                               -> Key
PirateTreasure                         -> Stove
```

## Important limitation: serialization is not runtime mechanism identity

A normalized animation token tells you how the animation category is serialized. It does **not** prove that two raw engine UseTypes share the same runtime behavior.

The clearest example is:

```text
Fist         -> Fist
PhysicalFist -> Fist
```

Both can serialize as `Fist`, but that does not make `gEUseType_Fist` and `gEUseType_PhysicalFist` the same native damage mechanism.

Therefore:

> **Use normalization to match animation resources; use the factual raw runtime UseType and surrounding native state to identify engine behavior.**

## Related pages

- [`../animation/naming.md`](../animation/naming.md)
- [`actions-and-phases.md`](actions-and-phases.md)

## Provenance

Promoted from `tcholti/Gothic3_Animation_Behaviors` at commit:

`9e8ea4034aa9d9ac10e3d6723795ce444f218404`

Primary source:

- `docs/ANIMATION_RULES.md` §4
- `docs/ANIMATION_INDEX.md` §2

The source project intentionally distinguishes this serialization mapping from later runtime-mechanism research.