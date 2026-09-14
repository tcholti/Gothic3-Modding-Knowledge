# Gothic 3 Modding Knowledge — Knowledge Registry

**Status:** Active authority / update-trigger registry  
**Project:** `tcholti/Gothic3-Modding-Knowledge`  
**Created:** 2026-09-14

## Purpose

Define where important project knowledge belongs, how it is retrieved, and what events should update each authority.

> **One responsibility should have one primary authority when practical. Other sources route to it.**

This registry prevents the project plan, pipeline, indexes, topic pages and source-project provenance from becoming independently maintained copies of the same meaning.

---

## 1. Authority registry

| Knowledge / project responsibility | Primary authority | Supporting route / provenance | Update when | Usually do NOT update when |
|---|---|---|---|---|
| project purpose / long-term direction / scope / authority topology / adopted CAM revision | `docs/PROJECT_MANIFEST.md` | central CAM baseline | purpose, scope, topology or deliberately adopted CAM revision changes | ordinary knowledge addition or source-project discovery |
| knowledge-base architecture / intended reader experience / staged development direction | `docs/KNOWLEDGE_BASE_PLAN.md` | manifest routes to it | knowledge-base model, development stages or intended public shape materially changes | routine use of the existing plan or addition inside an established domain |
| current objective / latest durable boundary / immediate next responsibility | `docs/SESSION_ENTRYPOINT.md` | Git durable state | active responsibility or prerequisite/blocker changes what a fresh context should do next | minor substep that does not change continuation |
| stable repository areas / taxonomy conventions / naming / page structure / status vocabulary / provenance / promotion / correction / retrieval conventions | `docs/PROJECT_PIPELINE.md` | plan + topic authorities | an accepted recurring convention changes, a new stable convention responsibility is established, or the first accepted use of a new recurring mechanism creates a convention that future instances must follow | routine use of an established convention or a new Chat preferring another style |
| detailed authority ownership / update triggers / domain orientation routes | `docs/KNOWLEDGE_REGISTRY.md` | manifest authority map | ownership, update triggers or retrieval/orientation routes materially change, including when first-use convention capture creates a genuinely new owner/responsibility | knowledge grows inside an already-correct owner |
| project-specific collaboration adaptations | `docs/COLLABORATION_DELTA.md` | CAM reusable baseline | recurring project-specific participant/tool/evidence/retrieval collaboration behavior changes | ordinary subject-matter knowledge or general CAM behavior applies unchanged |
| reader-facing top-level navigation | `knowledge/index.md` | domain indexes/topic pages | top-level reader routes materially change | ordinary fact correction inside an already-routed page |
| reader-facing Gothic 3 topic knowledge | owning page under `knowledge/` | source-project provenance / reference data / related topic routes | current bounded Gothic 3 meaning is established, corrected, scoped differently or materially reinterpreted | project-local implementation detail with no reusable Gothic 3 meaning |
| exact structured Gothic 3 reference dataset | owning artifact under `data/` once a domain deliberately adopts structured data | generated reader surface or source inventory | authoritative dataset changes or schema changes deliberately | prose explanation changes without data change |
| reader-facing domain index / navigation route | relevant index under `knowledge/` | owning topic pages/data | retrieval materially improves or category route changes | every new fact already discoverable through current route |
| provenance for knowledge promoted from another Gothic project | originating project / exact source locator unless deliberately copied | shared topic page cites/routes to it | source/provenance locator changes, disappears, or new evidence materially changes the claim | shared wording change that leaves supporting provenance unchanged |
| superseded ordinary wording/history | Git history | explicit supersession note only when useful | automatically preserved by version control | do not create parallel history documents merely to restate old wording |
| static documentation website / generated presentation tooling | future tooling/config authority when created | `knowledge/` + `data/` source material | site tooling/source-of-truth boundary or deployment architecture changes | ordinary knowledge correction that the site merely rebuilds from source |

No project-local operating-procedure authority, implementation protocol, global evidence ledger or native evidence-ID namespace exists at initialization. Add such responsibilities only when actual recurring work demonstrates the need. When the **first accepted instance** creates one of these recurring mechanisms, `PROJECT_PIPELINE.md` §0 requires its repeatable convention to be captured before a second independent instance can drift.

---

## 2. Authority hierarchy

For review or conflict resolution, recover:

```text
CAM / central reusable baseline
        ↓
PROJECT_MANIFEST.md
        ↓
KNOWLEDGE_BASE_PLAN.md / PROJECT_PIPELINE.md / topic authorities
        ↓
indexes / provenance / tooling / current task
```

These specialist authorities are not one total order. Responsibility determines ownership.

Examples:

- the manifest may define that public knowledge must preserve provenance;
- the pipeline defines the recurring provenance/page convention;
- an animation page owns the current Gothic 3 animation fact;
- a source-project EV record may own the detailed proof;
- an index only routes the reader to the animation page.

Do not call this duplication merely because the same concept is visible at several authority layers.

---

## 3. Dependency direction

Normal factual direction:

```text
source project / official source / runtime observation / asset evidence
        ↓
reusable bounded claim
        ↓
owning `knowledge/` topic or `data/` authority
        ↓
index / search route when needed
        ↓
reader / future Chat
```

