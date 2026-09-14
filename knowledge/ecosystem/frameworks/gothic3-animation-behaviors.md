# Gothic3 Animation Behaviors — Animation Author Guide

**Knowledge class:** Framework / mod-specific  
**Knowledge status:** Current documented authoring contract  
**Framework:** `Gothic3_Animation_Behaviors`  
**Scope:** Animation-author-facing behavior established through framework source/evidence at `3d9a659e6ac66b13d287ec91c80a04278a65cb17`

## Purpose

`Gothic3_Animation_Behaviors` is a framework for adding more control to Gothic 3 animations without replacing the game's whole combat system.

This page is for animation authors. It explains the parts you need when making or editing attack animations.

The most important rule is simple:

> **The framework can control when a weapon or body contact is allowed, but it does not turn the attack into a different kind of attack.**

The markers described below are framework features. They are **not native Gothic 3 animation markers**.

---

## Collision markers for equipped weapons

Add collision markers to the **Hit** animation at the frame where you want weapon contact to become active.

| Marker | What it does |
|---|---|
| `G3AB_COL_RIGHT` | Activates the weapon in the Gothic 3 right-hand equipped slot. |
| `G3AB_COL_LEFT` | Activates the weapon in the Gothic 3 left-hand equipped slot. |
| `G3AB_COL_BOTH` | Activates both equipped weapon slots together. |
| `G3AB_COL_OFF` | Turns the authored weapon contact off until another weapon marker appears. |

`RIGHT` and `LEFT` mean the **equipped slots**. They do not mean the final `R` or `L` text in an animation filename.

### Repeated contacts

You may place the same weapon marker again later in the Hit animation when the attack should make another contact.

For example, a multi-hit animation may use:

```text
first contact   -> G3AB_COL_RIGHT
inactive gap    -> G3AB_COL_OFF
second contact  -> G3AB_COL_RIGHT
```

For a dual-wield contact where both weapons should be active together, use:

```text
G3AB_COL_BOTH
```

rather than placing `RIGHT` and `LEFT` on the same frame.

Use at most one collision command on one frame.

---

## Collision marker for Fist attacks

Fist attacks use a separate marker from equipped weapons.

| Marker | What it does |
|---|---|
| `G3AB_COL_FIST` | Allows one native body-contact hit from this authored frame. |

`FIST` works differently from the equipped weapon markers. It does not create a weapon-like contact window, and there is currently no `G3AB_COL_FIST_OFF`.

### Which Fist attacks are supported?

| Attack family | `G3AB_COL_FIST` |
|---|---|
| Normal | Yes |
| Power | Yes |
| Quick | Yes |
| Sprint | Yes |

SprintAttack and PowerAttack use the same shipped animation resource in this case, but they are still different Gothic 3 attack actions.

`PhysicalFist` is a separate Gothic 3 mechanism and is **not yet part of the public FIST authoring contract**.

---

## Which attacks currently accept the equipped markers?

The current public marker contract includes these established attack families:

| Attack family | Equipped markers |
|---|---|
| Normal | Yes |
| Quick | Yes |
| Power | Yes |
| Pierce | Yes |
| SimpleWhirl | Yes |
| Full Whirl | Yes |
| HackAttack | Yes — current tested 2H / Staff scope |
| FinishingAttack | **No** |
| GetUpAttack | **No** — intentionally not supported |

If an attack family is not listed here, do not assume that it is supported. The framework may add more families later.

`GetUpAttack` is intentionally left unsupported. It works differently enough from the ordinary attack families that adding marker support would make the framework more complicated, while there is currently no clear animation-authoring need for it.

### HackAttack and FinishingAttack are different attacks

This can be confusing because Gothic 3 uses the same shipped animation names for two different engine actions.

A true `FinishingAttack` is the execution attack used on an enemy who is already down. It does not use normal weapon-contact timing in the same way as an ordinary attack. The execution/death happens through the game's finishing logic and timing, so the framework does not use the ordinary collision markers for it.

