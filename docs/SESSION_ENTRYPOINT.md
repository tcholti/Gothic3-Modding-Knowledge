# Gothic 3 Modding Knowledge — Session Entry Point

**Project:** `tcholti/Gothic3-Modding-Knowledge`  
**Purpose:** Minimal durable front door for a fresh Chat/session/context  
**Active branch:** `main`

Read this first. Do not reconstruct or scan the whole repository by default.

---

## Fresh-context bootstrap contract

A fresh context is **not ready merely because this file was opened**.

For normal continuation:

```text
read this entry point
→ recover current objective / durable boundary / next responsibility
→ read PROJECT_MANIFEST only if project purpose/authority needs orientation
→ read KNOWLEDGE_BASE_PLAN when the active work changes or applies knowledge-base architecture
→ read the relevant PROJECT_PIPELINE section before creating/changing taxonomy, filenames, page schema, knowledge-class boundary, status/provenance representation, promotion flow or retrieval conventions
→ use KNOWLEDGE_REGISTRY when ownership/update routing is needed
→ perform one-time domain orientation when entering a populated Gothic 3 domain without sufficiently fresh context
→ retrieve exact topic/source-project provenance only for the current question
→ then continue
```

Do not read every project document by default. Do not invent a new documentation style because the context changed.

### Abrupt / failed previous context — Recovery Lock

If the previous Chat/session stopped unexpectedly, hit a context limit, became unusable or may have ended before completed work was durably maintained, treat this entry point as a clue rather than unquestioned truth.

Use the adopted CAM `COLLABORATION_PROCEDURES.md` Recovery Lock:

```text
DO NOT begin a new migration, tooling task or consequential knowledge decision
DO NOT blindly execute the old NEXT pointer

read this file as a clue
→ recover only the smallest relevant manifest/registry ownership
→ identify the last trusted durable repository state
→ inspect the recent durable tail needed to find what actually changed
→ close missed smallest-owner maintenance
→ correct stale current state
→ verify the real immediate responsibility
→ then continue
```

Do not turn one failed context into a whole-repository audit.

### User fallback instruction

```text
Open tcholti/Gothic3-Modding-Knowledge on main.
Read docs/SESSION_ENTRYPOINT.md and follow its complete fresh-context bootstrap/recovery procedure before claiming readiness.
Use the repository as authority; do not reconstruct or scan the whole project.
```

---

## Current objective / active responsibility

**Stage 2 — expand the knowledge base domain-by-domain from the validated initial slice.**

The first real promotion slice has validated the ordinary Markdown page model and established canonical routes for:

- animation naming/interpretation;
- actions, phases and UseType normalization;
- source/hook research rules;
- tested build-specific RVAs;
- CombatMove/script-continuation behavior.

Continue extracting **established reusable Gothic 3 and Gothic 3 modding-ecosystem knowledge** from source projects, especially `Gothic3_Animation_Behaviors`, without importing their task history, evidence-ledger chronology, temporary probes, project plans or internal machinery that readers do not need.

---

## Latest durable boundary

**Stage 1 initial knowledge promotion is complete and the reader-page convention is frozen.**

Reader-facing knowledge now starts at:

- `knowledge/index.md`
- `knowledge/animation/index.md`
- `knowledge/animation/naming.md`
- `knowledge/reference/actions-and-phases.md`
- `knowledge/reference/use-types.md`
- `knowledge/hooks/index.md`
- `knowledge/reference/tested-rvas.md`
- `knowledge/engine/combat/combat-move.md`

Initial promotion source baseline:

`tcholti/Gothic3_Animation_Behaviors` branch `docs/collision-source-evidence` at:

`9e8ea4034aa9d9ac10e3d6723795ce444f218404`

`PROJECT_PIPELINE.md` owns the accepted ordinary Markdown page convention and now also owns the distinction between:

```text
native Gothic 3 knowledge
framework/mod-specific public contracts
tool/resource knowledge
```

The architecture now explicitly allows future `knowledge/ecosystem/frameworks/` and `knowledge/tools/` surfaces when real content is ready. No empty reader-facing sections have been created merely to reserve them.

Adopted CAM baseline remains:

`tcholti/Collaborative-Agency-Model` branch `current` at `59c63ce300dba1e9fb598d0d1a97cd09ef9bca4e`.

No website implementation is frozen, no native evidence-ID namespace exists, no structured dataset schema has yet been adopted, and no project-local operating-procedure or implementation-protocol library has been created.

---

## Current accepted state relevant to continuation