Normal project-maintenance direction:

```text
meaningful event
→ identify owning responsibility here
→ check update trigger
→ update only triggered owner(s)
→ update retrieval route only if retrieval changed
→ update SESSION_ENTRYPOINT only if continuation changed
```

Do not make a source-project evidence record carry a growing list of every possible future knowledge-base consumer.

---

## 4. Domain orientation routes

Use these routes once when entering a substantial knowledge domain without sufficiently fresh context. Then retrieve only the exact page/provenance needed for the active question.

| Domain / work area | Orientation route |
|---|---|
| project foundation / knowledge-base design | `docs/PROJECT_MANIFEST.md` → `docs/KNOWLEDGE_BASE_PLAN.md` → relevant `docs/PROJECT_PIPELINE.md` section |
| ordinary knowledge promotion | `docs/PROJECT_PIPELINE.md` §§5–12 → relevant domain index/page → exact source-project authority/provenance only as needed |
| animation knowledge | `knowledge/animation/index.md` → `knowledge/animation/naming.md` and/or `knowledge/reference/actions-and-phases.md` / `knowledge/reference/use-types.md` |
| source / API / hooks | `knowledge/hooks/index.md` → `knowledge/reference/tested-rvas.md` → exact source/project reference only when needed |
| CombatMove / script continuation | `knowledge/engine/combat/combat-move.md` → `knowledge/reference/actions-and-phases.md` + `knowledge/reference/tested-rvas.md` as needed |
| collision / damage beyond the currently promoted landmarks | **not yet instantiated as a canonical domain**; retrieve source-project authorities only for a concrete promotion task, then create the smallest public owner if the knowledge is ready |

When a real domain grows, add the smallest route to its index/topic authorities. Do not create another persistent summary merely to perform orientation.

---

## 5. Promotion ownership

A source project owns its own detailed research/evidence unless this repository deliberately adopts a local copy for preservation or independent operation.

This repository owns the **shared current interpretation** after promotion.

Therefore:

```text
source project proves/discovers X
        ↓
this repository decides X is reusable Gothic 3 knowledge
        ↓
knowledge topic page states current scoped X
        ↓
provenance points back to source project evidence
```

If later source evidence contradicts X, correct the shared owner and preserve the changed status/provenance. Do not silently rewrite the original project's historical observation.

---

## 6. Structured data ownership rule

Before adding a structured dataset, decide which representation is canonical:

```text
A. data file is canonical → generated page/index derives from it
or
B. human page is canonical → data file is a retrieval/analysis aid
```

Record that choice in this registry for the domain.

Never maintain two independently editable canonical copies of the same dataset.

The first accepted structured-data implementation also triggers the pipeline first-use capture rule so later datasets do not independently invent incompatible schema/ownership conventions.

---

## 7. Maintenance transaction

After a meaningful project event:

1. What changed semantically?
2. Which responsibility in this registry owns it?
3. Did that owner's update trigger fire?
4. Is the change a source observation, shared interpretation, convention, retrieval route or current-state change?
5. If a reusable source-project discovery is involved, has it passed the promotion test rather than being copied automatically?
6. Is scope/status/provenance sufficient for any changed shared claim?
7. Did retrieval materially change enough to update an index/orientation route?
8. If structured data is involved, is canonical ownership still unambiguous?
9. **Did this event create the first accepted instance of something likely to recur? If yes, execute `PROJECT_PIPELINE.md` §0 and capture the repeatable convention before a second independent instance is created.**
10. If the active responsibility changed, would a fresh context now be routed correctly by `SESSION_ENTRYPOINT.md`?
11. Did a pipeline convention actually change, or was it merely used?

Update only the triggered authorities.

A normal knowledge addition should not require a repository-wide audit.

---

## 8. Interrupted-context recovery

If a Chat/session ends unexpectedly before maintenance may have completed:

```text
SESSION_ENTRYPOINT = clue
→ recover manifest/registry ownership only as needed
→ identify last trusted durable commit/state
→ inspect only the recent durable tail
→ classify committed vs conversation-only work
→ complete missed smallest-owner maintenance
→ repair current-state pointer
→ resume after state is trustworthy
```

Do not reconstruct the entire knowledge repository because one context failed.

If recovery exposes genuine cross-authority contradiction or unclear ownership, perform the central CAM formal review/audit preflight before broad corrective edits.

---

## 9. New-authority rule

When a gap appears, use this order:

```text
can an existing topic authority own it?
→ can existing structured data own it?
→ can an index/cross-link solve retrieval?
→ can the pipeline/manifest/plan absorb the project-level responsibility cleanly?
→ only then create a new authority
```

Create a new document when it represents a genuinely distinct responsibility, not merely because another file has become long or because a new Chat prefers a different organization.

A new authority created by a first recurring use must also be registered here as part of the same first-use capture transaction.

---

## Core rule

> **Keep current Gothic 3 meaning in one primary owner, keep detailed proof at its real provenance source when practical, let indexes route rather than restate, capture the first durable repeatable pattern before repetition can create drift, and update only the authorities whose responsibilities actually changed.**
