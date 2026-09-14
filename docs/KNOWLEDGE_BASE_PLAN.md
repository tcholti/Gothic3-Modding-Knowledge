# Gothic 3 Modding Knowledge — Knowledge Base Plan

**Status:** Active project-specific knowledge-base architecture and development plan  
**Project:** `tcholti/Gothic3-Modding-Knowledge`  
**Created:** 2026-09-14

## Purpose of this document

This document owns the current project-specific plan for turning accumulated Gothic 3 modding and reverse-engineering knowledge into a durable, searchable, human-usable knowledge base.

It is intentionally different from the documentation of any one mod project. Individual projects may contain deep research history, experiments, implementation details, transient plans, build procedures and evidence needed to solve their own problems. This repository should distill reusable Gothic 3 knowledge from those projects while preserving enough provenance for a reader to understand why a claim is trusted.

It may also document a small number of important reusable **framework mods and modding tools/resources** when those have become part of the practical Gothic 3 modding ecosystem. Framework-specific knowledge must remain clearly distinguished from native Gothic 3 behavior.

The project charter, collaboration configuration and authority topology belong in `PROJECT_MANIFEST.md`. Stable repository conventions belong in `PROJECT_PIPELINE.md`. Detailed ownership and update triggers belong in `KNOWLEDGE_REGISTRY.md`. This plan owns the intended **knowledge-base shape, user experience, content model and staged development direction**.

---

## 1. Core idea — laboratory and library are different responsibilities

The knowledge base is not intended to replace research or mod-development repositories.

A useful relationship is:

```text
mod / research project
        │
        │ experiments, source investigation, runtime observations,
        │ implementation work, logs, project-specific reasoning
        ▼
verified or bounded reusable knowledge
        │
        │ deliberate distillation / promotion
        ▼
Gothic3-Modding-Knowledge
        │
        ▼
searchable public reference for Gothic 3 modding
```

A source project is a **laboratory**. This repository is the **library**.

The library should not require a reader to understand the source project's internal collaboration model, task history, transient probes, branch conventions or implementation workflow merely to answer a Gothic 3 question.

At the same time, reusable claims should not become detached folklore. Where practical, the library preserves a route back to the source, evidence, game build, SDK declaration, binary finding, runtime observation or originating project that supports the claim.

A source project may also be more than a laboratory. If it exposes a stable public framework or authoring contract that other modders intentionally use, the library may document that public surface as **ecosystem/framework knowledge** while keeping it clearly separate from native Gothic 3 semantics.

---

## 2. Intended users and primary question

The repository should be useful to:

- Gothic 3 modders looking up known game behavior;
- programmers working with the Gothic 3 SDK or engine hooks;
- animation authors trying to understand animation names, actions, phases, poses, UseTypes and runtime semantics;
- reverse engineers investigating game mechanisms;
- modders using important framework/extension mods and needing their public authoring/API contracts;
- people trying to find established Gothic 3 modding tools, SDKs, editors, importers/exporters and utilities;
- contributors documenting discoveries from other Gothic 3 projects;
- future Chats/tools that need targeted Gothic 3 knowledge without reconstructing years of project history.

The primary user question is:

> **“I want to know how Gothic 3 modding does X. Where do I look?”**

Depending on the question, the answer may describe native Gothic 3, a reusable framework, or a modding tool. The knowledge class should be obvious to the reader.

The normal answer should be reachable through search, indexes and topic-oriented pages rather than through knowledge of which research project originally discovered the fact.

---

## 3. Long-term knowledge-base shape

The knowledge base should grow around user-facing domains rather than around chronological research campaigns.

Expected major knowledge areas include, when material exists:

```text
getting-started/
engine/
    scripting/
    animation-system/
    combat/
    collision/
    damage/
    entities/
    inventory/
    movement/
    ai/
hooks/
animation/
reference/
guides/
discoveries/
ecosystem/
    frameworks/
tools/
```

This is a direction, not a requirement to create empty directories immediately. Categories should appear when real knowledge exists for them.

Likely early content from existing work includes:

- animation naming and family semantics;
- poses, UseTypes, actions and phases;
- exact animation-name inventories and curated groups;
- CombatMove execution and state behavior;
- frame effects;
- equipped-weapon collision behavior;
- human Fist / PhysicalFist distinctions;
- source/API/symbol/hook lookup;
- tested engine functions and build-specific RVAs;
- callback, damage and collision mechanisms discovered during `Gothic3_Animation_Behaviors` research.

The repository may later grow into areas unrelated to animation or combat, such as quests, NPC routines, navigation, world data, templates, entities, inventory, effects, GUI, audio or save-game behavior.

### Framework / ecosystem pages

