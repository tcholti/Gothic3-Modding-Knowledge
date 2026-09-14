# Tested Gothic 3 RVAs and Call Sites

**Knowledge status:** Verified for the tested source-project binaries  
**Scope:** Build-specific native addresses used during Gothic 3 Animation Behaviors research  
**Critical warning:** Reverify every address before using it with another executable or DLL build.

## Purpose

Provide a compact lookup for high-value functions/call sites that have already been identified and tested during Gothic 3 reverse-engineering work.

An RVA is **not** a universal API contract. Treat the semantic identity as the reusable knowledge and the numeric address as a locator for the tested build.

## Animation / CombatMove

| Purpose | Module + RVA | Established meaning / note |
|---|---:|---|
| `GetAnimationSpeedModifier` | `Script_Game +0x42A0` | Proven speed-modifier hook point; broad compatibility/final intervention architecture is separate. |
| CombatMove animation-string call | `Game +0x16B065` | Narrow animation substitution point used by known mod code. |
| CombatMove reach/vector call | `Game +0x16B8A3` | Useful CombatMove reference call site. |
| CombatMove movement call | `Game +0x16B8A9` | Useful CombatMove movement reference call site. |
| full-Whirl break-block call/test | `Script_Game +0x4DF8C / +0x4DF92` | Incomplete CombatMove can suspend the outer ScriptFunction. |
| full-Whirl ordinary continuation | `Script_Game +0x4E03C` | Resumed path reaches native continuation/cleanup. |
| GetUp pre-Combat offense | `Script_Game +0x41CA6` | Legitimate offensive logic can precede CombatMove. |
| GetUp later CombatMove | `Script_Game +0x41D5A` | Same outer ScriptFunction can later enter CombatMove. |
| GetUp ordinary cleanup | `Script_Game +0x41E10` | Tested cleanup region. |
| `GetAniName` | `Game +0x16F840` | Animation-name lookup. |
| `GetAniEx` | `Script +0x15C10` | Animation query. |
| motion data string | `Game +0xD97D5` | Motion resource string access. |
| cached motion actor | `Game +0xDA344` | Animation actor access. |

## Motion lifecycle

| Purpose | Module + RVA |
|---|---:|
| high `PlayMotion` | `Engine +0x30860` |
| high `StopMotion` | `Engine +0x30980` |
| high `StopAtLoopEnd` | `Engine +0x309D0` |
| wrapper `PlayMotion` | `Engine +0x476F0` |
| wrapper `StopMotion` | `Engine +0x47910` |
| wrapper `StopAtLoopEnd` | `Engine +0x479C0` |

## CombatMove / script state

| Purpose | Module + RVA | Established meaning / constraint |
|---|---:|---|
| `gCScriptRoutine_PS::AIFullStop` | `Game +0x164430` | Invokes the current persisted callback with `fullStop=true`. |
| `AIStopCombatMove` | `Game +0x1644D0` | Full-stops only the current CombatMove callback. |
| `sAICombatMoveInstr` | `Game +0x1696E0` | Persisted asynchronous CombatMove instruction. |
| `sAICombatMoveStart` | `Game +0x16ABB0` | CombatMove start. |
| `sAICombatMoveItlLoop` | `Game +0x16DD00` | Iterative persisted CombatMove loop. |
| `sAICombatMoveStartRecover` | `Game +0x16E360` | Recover start; do not treat as a universal weapon-cleanup authority. |
| `ProcessScript` | `Game +0x16F120` | Generic script dispatcher; not attack ownership by itself. |
| `AISetState` | `Game +0x164320` | Destructive script-state replacement; old continuation can be lost. |

## Script dispatch / continuation

| Purpose | Module + RVA |
|---|---:|
| `RunScriptState` | `Game +0x1603D0` |
| `RunScriptFunction` | `Game +0x1604E0` |
| registered ScriptFunction call | `Game +0x1605E9` |
| first instruction after registered call | `Game +0x1605EB` |
| completed-frame removal helper | `Game +0x1627B0` |
| tested legitimate-reaction `FullStop` | `Script_Game +0x2D0F2` |
| additional reaction `AIFullStop` caller | `Script_Game +0x2B8CB` |
| player Use2 helper | `Script_Game +0x62FF0` |
| common higher caller return | `Script_Game +0x61866` |
| tested held-Use2 `FullStop` | `Script_Game +0x633F1` |
| immediate destructive `SetState` | `Script_Game +0x63409` |

## Native raw-8 body-damage timing path

These addresses were established while classifying the native raw-8 Fist/body-contact mechanism. They are included here because they are useful engine landmarks, not as a recommendation to copy one project's collision implementation.

| Purpose | Module + RVA |
|---|---:|
| `sAICombatMoveItlLoop` | `Game +0x16DD00` |
| SPU `+0x164` permission/latch check | `Game +0x16DFB9` |
| `GetMaxTime(motion 0)` setup/call | `Game +0x16E160..+0x16E164` |
| `GetPlayTime(motion 0)` exact call site | `Game +0x16E180` |
| threshold comparison | `Game +0x16E18C..+0x16E190` |
| native successful-opportunity latch write | `Game +0x16E1A3` |
| observed `gCEntity::OnDamage` caller return | `Game +0x16E348` |
| native threshold multiplier double | `Game +0x308308` |

A separate branch involving `[SPU+0x154] == 0x39` exists and is not covered by the generic path above.

## Reverification checklist

Before reusing one of these addresses in another build:

```text
1. identify exact target module/build
2. locate the same semantic function/call site independently
3. compare surrounding instructions
4. verify calling convention and arguments
5. verify object/this identity
6. verify the caller/context still matches the intended scope
7. only then install or reuse the hook
```

Do not search-and-replace RVAs across game versions.

## Related pages

- [`../hooks/index.md`](../hooks/index.md)
- [`../engine/combat/combat-move.md`](../engine/combat/combat-move.md)

## Provenance

Promoted from `tcholti/Gothic3_Animation_Behaviors` at commit:

`9e8ea4034aa9d9ac10e3d6723795ce444f218404`

Primary source:

- `docs/SOURCE_HOOK_GUIDE.md` §§3–4

The source project remains the detailed proof/provenance owner for how each address was established.