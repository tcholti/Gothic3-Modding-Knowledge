# Gothic 3 Animation Filename Structure

**Knowledge status:** Verified / established reference  
**Scope:** Native Gothic 3 animation resource naming; runtime semantics remain authoritative where filenames are ambiguous

## Purpose

Explain the fields commonly encoded in Gothic 3 animation names and the limits of filename-based inference.

## Canonical example

```text
Demon_Stand_None_2H_P1_Attack_Hit_N_Fwd_00_%_00_P0_150_L
```

Current field interpretation:

```text
AnimationFamily
AniState
LeftAnimationUseType
RightAnimationUseType
SourcePose
gEAction serialization
gEPhase serialization
animation type N/O/I
direction
opaque 00_%_00 metadata group
DestinationPose
CombatMove distance/length value
final side/hit-direction token when present
```

The exact number of fields and optional tail information can vary with asset type, so treat this as the established combat-animation structure rather than a universal parser specification for every animation file in the game.

## Field notes

### Animation family

The first token identifies the animation/resource family, such as:

```text
Hero
Demon
Goblin
```

`Hero` does **not** mean player-only. Compatible human NPCs also use Hero-family resources.

### Left and right animation UseTypes

The filename order is:

```text
LeftAnimationUseType_RightAnimationUseType
```

These are serialized animation categories. Raw engine `gEUseType` values do not always serialize using the same spelling; see [`../reference/use-types.md`](../reference/use-types.md).

### Source and destination pose

The source/current pose appears before the action field. The destination pose appears later, after the opaque metadata group.

Composite poses such as:

```text
P10
P21
P30
P61
```

are meaningful and should not be simplified into single-digit assumptions.

Raise animations often preserve pose, while Hit animations commonly carry the meaningful transition.

### Action and phase

Filename action and phase fields serialize engine concepts such as `gEAction` and `gEPhase`.

However, filename spelling must not be treated as the only behavior authority. Known asset/runtime mismatches exist. See [`../reference/actions-and-phases.md`](../reference/actions-and-phases.md).

### Animation type

Current established interpretation:

```text
N = normal / non-overlay
O = overlay
I = interaction
```

### Direction

Common direction tokens include:

```text
Fwd
Back
Left
Right
```

and diagonal variants.

### CombatMove distance / length field

The numeric suffix before the optional final side token participates in CombatMove movement/reach behavior. It should not be treated as decorative naming metadata.

### Final L / R token

A final `L` or `R` strongly correlates with logical hit/attack direction.

It does **not** reliably select the physical collision hand/source. Tested Torch+1H and Dual cases demonstrate that runtime physical source can differ from filename-side metadata or from `QuickAttackR` / `QuickAttackL` naming.

## Runtime-over-filename rule

When implementing behavior, prefer exact native runtime state when available:

```text
exact gEAction
exact gEPhase
normalized left/right animation UseTypes
current resolved motion
actor animation family where needed
```

Use filenames primarily for:

- asset authoring;
- exact asset lookup;
- debugging;
- serialized-state identification;
- human-readable categorization.

Avoid fragile substring rules when the engine already exposes the factual runtime value.

## Frame numbering note

Gothic 3 animation authoring uses literal frame indices beginning at frame `0`.

Therefore:

```text
0–12 inclusive = 13 sampled frames
0–4 inclusive  = 5 sampled frames
0–8 inclusive  = 9 sampled frames
```

Do not silently convert authored frame indices into one-based numbering.

## Provenance

Promoted from `tcholti/Gothic3_Animation_Behaviors` at commit:

`9e8ea4034aa9d9ac10e3d6723795ce444f218404`

Primary source:

- `docs/ANIMATION_RULES.md` §§2–8, 12

The source project retains the detailed experimental/evidence history behind edge cases.