A small number of reusable framework-type mods may deserve dedicated pages when other modders need to understand or depend on their public contracts.

Examples of suitable framework knowledge may include:

- supported feature scope;
- authoring markers or reserved conventions;
- configuration/API surface;
- compatibility boundaries;
- how to create assets/content intended to work with the framework;
- links to authoritative releases/source/documentation.

This does **not** mean the repository should catalog ordinary content mods. Inclusion should be based on durable modding utility and ecosystem relevance.

For example, `Gothic3_Animation_Behaviors` may eventually have an ecosystem/framework page documenting its public animation-authoring contract such as `G3AB_COL_*`. Those markers would be presented as framework-specific features, never as native Gothic 3 markers.

### Modding tools/resources index

The repository should eventually provide a curated tools/resources entry point because important Gothic 3 utilities are fragmented and often difficult to discover.

Likely categories include:

- Gothic 3 SDK and source/reference packages;
- general editors such as G3Edit-type tools;
- quest/dialogue editors;
- mesh import/export utilities;
- animation import/export utilities;
- template/entity/world tools;
- archive/file utilities;
- other established community tools and documentation resources.

The index should prioritize **discoverability and authoritative links**, not become an unverified download mirror. When tool pages are created, record what the tool does, authoritative/home/download source, known compatibility/version boundaries where available, and maintenance/status caveats when materially relevant.

---

## 4. Three reader-facing knowledge layers

The public knowledge base should distinguish three complementary forms of documentation.

### Guides — “How do I do or understand this?”

Task- or mechanism-oriented material intended to teach or lead a reader through a problem.

Examples:

- how Gothic 3 CombatMove executes an attack;
- how to find and interpret an animation;
- how animation-authored collision works;
- how to trace a combat action;
- how to approach a safe hook;
- how human Fist damage differs from equipped-weapon damage;
- how to author content for a supported framework when that framework is explicitly in scope.

### Reference — “What is this?”

Concise lookup material for concrete symbols, enums, names, actions, functions, hooks, addresses and concepts.

Examples:

- `gEAction`;
- `gEPhase`;
- `gEUseType`;
- `PhysicalFist`;
- `StatePosition`;
- `gCScriptProcessingUnit`;
- `ClearTriggeredList`;
- tested module + RVA entries;
- framework-specific public tokens when clearly scoped to that framework.

### Research / provenance — “Why do we believe this?”

Deeper evidence and provenance routes for readers who need to inspect the basis, limitations or history of a claim.

This layer may link to:

- source repositories;
- exact commits;
- evidence records;
- SDK declarations;
- binary-reference material;
- test artifacts;
- runtime observations;
- source-project documents.

Most users should be able to remain in Guides and Reference. Research/provenance should remain available without making it mandatory reading.

Tools/resources are primarily a navigation/discovery surface rather than a fourth epistemic layer; individual tool pages may still use the normal status/scope/provenance conventions where useful.

---

## 5. Knowledge is organized by responsibility, not discovery chronology

A public page should normally present the current bounded knowledge first.

Do not make readers reconstruct a conclusion by reading a sequence such as:

```text
probe A
→ probe B
→ failed hypothesis
→ probe C
→ implementation D
→ regression E
→ final conclusion
```

The final reusable knowledge belongs in the relevant topic/reference authority. Important provenance can route to the research history when needed.

Chronology remains valuable for proving or revisiting a conclusion, but it should not be the primary retrieval surface for ordinary modders.

---

## 6. Provenance and epistemic status

One of the repository's defining qualities should be that it distinguishes what is known from what is suspected.

The initial public-facing finding states are:

| Status | Meaning |
|---|---|
| **Verified** | Demonstrated by sufficiently controlled runtime, source, binary or equivalent evidence for the stated scope. |
| **Strong evidence** | Multiple or strong sources support the interpretation, but the mechanism or boundary is not fully demonstrated. |
| **Observed** | A repeatable or recorded observation exists, but the underlying mechanism or generality is not established. |
| **Hypothesis** | A plausible interpretation awaiting stronger evidence. |
| **Unknown** | The question or boundary is explicitly unresolved. |
| **Superseded / incorrect** | A prior claim is retained for provenance but is no longer current knowledge. |

These labels describe epistemic confidence, not importance.

A claim's status must be scoped. “Verified” never means universally true beyond the tested game build, actor type, action family, code path, framework version or other relevant boundary.

Where material depends on a specific executable/build, SDK version, framework/mod version, mod environment or source revision, that dependency should be visible.

The repository does **not** initially adopt a global EV-style evidence-numbering system. Provenance may be represented by source links, source-project evidence IDs, exact commits, citations or page-local evidence sections. A repository-wide identifier system should be introduced only if real usage shows that it materially improves retrieval or maintenance.

