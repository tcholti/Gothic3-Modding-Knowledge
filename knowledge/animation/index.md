# Gothic 3 Animation Knowledge

**Knowledge status:** Established reference / promoted knowledge  
**Scope:** Native Gothic 3 animation naming and runtime interpretation

## Purpose

Route common animation questions to the smallest useful page.

The most important general rule is:

> **Animation filenames are valuable serialized asset contracts, but runtime native action, phase, UseType and current-motion state should be preferred when behavior depends on actual engine semantics.**

A filename can describe how an asset is named without uniquely identifying the runtime mechanism that is executing it.

## Start here

| Question | Page |
|---|---|
| What do the fields in a Gothic 3 animation filename mean? | [`naming.md`](naming.md) |
| Which native attack action or animation phase is this? | [`../reference/actions-and-phases.md`](../reference/actions-and-phases.md) |
| How do raw `gEUseType` values map to animation filename tokens? | [`../reference/use-types.md`](../reference/use-types.md) |
| Where can I find tested animation/combat engine addresses? | [`../reference/tested-rvas.md`](../reference/tested-rvas.md) |
| How does persisted CombatMove execution work? | [`../engine/combat/combat-move.md`](../engine/combat/combat-move.md) |

## Core interpretation rules

### Animation family is not the same thing as player identity

The first token is the animation/resource family, for example `Hero`, `Demon` or `Goblin`.

`Hero` is not player-only. Compatible human NPCs can use Hero-family resources.

### Filename action text is not always runtime action truth

Known cases demonstrate that serialized asset naming and the factual native `gEAction` can differ.

Examples include:

- Dual attacks that execute native `gEAction_SimpleWhirl` while the exact Hit asset serializes `WhirlAttack`;
- `QuickAttackR` / `QuickAttackL`, which identify native action variants but do not by themselves identify the physical damage source;
- related Hack/Finishing asset naming, where the runtime action must remain authoritative.

### Left/right filename metadata is not a physical-source selector

The final `L` / `R` token strongly correlates with logical hit/attack direction, but tested Torch+1H and Dual cases show that it must not be treated as a universal selector for the physical collision hand/source.

### Serialized UseType token is not always raw enum spelling

Several raw `gEUseType` values normalize to another animation token. For example:

```text
Axe / Pickaxe                          -> 2H
Halberd / Rake / Shovel / Broom / Fan -> Staff
PhysicalFist                           -> Fist
Plant                                  -> Bread
Bottle                                 -> Potion
Map / Book                             -> Letter
Lockpick                               -> Key
```

See [`../reference/use-types.md`](../reference/use-types.md) for the full promoted mapping.

## Provenance

Promoted from `tcholti/Gothic3_Animation_Behaviors` at commit:

`9e8ea4034aa9d9ac10e3d6723795ce444f218404`

Primary source authorities:

- `docs/ANIMATION_RULES.md`
- `docs/ANIMATION_INDEX.md`

The source project's detailed evidence remains the deeper provenance layer.