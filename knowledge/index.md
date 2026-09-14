# Gothic 3 Modding Knowledge

**Knowledge status:** Initial promoted knowledge slice  
**Scope:** Reusable Gothic 3 modding and engine knowledge

## Purpose

This is the reader-facing entry point to the Gothic 3 modding knowledge base.

The repository is intended to answer questions such as:

- What does this Gothic 3 animation field mean?
- Which native action or phase is running?
- How does a CombatMove persist and resume?
- Where is a useful engine function or hook point?
- Which findings are build-specific?
- What is known, what is only observed, and what remains unresolved?

The goal is to present current reusable knowledge directly, while keeping deeper provenance recoverable without forcing readers to reconstruct the research project that discovered it.

## Current knowledge areas

### Animation

Start with [`animation/index.md`](animation/index.md).

Current promoted material covers:

- native animation filename structure;
- animation families;
- source/destination pose fields;
- action and phase serialization;
- UseType-to-animation-token normalization;
- important cases where filename tokens must not be treated as runtime truth.

### Engine / combat

Start with [`engine/combat/combat-move.md`](engine/combat/combat-move.md).

Current promoted material covers the persisted `CombatMove` path, script suspension/resumption, `AIFullStop`, `AISetState`, and why destructive state replacement can prevent an old suspended continuation from resuming.

### Hooks / source research

Start with [`hooks/index.md`](hooks/index.md).

Current promoted material covers source priority, practical hook-selection rules, exact-call-site scope, calling-convention/object-identity requirements, and compatibility cautions.

### Reference

- [`reference/actions-and-phases.md`](reference/actions-and-phases.md) — project-relevant native action and phase values plus interpretation rules.
- [`reference/use-types.md`](reference/use-types.md) — raw `gEUseType` to serialized animation-token normalization.
- [`reference/tested-rvas.md`](reference/tested-rvas.md) — tested build-specific functions and RVAs.

## Reading status and scope

Technical claims should be read together with their stated scope.

A page marked **Verified** means the stated claim has strong direct support for the scope described on that page; it does not imply that the claim applies to every actor, action, executable build, or mod configuration.

Build-specific addresses must be reverified before use with another executable build.

## Provenance

The initial promoted slice was distilled from established reusable knowledge in:

`tcholti/Gothic3_Animation_Behaviors`

source baseline:

`9e8ea4034aa9d9ac10e3d6723795ce444f218404`

The source project remains the detailed research/provenance owner. This repository owns the reader-facing shared interpretation.