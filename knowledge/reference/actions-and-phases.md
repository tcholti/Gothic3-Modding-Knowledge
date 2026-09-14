# Gothic 3 Combat Actions and Animation Phases

**Knowledge status:** Verified / established reference  
**Scope:** Project-relevant native `gEAction` and `gEPhase` values used in Gothic 3 combat/animation work

## Purpose

Provide a compact lookup for native action and phase values and document the most important interpretation rule: **runtime action identity outranks filename wording when they disagree**.

## Relevant `gEAction` values

| Value | Action |
|---:|---|
| 1 | `Attack` |
| 2 | `PowerAttack` |
| 3 | `QuickAttack` |
| 4 | `QuickAttackR` |
| 5 | `QuickAttackL` |
| 6 | `SimpleWhirl` |
| 10 | `WhirlAttack` |
| 11 | `PierceAttack` |
| 14 | `HackAttack` |
| 15 | `FinishingAttack` |
| 30 | `GetUpAttack` |
| 31 | `GetUpParade` |
| 39 | `AbortAttack` |

This is the currently promoted combat-relevant subset, not a claim that these are the only `gEAction` values in Gothic 3.

## Relevant `gEPhase` values

| Value | Phase |
|---:|---|
| 0 | `Raise` |
| 1 | `Hit` |
| 3 | `Recover` |
| 4 | `Begin` |
| 5 | `Loop` |
| 6 | `End` |

## Runtime action vs filename action

Do not infer engine behavior solely from the action text embedded in an animation filename.

Established examples:

### Dual SimpleWhirl

A Dual attack can execute native:

```text
gEAction_SimpleWhirl
```

while its exact Hit asset serializes:

```text
WhirlAttack
```

The runtime action remains the behavior authority.

### QuickAttackR / QuickAttackL

These values identify action variants. They do **not** universally identify which physical hand/source will cause damage.

### HackAttack vs FinishingAttack

Related asset naming can appear around Hack/Finishing resources, but factual runtime action `14` (`HackAttack`) and action `15` (`FinishingAttack`) must remain distinct.

## Practical rule for mods

When a script/plugin can obtain the native runtime values, use:

```text
exact gEAction
exact gEPhase
```

for behavior decisions.

Use filename action/phase fields for:

- asset lookup;
- animation authoring;
- debugging;
- identifying serialized resources.

This distinction prevents a mod from accidentally assigning one action family's gameplay semantics to another merely because their assets have related names.

## Related pages

- [`../animation/naming.md`](../animation/naming.md)
- [`use-types.md`](use-types.md)
- [`../engine/combat/combat-move.md`](../engine/combat/combat-move.md)

## Provenance

Promoted from `tcholti/Gothic3_Animation_Behaviors` at commit:

`9e8ea4034aa9d9ac10e3d6723795ce444f218404`

Primary source:

- `docs/ANIMATION_RULES.md` §§5, 7, 12
- `docs/ANIMATION_INDEX.md` §4

For complete enum declarations, consult the Gothic 3 SDK `GameEnum.h`; this page intentionally preserves the subset and interpretation rules already established through modding work.