---

## 7. Promotion from mod/research projects into shared knowledge

Discoveries should enter this repository deliberately rather than by copying project documentation wholesale.

Normal promotion model:

```text
project question / experiment / public framework contract
→ source or runtime evidence / authoritative framework source
→ project-level interpretation / closure
→ reusable-knowledge check
→ classify native vs framework/mod-specific vs tool/resource
→ distill only the reusable result
→ record scope + status + provenance
→ place it in the correct Gothic 3 topic/ecosystem authority
→ update indexes/search routes only when retrieval changes
```

The reusable-knowledge check asks:

> **Would another Gothic 3 modder benefit from knowing this either because it explains Gothic 3 itself, or because it documents a reusable framework/tool/resource they may intentionally use or depend on?**

If no, keep it in the source project.

If yes, promote the reusable meaning rather than the entire project narrative.

There are therefore two legitimate source-project promotion paths:

```text
source project discovers native Gothic 3 behavior
→ native engine/animation/reference knowledge

source project itself exposes a reusable public framework contract
→ ecosystem/framework knowledge
```

Examples of material that normally should **not** be promoted directly:

- transient task handoffs;
- one-off build/deployment instructions that framework users do not need;
- project-local collaboration procedures;
- diagnostic probe implementation details that add no reusable engine knowledge;
- speculative branches that were disproved and have no continuing reference value;
- project-specific planning history;
- internal implementation detail with no reusable public contract.

Examples that normally are good promotion candidates:

- established engine mechanisms;
- SDK/API semantics;
- tested hooks and constraints;
- animation naming/authoring semantics;
- action/phase/UseType mappings;
- reusable failure modes and negative findings;
- build-specific addresses with clear scope;
- exact asset inventories;
- tested distinctions that prevent common modding mistakes;
- stable public authoring/API contracts of important reusable frameworks;
- curated pointers to important tools/resources with authoritative sources.

---

## 8. Source projects remain first-class provenance

This repository may consume knowledge from many Gothic 3 projects over time.

A promoted claim should preserve enough source identity to answer, when relevant:

- where was this discovered or verified?;
- against which game build or source revision?;
- which project evidence or exact commit supports it?;
- is the claim an SDK declaration, static binary finding, runtime observation, asset observation, framework contract or interpretation?;
- what important boundary or limitation was established?;

The knowledge repository becomes the owner of the **shared current interpretation**, while the originating project remains an important owner of detailed provenance when that provenance lives there.

For framework-specific knowledge, the originating framework/project may remain the normative owner of its own current public contract; this repository owns the curated reader-facing representation and should point to the authoritative framework source/release.

Do not duplicate large raw evidence sets or third-party tool binaries merely to make this repository self-contained unless durable access or preservation genuinely requires it and licensing permits it.

---

## 9. Search and retrieval direction

The source of truth should remain ordinary repository content that works on GitHub and can be version-controlled normally.

The intended user-facing destination is a generated searchable documentation site, likely backed by Markdown and a static documentation generator such as Material for MkDocs or an equivalent tool selected during the website-design stage.

Desired retrieval capabilities include:

- full-text search across documentation;
- direct lookup by exact symbol/name/token/framework feature/tool name;
- topic navigation;
- cross-links between related mechanisms;
- dedicated navigation for native knowledge, ecosystem/frameworks and tools/resources where useful;
- indexes for large exact-name/reference datasets;
- filters or generated tables for structured datasets where useful;
- stable URLs/pages suitable for community linking.

Website tooling is not frozen by this initial plan. The project should first establish the content and information architecture strongly enough that a presentation layer can serve it rather than dictate it.

Future Chats/tools should use repository indexes and topic authorities as targeted retrieval surfaces instead of loading the whole repository.

---

## 10. Structured data where the material is naturally data

Large machine-like inventories should not be forced into hand-maintained prose when structured representation would improve reliability and retrieval.

Potential future structured datasets include:

- animation names and parsed naming components;
- actions;
- phases;
- UseTypes;
- poses;
- engine functions;
- symbols/hooks;
- tested RVAs;
- frame effects;
- collision groups;
- tool/resource records if the curated directory grows enough to benefit from validation/generation.

For example, an animation record may eventually contain fields such as actor family, pose, action, phase, direction and source/provenance, allowing generated tables or filters.

Structured schemas should be introduced only after the relevant domain semantics are understood well enough to avoid freezing a misleading model.

---

## 11. Authority and anti-drift principle

The repository must not solve documentation drift by creating many overlapping summaries.

For each recurring consequential question, one source should own the current answer when practical. Other pages should route to it.

