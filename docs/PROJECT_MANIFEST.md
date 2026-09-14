# Gothic 3 Modding Knowledge — Project Manifest / Charter

**Project:** `tcholti/Gothic3-Modding-Knowledge`  
**Status:** Active project configuration and highest project-specific authority  
**Central collaboration baseline:** `tcholti/Collaborative-Agency-Model` branch `current`  
**Currently adopted CAM revision:** `59c63ce300dba1e9fb598d0d1a97cd09ef9bca4e`  
**Initialized:** 2026-09-14

## Purpose

This repository exists to become a durable, searchable and trustworthy Gothic 3 modding knowledge base.

It should preserve and expose reusable knowledge about Gothic 3 — including engine mechanisms, SDK/API behavior, hooks, animations, actions, assets, runtime semantics, reverse-engineered findings and practical modding guidance — without forcing readers or future project contexts to reconstruct the history of the mod or research project that discovered it.

This file is the highest project-specific authority beneath CAM for project purpose, long-term direction, scope and authority topology. The detailed knowledge-base architecture and staged development direction are owned by `KNOWLEDGE_BASE_PLAN.md`.

CAM is the constitutional collaboration architecture for sustaining the project. It is not part of the public Gothic 3 subject matter and should not be copied into reader-facing knowledge pages.

---

## 1. Project charter / orientation

### Desired outcome

Build a public Gothic 3 technical knowledge resource where a modder can search for a concept, symbol, animation, action, engine mechanism or practical question and reach the current bounded answer quickly, while deeper provenance remains recoverable when needed.

### Long-term direction

The repository should grow into a technical encyclopedia/reference for Gothic 3 modding rather than remain tied to animation work or to one mod.

The expected reader-facing model is:

```text
Guides     → How does this work / how do I do this?
Reference  → What is this exact thing?
Research   → Why do we believe this / where did it come from?
```

The detailed plan, early content domains and staged development path are defined in `KNOWLEDGE_BASE_PLAN.md`.

### Current high-level objective

Establish a coherent sustained-project foundation, then validate the knowledge model using a small representative slice of existing Gothic 3 knowledge before any bulk migration.

### Priorities

1. **Usability:** organize knowledge around questions modders actually ask.
2. **Trustworthiness:** preserve scope, epistemic status and provenance.
3. **Retrievability:** make exact knowledge cheap to find without whole-repository rereads.
4. **Anti-drift ownership:** one primary owner for durable meaning when practical.
5. **Project independence:** shared Gothic 3 knowledge must not depend on understanding one source project's internal workflow.
6. **Incremental growth:** add structure only when real content or recurring work justifies it.

### Scope

The repository may contain reusable Gothic 3 knowledge such as:

- engine and script mechanisms;
- Gothic 3 SDK/API semantics;
- tested symbols, functions, callbacks and hooks;
- build-scoped RVAs and binary-reference findings;
- animation naming, actions, phases, poses, UseTypes and asset families;
- combat, collision, damage and movement behavior;
- entities, AI, inventory, quests, navigation, world data, effects, UI and other domains as knowledge becomes available;
- practical guides derived from established mechanisms;
- structured reference datasets where data representation is more suitable than prose;
- provenance routes to source projects, exact commits, source declarations, runtime observations and other evidence.

### Important non-goals / protected outcomes

The repository is not intended to become:

- a history or mirror of `Gothic3_Animation_Behaviors`;
- a dump of raw logs, diagnostic probes, chat transcripts or transient project plans;
- a replacement for source projects' own implementation/build/test documentation;
- a collection of unscoped claims where observation, inference and verified mechanism are indistinguishable;
- a rigid ontology designed in advance of the knowledge it must represent;
- a CAM documentation mirror;
- a mod build or deployment repository.

Public Gothic 3 documentation should remain understandable without knowledge of CAM.

### Authority hierarchy

```text
CAM / central reusable baseline
        ↓
PROJECT_MANIFEST.md
project charter / scope / authority topology
        ↓
KNOWLEDGE_BASE_PLAN.md
knowledge-base architecture / development direction
        ↓
PROJECT_PIPELINE.md + future topic/domain authorities
stable conventions + current Gothic 3 knowledge owners
        ↓
indexes / provenance / procedures / current task
```