`HackAttack` is different. Gothic 3 has a separate native `HackAttack` action for 2H weapons and Staff. It behaves like an actual combat attack, but the shipped game normally points it to animation resources named `FinishingAttack`.

So these two things can use the same animation file while still being different inside the engine:

```text
HackAttack       = normal combat action, supported by the framework in tested 2H / Staff scope
FinishingAttack  = execution action for a downed enemy, not marker-controlled
```

The fact that Gothic 3 has a separate `HackAttack` action but reuses `FinishingAttack` animation resources strongly suggests that the asset side of this feature was never fully separated before release. That is an interpretation of the shipped game, not a proven statement about the developers' intention.

Do not add the framework markers to a true FinishingAttack and expect it to behave like HackAttack.

---

## Making a separate HackAttack animation

The framework can use separate Hack animations for the current 2H / Staff Hack scope.

A simple way to create them is:

1. Find the matching 2H or Staff `FinishingAttack` animation names.
2. Copy the names for the needed phases.
3. Replace only:

```text
_FinishingAttack_
```

with:

```text
_HackAttack_
```

Do this for the matching:

```text
Raise
Hit
Recover
```

Keep the rest of each filename the same.

For example, conceptually:

```text
..._FinishingAttack_Raise_...
..._FinishingAttack_Hit_...
..._FinishingAttack_Recover_...
```

becomes:

```text
..._HackAttack_Raise_...
..._HackAttack_Hit_...
..._HackAttack_Recover_...
```

You can then author the Hack animation as its own animation.

When Gothic 3 is actually running `HackAttack` and the matching `_HackAttack_` resource exists, the framework can use that resource instead of the ordinary `_FinishingAttack_` one.

The **Hit** animation can use the supported collision markers described above.

A real `FinishingAttack` is left unchanged.

---

## What the markers do not change

The markers are mainly about **when weapon or body contact is allowed**.

They do not automatically change:

- the attack action into another action;
- the damage value;
- the target Gothic 3 considers valid;
- the normal gameplay rules of that attack family;
- the attack range or movement logic;
- the animation speed;
- the Raise animation.

This is important because two attacks can use the same marker but still behave differently in Gothic 3.

A marker does not make Gothic 3 accept a hit that the game's normal rules would reject.

---

## Choosing the marker frame

Frame `0` is allowed. You do not have to begin at frame `1`.

However, the earliest possible frame is not always the best frame.

Place the marker close to the visual moment when the weapon or body should make contact. In many animations it can be useful to place an equipped collision marker about one authored frame before the visible contact, but this is an animation-authoring choice, not a fixed engine rule.

Test the animation in game and adjust the frame if the contact feels early, late, or unreliable.

---

## Future framework options

This framework is intended to grow beyond collision markers.

Future author-facing documentation may include things such as:

- enabling or adding missing Raise animations through configuration;
- changing attack animation speed through configuration;
- additional supported attack families;
- other animation-authoring controls.

When these become stable public features, their exact configuration syntax and supported scope should be added to this page or linked framework pages.

Do not rely on development-only examples until they are documented as part of the public framework contract.

---

## Related native Gothic 3 knowledge

- [`../../animation/naming.md`](../../animation/naming.md) — how Gothic 3 animation filenames are structured.
- [`../../reference/actions-and-phases.md`](../../reference/actions-and-phases.md) — native actions and animation phases.
- [`../../reference/use-types.md`](../../reference/use-types.md) — native UseTypes and their animation-token mapping.

---

## Provenance

Framework repository:

`tcholti/Gothic3_Animation_Behaviors`

Documented source/evidence baseline:

`3d9a659e6ac66b13d287ec91c80a04278a65cb17`

Primary source authorities:

- `docs/ANIMATION_RULES.md` §§8–12;
- `docs/ANIMATION_CATALOG.md` §§3, 5–7, 11–12;
- `docs/DESIGN.md` §4;
- `docs/COLLISION_SPRINT_RAW8_IMPLEMENTATION.md` — Sprint FIST family support.

This page is a simplified author-facing explanation of the framework's public behavior. The framework repository remains the normative source for implementation and exact current release behavior.