The intended direction is:

```text
source / observation / provenance
        ↓
current bounded shared claim or framework/tool record
        ↓
canonical topic/reference/ecosystem authority
        ↓
index / search route when useful
        ↓
reader / future Chat
```

The project should prefer strengthening an existing authority or route over creating another document that independently restates the same facts.

Plans and indexes should point to knowledge; they should not silently become competing knowledge authorities.

---

## 12. Initial development stages

### Stage 0 — project foundation

Establish the sustained project before migrating substantial knowledge:

- project manifest / charter;
- session entry point;
- collaboration delta;
- knowledge registry;
- project pipeline / stable conventions;
- this knowledge-base plan;
- exact adopted CAM baseline.

Exit condition: a fresh Chat can recover purpose, authority, conventions and next responsibility without rereading the whole repository.

### Stage 1 — design the first real knowledge slice

Use a small but representative subset of existing `Gothic3_Animation_Behaviors` knowledge to validate the content model.

Preferred initial slice:

- animation semantics and naming;
- actions / phases / UseTypes;
- source/hook reference material.

During this stage, decide from real examples:

- page template(s);
- metadata/provenance fields;
- exact status presentation;
- initial taxonomy;
- cross-link conventions;
- what belongs in prose versus structured data;
- what level of source-project evidence should be imported versus linked.

Do not bulk-migrate knowledge before this slice proves the model.

### Stage 2 — searchable site prototype

Once the first content slice is coherent:

- select and configure the static documentation tooling;
- generate navigation/search;
- test exact-name/symbol lookup;
- test framework/tool discovery routes as those categories gain real content;
- test GitHub Pages or equivalent deployment;
- validate that source Markdown remains usable without the website.

### Stage 3 — systematic promotion of established knowledge

Promote additional reusable knowledge from existing projects domain by domain.

Likely early sources include `Gothic3_Animation_Behaviors` and its source/hook, animation, collision and engine research.

Where a source project exposes an important reusable public framework contract, promote that separately under ecosystem/framework knowledge rather than mixing it into native engine pages.

Promotion should remain selective and provenance-preserving rather than a mass file copy.

### Stage 4 — broader community/reference growth

Expand into additional Gothic 3 domains and, when useful, accept contributions from other sources/projects under the same provenance and status model.

Develop the curated modding-tools/resource directory as authoritative links and compatibility knowledge become available. Consider framework pages for other important reusable mods only when they have meaningful ecosystem value.

At this stage the project may justify richer automation, schema validation, generated indexes, contribution templates or additional maintenance procedures. Those mechanisms should be added because demonstrated scale requires them, not because they were imagined during project initialization.

---

## 13. Initial success criteria

The project is moving in the intended direction when:

- a modder can search a Gothic 3 term and reach the current useful answer quickly;
- the reader can tell whether an answer describes native Gothic 3, a particular framework/mod, or an external tool/resource;
- the answer makes its important scope/limitations visible;
- deeper provenance can be recovered without cluttering ordinary reading;
- source projects do not have to surrender their own detailed research history;
- important reusable framework contracts can be documented without being mistaken for native game behavior;
- important modding tools/resources become easier to discover through curated authoritative links;
- new knowledge can be promoted without inventing a new documentation style each time;
- corrections replace or supersede current claims cleanly without erasing provenance;
- future Chats can orient to one domain and retrieve exact details without whole-repository rereads;
- the repository grows as a Gothic 3 technical/modding knowledge base rather than as a diary of whichever mod is currently active.

---

## 14. Important non-goals

This repository is not intended to be:

- a mirror of `Gothic3_Animation_Behaviors` documentation;
- a catalog of every Gothic 3 content mod;
- an unverified link dump of every tool ever mentioned in the community;
- a global dump of raw logs, probes or chat history;
- a replacement for every source project's own evidence and implementation documentation;
- a place where framework-specific behavior is silently presented as native Gothic 3 behavior;
- a place where unverified community claims are silently presented as fact;
- a fixed up-front ontology that forces future discoveries into the wrong categories;
- a CAM documentation repository;
- a mod build or deployment repository;
- a repository whose public readers must understand CAM to use the Gothic 3 knowledge.

CAM governs how the sustained collaboration is maintained; it should remain mostly invisible to readers using the knowledge base itself.

---

## Core principle

> **Build a Gothic 3 modding library, not another project diary: organize reusable knowledge around the questions modders ask, distinguish native game behavior from reusable framework contracts and external tools/resources, preserve the evidence boundary behind the answer, keep one current owner for durable meaning, promote discoveries deliberately from source projects, and let search/indexing expose deep knowledge without forcing readers or future Chats to reconstruct the history that produced it.**