Specialist topic authorities remain primary inside their delegated domains once they exist. The manifest does not duplicate their subject matter.

---

## 2. Repository and state model

**Primary repository:** `tcholti/Gothic3-Modding-Knowledge`  
**Stable/public branch:** `main`  
**Current initial state:** project foundation and knowledge-model design  
**Project entry point:** `docs/SESSION_ENTRYPOINT.md`  
**Pipeline authority:** `docs/PROJECT_PIPELINE.md`

`main` represents the currently accepted public/project state. Working branches and pull requests may be used when a change is large, experimental, contributor-supplied or benefits from review, but the project does not require a permanent development branch before real workflow shows one is useful.

Git history preserves superseded documentation and prior accepted states. Do not create a separate history document merely to duplicate version control.

---

## 3. Fresh-context bootstrap and recovery

A normal fresh Chat/session should read:

1. `docs/SESSION_ENTRYPOINT.md` first;
2. only the additional authorities routed by the current responsibility;
3. the relevant domain orientation route once when entering a substantial knowledge area without sufficiently fresh context;
4. exact deeper sources only when needed.

Reading the entry point alone is not sufficient if it routes additional bootstrap work.

### Abrupt-context restart instruction

```text
Open tcholti/Gothic3-Modding-Knowledge on main.
Read docs/SESSION_ENTRYPOINT.md and follow its complete fresh-context bootstrap/recovery procedure before claiming readiness.
Use the repository as authority; do not reconstruct or scan the whole project.
```

If the previous context ended unexpectedly before maintenance was known to be complete, use the central CAM Recovery Lock procedure through `COLLABORATION_PROCEDURES.md` until/unless this project develops a genuinely necessary local procedure.

---

## 4. Authority map

| Responsibility | Primary authority |
|---|---|
| project purpose / long-term direction / scope / authority topology | `docs/PROJECT_MANIFEST.md` |
| knowledge-base architecture / content model / staged development direction | `docs/KNOWLEDGE_BASE_PLAN.md` |
| current objective / latest durable boundary / immediate next responsibility | `docs/SESSION_ENTRYPOINT.md` |
| stable taxonomy, naming, provenance/status, promotion and retrieval conventions | `docs/PROJECT_PIPELINE.md` |
| detailed knowledge ownership / update triggers / orientation routes | `docs/KNOWLEDGE_REGISTRY.md` |
| project-specific collaboration adaptations | `docs/COLLABORATION_DELTA.md` |
| current Gothic 3 topic knowledge | future topic/reference authorities created only as real content requires them |
| detailed source-project evidence | originating source project unless deliberately promoted/copied for preservation |
| repository history / superseded ordinary wording | Git history |

Do not create a new authority merely because a new topic appears. First determine whether an existing topic authority, reference dataset or index can own it cleanly.

---

## 5. Knowledge model

The project follows the central CAM knowledge-system distinction between:

```text
source / evidence / provenance
        ↓
canonical current interpretation
        ↓
indexes / retrieval routes
        ↓
current-state pointer
        ↓
history / archive when superseded
```

For this repository specifically:

- **provenance** identifies where a claim comes from and what its tested/observed scope is;
- **canonical topic authorities** present current reusable Gothic 3 knowledge;
- **reference datasets** hold naturally structured exact material such as names, enums, symbols or addresses when appropriate;
- **indexes/search** route users and future contexts without duplicating topic narratives;
- **current state** lives only in `SESSION_ENTRYPOINT.md`;
- **history** normally remains in Git and source-project provenance unless a dedicated archive becomes necessary.

The initial epistemic-status vocabulary is defined in `PROJECT_PIPELINE.md` and described conceptually in `KNOWLEDGE_BASE_PLAN.md`.

A repository-wide evidence-ID system is deliberately **not** part of the initial architecture. Existing source-project evidence IDs may be cited as provenance. A native global evidence namespace should be created only if future scale proves it useful.

---

## 6. Knowledge promotion boundary

This repository owns reusable shared knowledge; source projects own their own detailed execution and research history.

