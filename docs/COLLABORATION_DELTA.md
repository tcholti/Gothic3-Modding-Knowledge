# Gothic 3 Modding Knowledge — Collaboration Delta

**Status:** Active project-specific collaboration authority  
**Project:** `tcholti/Gothic3-Modding-Knowledge`  
**Central baseline identity:** see `PROJECT_MANIFEST.md`

## Purpose

Record only collaboration adaptations that are specific to maintaining a shared Gothic 3 knowledge base.

General collaboration behavior, bootstrap/recovery, maintenance, review and promotion procedures remain owned by the adopted CAM baseline. Do not copy them here.

---

## 1. Project-specific responsibility allocation

```text
User
project direction + Gothic 3/modding judgment + acceptance of meaningful choices
        ↓
User + Normal Chat
knowledge interpretation + architecture + curation + provenance/status judgment
        ↓
Work / implementation tooling when useful
bounded mechanical implementation, generation, site/tool configuration
        ↓
repository + source projects + external evidence
persistent shared state and provenance
```

Normal Chat is expected to maintain project documentation/routing after meaningful work without requiring the User to separately request routine housekeeping.

The User should not have to remember detailed CAM procedures during ordinary Gothic 3 knowledge work.

---

## 2. Project-specific knowledge / evidence rules

- A source project's confident statement is not automatically a shared Gothic 3 fact. Preserve the source's evidence/status boundary when promoting knowledge.
- Distinguish observation, source declaration, static/binary finding, runtime result and interpretation whenever collapsing them would make a claim misleading.
- “Verified” applies only within the stated demonstrated scope; do not generalize from one actor/action/build/path by convenience.
- Negative findings and disproved interpretations are worth promoting when they prevent a likely future modding mistake or define an important boundary.
- Do not import another project's internal task/probe chronology unless that chronology itself has durable explanatory or provenance value.

---

## 3. Project-specific retrieval / documentation rules

- Reader-facing Gothic 3 knowledge belongs under `knowledge/`; CAM/project infrastructure belongs under `docs/`.
- Public topic pages should answer the useful current question before exposing deep research history.
- Search/retrieval should favor canonical technical spelling for symbols, actions, enums, animation names and engine terms.
- When knowledge comes from another repository, prefer exact repository/commit/path/evidence identity where practical over vague “from project X” attribution.
- A future Chat should orient to the active domain once, then retrieve exact pages/provenance as needed rather than rereading the whole repository.

---

## 4. Project-specific delegation rules

Bounded implementation/tooling may be delegated for tasks such as:

- static documentation-site setup;
- index/data generation;
- validation scripts;
- mechanical transformations/migrations;
- repetitive formatting after the semantic model is frozen.

Before such delegation, freeze the relevant source-of-truth boundary, taxonomy/schema/convention and protected semantics.

The executor may make local mechanical choices inside that contract but must return rather than independently redefine:

- project purpose/scope;
- knowledge taxonomy;
- epistemic status meaning;
- provenance requirements;
- canonical Gothic 3 interpretation;
- which representation owns a dataset.

A separate implementation protocol should be created only if repeated delegated work proves one necessary.

---

## 5. Project-specific continuity rule

Because this repository may aggregate knowledge from many long-running source projects, a new Chat must not assume that the newest-looking source file is the shared authority.

Use:

```text
PROJECT_MANIFEST / KNOWLEDGE_REGISTRY
→ owning shared topic/reference authority
→ source-project provenance when exact proof is needed
```

Source projects remain provenance; this repository becomes the owner of the promoted shared interpretation.

---

## 6. Current adaptations from generic CAM defaults

No material deviation from CAM is currently required.

The main project-specific specialization is the deliberate separation between:

```text
project infrastructure (`docs/`)
vs
public Gothic 3 knowledge (`knowledge/`)
vs
source-project evidence/provenance (often external)
```

This specialization exists to keep the public knowledge base usable without exposing readers to collaboration machinery while still preserving rigorous project continuity behind it.

---

## Core rule

> **Curate before copying: preserve uncertainty and provenance, keep public Gothic 3 knowledge easy to use, and delegate mechanics only after the semantic responsibility is clear.**
