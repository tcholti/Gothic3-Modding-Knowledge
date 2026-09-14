# Gothic 3 CombatMove Execution and Script Continuation

**Knowledge status:** Verified / established mechanism for the tested paths  
**Scope:** Gothic 3 script/CombatMove execution observed during combat research; exact RVAs are build-specific

## Purpose

Explain the native `CombatMove` execution model that matters when modding attacks, animation behavior, interruption and script continuation.

The key idea is that a CombatMove is not simply a synchronous function call that always returns after the animation is finished. Gothic 3 can persist CombatMove execution and suspend the surrounding ScriptFunction until the move progresses or completes.

## Core execution model

Relevant native landmarks include:

```text
sAICombatMoveInstr        -> persisted asynchronous CombatMove instruction
sAICombatMoveStart        -> CombatMove start
sAICombatMoveItlLoop      -> iterative/persisted CombatMove loop
sAICombatMoveStartRecover -> Recover start
```

A tested attack path can behave conceptually like this:

```text
outer attack ScriptFunction
→ enters CombatMove
→ CombatMove is incomplete
→ outer ScriptFunction suspends at its break/continuation boundary
→ Gothic persists the active CombatMove callback/state
→ later processing continues the CombatMove
→ when the path completes normally, the suspended outer ScriptFunction can resume
→ later native attack logic/cleanup can execute
```

This distinction matters whenever a mod assumes that code appearing after a CombatMove call has already executed.

## Persisted callback state

Useful engine/state concepts when inspecting this mechanism include:

```text
gCScriptProcessingUnit
gCScriptRoutine_PS
gScriptRunTimeSingleState
m_StateStack
m_pfInstrCallback
m_pArguments
StateTime
StatePosition
```

The persisted callback/instruction state is part of Gothic's asynchronous script execution. Raw pointer identity by itself should not be assumed to be a durable semantic identity across all lifetime/replacement events.

## `AIFullStop`

`gCScriptRoutine_PS::AIFullStop` invokes the current persisted callback with:

```text
fullStop = true
```

This is significant because the current CombatMove callback can be asked to terminate before the outer ScriptFunction has naturally resumed.

`AIStopCombatMove` is narrower: it full-stops the current CombatMove callback rather than being a universal script-state reset.

## `AISetState` is destructive state replacement

`AISetState` replaces script state. In a tested continuation-loss path, this state replacement can destroy the old suspended continuation rather than allowing it to resume later.

A proven causal class is:

```text
attack ScriptFunction suspended at CombatMove break block
→ FullStop terminates active CombatMove
→ immediate SetState / AISetState replaces script state
→ old continuation is cleared
→ ordinary code after the suspended CombatMove cannot resume
```

This is important for modders because a missing later callback/cleanup may not mean that the later code itself malfunctioned. The continuation that would have reached it may already have been destroyed upstream.

## Example tested held-Use2 path

One tested player path used roughly this sequence:

```text
Script_Game +0x633F1 -> FullStop
Script_Game +0x63409 -> SetState
Game +0x164320       -> AISetState
```

The held-Use2 timing used to reproduce that path was a trigger for the native state transition, not evidence that Use2 itself owned attack collision or cleanup.

That distinction is generally useful:

> **Separate the trigger that exposes a failure from the native mechanism that actually causes it.**

## Recover is not a universal cleanup authority

`sAICombatMoveStartRecover` marks Recover start for CombatMove execution, but established attack research shows that it should not be treated as the universal owner of every weapon/collision cleanup path.

Different attack/action paths can place important offense or cleanup logic outside a simplistic `Start -> Hit -> Recover -> cleanup` assumption.

For example, tested GetUp attack execution can contain offensive logic before a later CombatMove within the same outer ScriptFunction.

## Runtime action identity still matters

CombatMove behavior should be interpreted together with factual native state such as:

```text
exact gEAction
exact gEPhase
StatePosition
current motion
source UseTypes
```

Do not infer the complete execution path only from an animation filename.

## Practical debugging approach

When an attack appears to skip later logic:

```text
1. identify the outer ScriptFunction
2. determine whether it entered an incomplete/persisted CombatMove
3. locate the persisted callback/state
4. observe FullStop / AIFullStop traffic
5. observe AISetState / other destructive state replacement
6. determine whether the original continuation still exists
7. only then debug the later code that appears not to run
```

This can avoid spending time patching a downstream cleanup function when the real cause is upstream continuation loss.

## Tested build landmarks

For relevant RVAs such as:

- `sAICombatMoveInstr`;
- `sAICombatMoveStart`;
- `sAICombatMoveItlLoop`;
- `sAICombatMoveStartRecover`;
- `AIFullStop`;
- `AIStopCombatMove`;
- `AISetState`;
- `RunScriptFunction`;

see [`../../reference/tested-rvas.md`](../../reference/tested-rvas.md).

## Related pages

- [`../../hooks/index.md`](../../hooks/index.md)
- [`../../reference/actions-and-phases.md`](../../reference/actions-and-phases.md)
- [`../../animation/naming.md`](../../animation/naming.md)

## Provenance

Promoted from `tcholti/Gothic3_Animation_Behaviors` at commit:

`9e8ea4034aa9d9ac10e3d6723795ce444f218404`

Primary source authorities:

- `docs/SOURCE_HOOK_GUIDE.md` §§2–3
- `docs/DESIGN.md` established CombatMove/script-lifecycle architecture

The detailed evidence chronology, diagnostic probes and project-specific repair architecture remain in the source project rather than being duplicated here.