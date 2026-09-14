# Gothic 3 Hooks and Source Research

**Knowledge status:** Established practical guide  
**Scope:** Reverse engineering and hook selection for Gothic 3 modding; exact addresses are build-specific

## Purpose

Provide a reusable research order and practical rules for selecting and implementing hooks without confusing a convenient call site with the engine mechanism that actually owns the behavior.

## Recommended research order

For an exact runtime question, use the strongest and cheapest source that can answer it:

```text
exact runtime question
→ official SDK declaration/API
→ smallest known-good hook/example
→ relevant third-party source/reference
→ tested binary reference / static inspection
→ controlled runtime evidence
→ animation/asset evidence when relevant
→ smallest new diagnostic only if causality remains unresolved
```

Useful source classes include:

- the official Gothic 3 SDK for declarations, signatures, enums and wrappers;
- known mod source as implementation/compatibility reference;
- tested binary/disassembly references for native behavior and exact call sites;
- controlled runtime traces for factual execution and causal boundaries;
- animation resources when the question concerns asset serialization or frame effects.

Third-party implementation is useful evidence of what a mod does; it is not automatically evidence of what native Gothic 3 does.

## Hook-selection rules

### Prefer the narrowest factual intervention point

If the required behavior belongs to one exact call site, hook that call site rather than replacing the underlying API globally.

A call-site hook should remain tied to:

- the exact call;
- its argument meaning;
- its caller/context;
- the mechanism it was designed to observe or influence.

Do not convert a proven local hook into a global API override without separate evidence that the broader scope is correct.

### Preserve calling convention and object identity

Hooks must preserve the exact native calling convention and the per-invocation object/`this` identity.

Where nested or recursive traffic is possible, shared implicit-this transport can be unsafe. A proven explicit per-invocation `.ThisCall()` style transport is preferable when it preserves the actual invocation identity.

### One physical hook owner

When several features need facts from the same native function/call site, prefer one low-level owner for the physical hook and delegate translated facts to feature-specific modules.

This prevents multiple project features from independently patching the same native location and reduces compatibility ambiguity.

The low-level hook owner should transport native facts; it should not accumulate unrelated feature policy merely because it owns the hook.

### Reverify RVAs for another build

An RVA is a build-specific locator, not a universal Gothic 3 API contract.

Before using a recorded address with another executable/DLL build:

```text
identify exact target binary
→ verify symbol/function/call-site identity
→ verify surrounding instructions/calling convention
→ only then reuse the address
```

See [`../reference/tested-rvas.md`](../reference/tested-rvas.md).

## Compatibility with other mods

Do not assume that two mods can safely hook the same function merely because both hooks work independently.

For compatibility-sensitive systems:

1. identify whether another mod already owns the same physical path;
2. determine whether hook chaining/order is actually safe;
3. prefer a narrower downstream call site or shared authoritative intervention when evidence supports it;
4. preserve native behavior outside the exact intended scope.

Known mod source such as New Balance/Jackydima can be valuable for compatibility research, but should be treated as third-party implementation evidence rather than native engine authority.

## High-value search terms

### Native animation/state semantics

```text
gEAction
gEPhase
gEAniState
gEPose
gEUseType
gEDirection
gEHitDirection
```

### Script / CombatMove

```text
gCScriptProcessingUnit
gCScriptRoutine_PS
gScriptRunTimeSingleState
RunScriptFunction
sAICombatMoveInstr
sAICombatMoveStart
sAICombatMoveItlLoop
sAICombatMoveStartRecover
m_StateStack
m_pfInstrCallback
m_pArguments
StateTime
StatePosition
AIFullStop
AISetState
```

### Collision / damage

```text
OnAI_Attack
OnAI_QuickAttack
OnAI_PowerAttack
OnAI_PierceAttack
OnAI_SimpleWhirl
OnAI_WhirlAttack
OnAI_HackAttack
SetCollisionGroup
ClearTriggeredList
eCTrigger_PS
gCEntity::OnDamage
gESlot_LeftHand
gESlot_RightHand
```

### Frame effects

```text
UpdateFrameEffects
GetFrameEffectList
eSFrameEffect
StartEffect
```

### Animation speed / timing

```text
GetAnimationSpeedModifier
AniSpeedScale
GetMaxTime
GetPlayTime
PlayMotion
```

## Related pages

- [`../reference/tested-rvas.md`](../reference/tested-rvas.md)
- [`../engine/combat/combat-move.md`](../engine/combat/combat-move.md)
- [`../animation/index.md`](../animation/index.md)

## Provenance

Promoted from `tcholti/Gothic3_Animation_Behaviors` at commit:

`9e8ea4034aa9d9ac10e3d6723795ce444f218404`

Primary source:

- `docs/SOURCE_HOOK_GUIDE.md` §§1–3, 7–8
- `docs/DESIGN.md` governing hook-ownership principles

Project-specific feature architecture and unfinished research plans were intentionally not promoted.