- The repository is the **library**; mod/research projects are **laboratories**, but an important source project may also expose a reusable framework contract worth documenting as ecosystem knowledge.
- `docs/` owns project infrastructure; `knowledge/` owns reader-facing Gothic 3 and modding-ecosystem subject matter; `data/` is reserved for structured/bulk reference data when needed.
- Reader-facing knowledge must distinguish **native**, **framework/mod-specific**, and **tool/resource** scope rather than excluding useful non-native knowledge.
- Framework pages are reserved for a small number of important reusable framework-type mods; this is not intended to become a catalog of ordinary content mods.
- A future curated tools/resources index is approved in principle for SDKs, editors, import/export utilities and other useful Gothic 3 modding tools; authoritative links and compatibility/status should be preserved when known.
- Current reader layers remain Guides, Reference and Research/provenance, but only categories with real content should be instantiated.
- Ordinary technical Markdown pages use the accepted header/body/provenance pattern in `PROJECT_PIPELINE.md` §§5 and 9.
- Initial finding statuses are Verified, Strong evidence, Observed, Hypothesis, Unknown and Superseded/incorrect.
- Status is always scoped; “Verified” must not be generalized beyond demonstrated boundaries.
- Source-project evidence IDs keep their source identity rather than being automatically renumbered here.
- Promotion copies reusable meaning or a reusable public framework contract, not another project's local task/build/probe machinery.
- Native engine facts and current shared interpretation belong here; unfinished source-project research remains in the source project until its reusable meaning is sufficiently established.
- Framework-specific features such as future `G3AB_COL_*` documentation may belong here when documenting the public `Gothic3_Animation_Behaviors` authoring contract, but must never be presented as native Gothic 3 behavior.
- `main` is the accepted public/project state; working branches/PRs are appropriate for coordinated or experimental promotion batches.
- Searchable static documentation remains intended, but exact site tooling/frontmatter/navigation/deployment conventions remain deliberately unfrozen until website work actually begins.
- `KNOWLEDGE_REGISTRY.md` contains orientation routes for animation, hooks/source work and CombatMove/script-continuation knowledge, plus approved future routes for framework and tools knowledge.

---

## Material unresolved question

The next major representation decision is likely to arise when importing knowledge that behaves more like **structured data** than prose — especially native animation-name inventories, parsed animation fields, symbols/functions or larger enum/reference tables.

Before adopting a first structured dataset, decide from that real case:

- whether the data file or human page is canonical;
- format/schema;
- stable field names;
- provenance fields;
- whether any reader page is generated or independently authored.

Two additional first-use decisions are deliberately deferred until real content exists:

- the exact recurring fields for a framework profile/page;
- the exact recurring fields/schema for the curated tools/resources index.

Each must execute the first-use convention capture rule in `PROJECT_PIPELINE.md` §0 before a second independent instance creates drift.

---

## Immediate next responsibility

Continue knowledge promotion using the validated page model.

Preferred next source-project material, in bounded batches:

1. **animation assets/families and frame effects** — promote stable native asset/mechanism knowledge; if `Gothic3_Animation_Behaviors` public authoring features such as `G3AB_COL_*` are documented, promote them separately and explicitly as framework-specific ecosystem knowledge rather than mixing them into native animation semantics;
2. **script-processing/API mechanisms** — `gCScriptProcessingUnit`, script state/callback concepts and other established engine-facing semantics that are reusable outside the mod;
3. **collision/damage mechanisms only where already closed enough to state cleanly** — preserve distinctions between equipped collision, raw-8 body damage and any still-active research boundary; do not turn unfinished raw55/PhysicalFist research into canonical general claims;
4. **native inventories/reference data** when useful — if a structured dataset is introduced, freeze its first-use schema/ownership convention immediately;
5. **framework/tools surfaces when deliberately selected as a bounded batch** — use the first real framework page or tools index to freeze its specific recurring fields, then expand consistently.

For each batch:

```text
retrieve smallest source authority
→ classify native vs framework/mod-specific vs tool/resource
→ separate established reusable meaning from active research/internal machinery
→ preserve scope/status/provenance or authoritative framework/tool source
→ add/update the smallest public route
→ execute first-use convention capture if a new recurring mechanism/schema appears
→ update this entry point only if the active responsibility changes materially
```

Do not perform a bulk document copy from `Gothic3_Animation_Behaviors` and do not create an unverified link dump for tools/resources.

---

## Retrieve next only if needed

- project purpose / scope / authority topology → `docs/PROJECT_MANIFEST.md`
- knowledge-base architecture / stages → `docs/KNOWLEDGE_BASE_PLAN.md`
- page schema / naming / taxonomy / knowledge-class / status / provenance / promotion / retrieval conventions → `docs/PROJECT_PIPELINE.md`
- authority ownership / update triggers / domain orientation → `docs/KNOWLEDGE_REGISTRY.md`
- project-specific collaboration adaptations → `docs/COLLABORATION_DELTA.md`
- animation orientation → `knowledge/animation/index.md`
- hooks/source orientation → `knowledge/hooks/index.md`
- CombatMove/script continuation → `knowledge/engine/combat/combat-move.md`
- framework/tools direction before first instantiation → `docs/KNOWLEDGE_BASE_PLAN.md` + relevant `PROJECT_PIPELINE.md` sections
- central bootstrap/recovery/review procedure → adopted CAM `COLLABORATION_PROCEDURES.md`
- deeper source-project proof → targeted authority/provenance in `tcholti/Gothic3_Animation_Behaviors`, not a whole-repository reread

---

## Current-state drift check

After any meaningful design decision, source contradiction, blocked route or completed promotion boundary, ask:

> **If a fresh context followed this file literally now, would it begin with the correct immediate responsibility?**

If not, update this entry point even when the larger project stage remains conceptually the same.