Normal promotion direction:

```text
source project discovery
→ project-level evidence/closure
→ reusable-knowledge check
→ distill reusable meaning
→ preserve scope/status/provenance
→ place in shared topic/reference authority
```

The promotion test is:

> **Would another Gothic 3 modder benefit from knowing this independently of the source project that discovered it?**

If not, the material normally remains in the source project.

The detailed promotion conventions are owned by `PROJECT_PIPELINE.md`.

---

## 7. Domain orientation model

No large domain indexes are created during initialization because substantial reader-facing knowledge has not yet been populated.

The first expected orientation routes will likely cover:

- animation semantics/reference;
- engine source/API/hooks;
- combat/collision mechanisms.

`KNOWLEDGE_REGISTRY.md` owns the active orientation-route map as those domains become real.

---

## 8. Participants and responsibility allocation

| Participant / tool | Current responsibility | Boundary |
|---|---|---|
| User | project direction, priorities, acceptance of meaningful scope/architecture choices; first-hand Gothic 3/modding observations | should not have to remember routine CAM maintenance steps |
| Normal Chat | project architect, knowledge curator, reasoning partner, provenance/status interpretation, documentation architecture and maintenance | must preserve project authorities/conventions; must not silently turn uncertain claims into facts |
| Work / implementation agent, when used | bounded mechanical or implementation tasks such as site configuration, transformations or tooling after responsibility is frozen | does not independently redefine project purpose, taxonomy, evidence meaning or canonical Gothic 3 semantics |
| GitHub repository | durable shared project state and public source | repository state does not interpret itself |
| Source projects | detailed originating evidence, implementation and research provenance | do not become shared knowledge merely because material exists there |

This allocation may evolve from evidence. Material recurring changes belong in `COLLABORATION_DELTA.md`.

---

## 9. Project-local procedures

No project-local operating-procedure library is created at initialization.

Reason: the repository does not yet have recurring local operational sequences distinct enough from the central CAM procedures to justify another authority.

Use the central `COLLABORATION_PROCEDURES.md` for startup, bootstrap/recovery, meaningful decisions, knowledge maintenance, review and promotion principles. If repeated project-specific friction later exposes a stable local procedure, create the smallest authority then.

---

## 10. Implementation / production boundary

The repository is primarily a knowledge project, not a software implementation project.

Bounded implementation may still be used for:

- documentation-site configuration;
- generators/indexers;
- structured-data tooling;
- validation scripts;
- mechanical migrations or transformations.

No project-specific implementation protocol is created until repeated implementation work demonstrates a real need.

Semantic knowledge decisions remain with the User + reasoning/curation responsibility, supported by evidence.

---

## 11. Review, stabilization and promotion

A knowledge change is suitable for `main` when its current form is accepted for public/shared use at its stated status and scope. “Stable” does not mean every topic is verified; an explicitly labeled hypothesis or unknown can be valid stable documentation when the uncertainty itself is the current truth.

Broader formal review is appropriate when, for example:

- the taxonomy/knowledge schema materially changes;
- several authorities appear to overlap or contradict;
- a large migration is proposed;
- website/tooling changes would redefine source-of-truth responsibilities;
- recurring maintenance failure shows that the ownership model is no longer working.

Before such a review, recover the CAM → manifest → specialist-owner hierarchy and intended role of each target. Ordinary knowledge additions should use local incremental maintenance, not repository-wide audits.

---

## 12. CAM ↔ project evolution boundary

A newer `Collaborative-Agency-Model/current` revision does not silently modify this project.

Adoption requires:

```text
new CAM revision
→ compare with currently adopted revision
→ determine project relevance
→ deliberately operationalize applicable changes
→ update this manifest's adopted revision
```

Likewise, lessons from this project may inform CAM, but ordinary Gothic 3 project work does not directly rewrite CAM. Generalization belongs to a separate deliberate CAM responsibility.

---

## Core rule

> **This repository is the shared Gothic 3 library: keep the public knowledge independent of any one mod project, preserve provenance and uncertainty, organize current meaning under clear owners, keep retrieval cheap, and add collaboration/documentation machinery only when demonstrated project needs justify it.**
