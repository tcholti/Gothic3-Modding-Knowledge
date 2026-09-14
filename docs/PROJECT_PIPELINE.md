# Gothic 3 Modding Knowledge — Project Pipeline

**Status:** Active operating-convention authority  
**Project:** `tcholti/Gothic3-Modding-Knowledge`  
**Created:** 2026-09-14

## Purpose

Preserve the recurring conventions that should remain stable while the knowledge base grows across Chats, contributors, source projects and future tooling.

This is not a linear project plan. `KNOWLEDGE_BASE_PLAN.md` owns the current staged development direction. This file owns the stable grammar around that adaptive work: repository areas, naming, knowledge status, provenance, promotion, correction and retrieval conventions.

A convention changes because there is a reason, not because a new context prefers another style.

---

## 0. First-use convention capture rule

The project should not design every future mechanism in advance. However, **the first real accepted use of a new recurring mechanism must not remain an undocumented one-off that later examples reinvent differently**.

When work creates the first instance of something that is likely to recur — for example the first native evidence identifier, first website/deployment configuration, first page-metadata schema, first structured dataset schema, first generated reference surface, first project-local procedure, or first new artifact naming pattern — use this sequence:

```text
real need appears
→ create/design the smallest fit for the first real case
→ identify which parts are one-off and which parts establish a repeatable convention
→ in the same maintenance transaction, record the repeatable convention in PROJECT_PIPELINE
   or create another authority only if the responsibility is genuinely distinct
→ update KNOWLEDGE_REGISTRY if a new owner/responsibility was created
→ before creating a second independent instance, retrieve and follow the recorded convention
```

### Second-instance gate

The first accepted instance may establish the convention. The **second independent instance must not invent a parallel pattern from memory or preference**.

Before a second instance is created:

- use the recorded convention; or
- if the first pattern proved inadequate, deliberately revise the convention with the reason, effective boundary and treatment of the first artifact.

### Provisional first use

Sometimes one example is not enough to freeze a good permanent rule. In that case:

- mark the first-use convention as **provisional** in this pipeline or its owning authority;
- state what remains unresolved;
- do not let the provisional pattern silently become permanent through repetition;
- resolve, revise or deliberately retain it before the second accepted/production use where practical.

An intentionally throwaway experiment does not need to establish a project convention merely because it exists. The trigger is the first use that is accepted as part of the durable project or that future work is reasonably expected to repeat.

> **Delay machinery until reality justifies it; once reality creates a repeatable pattern, capture that pattern before repetition creates drift.**

---

## 1. Repository areas

Use these top-level responsibilities unless a demonstrated future need justifies change:

```text
docs/
    project-local charter, collaboration, pipeline and maintenance authorities

knowledge/
    reader-facing Gothic 3 guides, reference and topic documentation

data/
    structured or bulk reference data when prose is the wrong representation
```

Optional areas such as `research/`, repository-side `tools/`, or site configuration should be created only when real content/work requires them.

### Separation rule

`docs/` is project infrastructure. `knowledge/` is Gothic 3 subject matter and modding-ecosystem knowledge intended for readers.

Public readers should not need CAM or project-governance documents to understand the Gothic 3 knowledge base. A future static documentation site should normally publish from `knowledge/` (plus generated/reference data surfaces as appropriate), not expose the project-management layer as reader documentation.

Do not create empty topic directories merely to make the repository look complete.

---

## 2. Knowledge taxonomy

The initial reader-facing taxonomy is domain-oriented and may grow incrementally.

Expected categories include:

```text
knowledge/getting-started/
knowledge/engine/
knowledge/hooks/
knowledge/animation/
knowledge/reference/
knowledge/guides/
knowledge/discoveries/
knowledge/ecosystem/
    frameworks/
knowledge/tools/
```

Subdirectories under `engine/` may include scripting, animation-system, combat, collision, damage, entities, inventory, movement, AI and other real domains as content appears.

`knowledge/ecosystem/frameworks/` is reserved for a **small number of important reusable framework-type mods or extension systems** whose public behavior/contracts are useful knowledge for other modders. It is not intended to become a catalog of ordinary content mods.

`knowledge/tools/` is reserved for curated modding tools/resources such as SDKs, editors, import/export utilities, asset tools and other practical utilities that are otherwise difficult to discover reliably.

### Knowledge-class boundary

Reader-facing material may describe three different classes of knowledge:

```text
NATIVE
Gothic 3 engine/game/asset behavior itself

FRAMEWORK / MOD-SPECIFIC
behavior, authoring contracts or APIs provided by a particular reusable mod/framework

TOOL / RESOURCE
external utilities, SDKs, editors, converters, importers/exporters or community resources
```

These classes may cross-link, but **must not be silently conflated**.

A framework-specific page must make the owning framework/mod and relevant version/revision scope obvious. For example, `G3AB_COL_RIGHT` may eventually be documented as part of the public authoring contract of `Gothic3_Animation_Behaviors`; it must never be presented as a native Gothic 3 animation marker.

A tools/resource page should distinguish what a tool is for, where its authoritative/download source is, and any important compatibility/maintenance limitation known at the time of documentation.

When the first actual framework profile or tools index is created, §0 applies: use the real case to freeze the exact recurring page fields before producing further entries.

### Taxonomy rule

Choose the category based on what the reader is trying to retrieve, not only on which project discovered the knowledge.

Do not duplicate one fact into several categories merely to improve discoverability. Prefer cross-links, indexes, aliases/search metadata or generated routes to one owning page.

If a topic naturally belongs to several domains, choose one primary owner and route to it from the others.

---

## 3. File and directory naming

### Project authorities

Under `docs/`, use descriptive uppercase underscore names for stable project authorities, for example:

```text
PROJECT_MANIFEST.md
SESSION_ENTRYPOINT.md
PROJECT_PIPELINE.md
KNOWLEDGE_REGISTRY.md
```

### Reader-facing knowledge

Under `knowledge/`:

- directories: lowercase, hyphen-separated when multiple words are needed;
- Markdown files: lowercase, hyphen-separated descriptive names;
- prefer stable semantic names over dates or sequence numbers.

Examples:

```text
knowledge/animation/use-types.md
knowledge/engine/combat/combat-move.md
knowledge/reference/actions.md
knowledge/guides/tracing-a-combat-action.md
knowledge/ecosystem/frameworks/gothic3-animation-behaviors.md
knowledge/tools/index.md
```

Do not encode confidence status or revision numbers into ordinary page filenames. Current status belongs in page metadata/content; Git owns revision history.

### Structured data

Under `data/`, use lowercase descriptive names. Choose CSV, YAML, JSON or plain text according to the data and tooling needs. Do not freeze a schema before the relevant domain semantics are understood.

---

## 4. Branch and state model

**Stable/public state:** `main`

`main` contains the currently accepted project and public knowledge state at each claim's stated status/scope.

Working branches / pull requests are appropriate when:

- a change is substantial or experimental;
- a contributor is proposing knowledge;
- a migration/tooling change benefits from review;
- several coordinated files must change before they form a coherent accepted state.

A permanent development branch is not required initially.

Do not treat a hypothesis as unsuitable for `main` merely because it is uncertain. Explicitly documented uncertainty can itself be stable current knowledge.

---

## 5. Epistemic status vocabulary

Use the following initial statuses for factual Gothic 3 findings when a status is useful:

| Status | Meaning |
|---|---|
| **Verified** | Demonstrated by sufficiently controlled runtime, source, binary, asset or equivalent evidence for the stated scope. |
| **Strong evidence** | Strong/multiple evidence supports the interpretation, but the mechanism or boundary is not fully demonstrated. |
| **Observed** | A repeatable or recorded observation exists; mechanism/generalization remains unresolved. |
| **Hypothesis** | Plausible interpretation awaiting stronger evidence. |
| **Unknown** | The question/boundary is explicitly unresolved. |
| **Superseded / incorrect** | Prior claim retained or referenced for provenance but no longer current knowledge. |

### Status rules

- status applies to the exact scoped claim, not to an entire broad subject by implication;
- `Verified` must expose important scope limits such as game build, actor family, action path, framework version or tested configuration when relevant;
- do not upgrade status merely because a claim is repeated in multiple documents that share the same original source;
- source/API declarations, static findings, runtime observations and interpretations should remain distinguishable when that distinction matters;
- disagreement or uncertainty should be made visible rather than silently averaged into confident prose.

### First accepted reader-page metadata convention

The initial promoted knowledge slice established a plain-Markdown metadata convention. Until a future website/tooling decision deliberately replaces it, reader-facing technical pages should begin with:

```text
# Page title

**Knowledge status:** <status or bounded status description>
**Scope:** <the boundary readers must know>
```

For framework/mod-specific knowledge, `Scope` must name the framework/mod and relevant version/revision boundary when material.

Add a compact `**Critical warning:** ...` line only when missing the warning could make direct reuse unsafe, such as build-specific RVA pages.

Do **not** introduce YAML/frontmatter solely for cosmetic consistency before site tooling actually requires it. If future site tooling adopts frontmatter, treat that as a pipeline convention change with an explicit migration boundary.

### First accepted framework-page convention

The first framework page, `knowledge/ecosystem/frameworks/gothic3-animation-behaviors.md`, establishes the recurring framework-page header:

```text
# Framework / feature title

**Knowledge class:** Framework / mod-specific
**Knowledge status:** <current status>
**Framework:** <canonical framework/mod name>
**Scope:** <release/revision and user-facing boundary>
```

Framework pages should then:

- explain the feature from the user's point of view before implementation detail;
- state clearly what the framework adds and what remains native Gothic 3 behavior;
- show supported and unsupported boundaries when users could otherwise make unsafe assumptions;
- use exact public feature/config/marker names so they are searchable;
- explain user-facing behavior in enough detail that a modder can use the feature correctly, including technical behavior when it matters to authoring or use;
- treat **plain English as lower assumed background knowledge, not as shorter documentation**: a technical term that carries a lot of meaning for an engineer or experienced native speaker may need to be unpacked into a longer step-by-step explanation for a non-specialist or non-native reader;
- when useful, explain what a technical action means in practical terms instead of only naming the operation—for example, explain the effect on the data or authoring workflow rather than assuming the reader understands a programming term;
- prefer practical examples and user-facing mechanics over backend implementation details such as hooks, internal state machines, probe architecture or diagnostic plumbing;
- include backend details only when they materially explain a user-facing rule, limitation, compatibility issue or troubleshooting step;
- use clear, plain English because a large part of the Gothic 3 community does not use English as a first language;
- avoid unnecessary jargon, but do not remove useful explanation merely because the behavior itself is technical;
- mark future/planned features as future rather than presenting development ideas as current public behavior;
- end with authoritative framework provenance/revision.

This framework-page convention is **accepted**, not provisional. More specialized framework subpages may add fields later if a real need appears, but they should preserve this class/framework/scope boundary.

---

## 6. Provenance convention

Reusable knowledge should preserve enough provenance to recover its basis when the claim is non-trivial or boundary-sensitive.

Prefer the strongest practical locator, such as:

- exact source-project repository + commit + path/section;
- exact external evidence ID where the source project already has one;
- official SDK file/symbol/declaration;
- tested binary-reference source/build;
- runtime/test artifact identity;
- exact asset/file identity;
- framework/mod repository + release/commit + public documentation/source contract;
- authoritative tool homepage/repository/release/source;
- public external source/citation.

### Source-project identity

Do not renumber another project's evidence into a new local sequence merely for cosmetic consistency.

For example, if `Gothic3_Animation_Behaviors` owns `EV-240`, this repository may cite it using the source-project identity, e.g. conceptually:

```text
Gothic3_Animation_Behaviors — EV-240
```

plus repository/commit/path when useful.

The knowledge base owns the shared interpretation; the source project may continue to own the detailed evidence transaction.

### No global evidence sequence at initialization

This project has **no native repository-wide EV numbering scheme** at startup.

Introduce one only if real usage demonstrates that local source links/page evidence sections are insufficient for reliable retrieval or maintenance.

If the first native evidence identifier is ever introduced, §0 applies: the identifier form, ownership, sequence/scope and reuse rules must be captured before a second native evidence item is assigned.

---

## 7. Promotion from source projects

New shared knowledge normally enters through:

```text
source project discovery / evidence
→ source-project interpretation or closure
→ reusable-knowledge check
→ classify native vs framework/mod-specific vs tool/resource knowledge
→ distill current reusable meaning
→ preserve scope + status + provenance
→ update the owning knowledge/reference/ecosystem page
→ update retrieval routes only if needed
```

The reusable-knowledge check is:

> **Would another Gothic 3 modder benefit from knowing this either because it explains Gothic 3 itself, or because it documents a reusable framework/tool/resource they may intentionally use or depend on?**

This replaces the narrower assumption that promoted knowledge must always be useful independently of the source project. A source project can itself become part of the reusable modding ecosystem when it exposes a stable public framework, authoring contract or compatibility surface.

### Native knowledge vs framework knowledge

For source projects that are also reusable frameworks, separate two legitimate promotion paths:

```text
research discovered native Gothic 3 behavior
→ promote under native engine/animation/reference knowledge

framework exposes a reusable public contract
→ promote under ecosystem/framework knowledge
```

Do not mix the two merely because they were discovered or implemented in the same repository.

### Promote meaning, not internal machinery

Do not copy source-project material wholesale when it exists mainly to operate that project.

Normally exclude:

- transient handoffs;
- task contracts;
- local build/deployment procedures that framework users do not need;
- collaboration protocols;
- probe chronology with no continuing reusable value;
- project-specific state pointers;
- obsolete implementation scaffolding;
- internal implementation detail that does not form part of a reusable framework contract or reusable Gothic 3 mechanism.

Preserve relevant negative results and failed interpretations when they prevent likely future mistakes or materially define the boundary of current knowledge.

---

## 8. Correction and supersession

When current knowledge changes:

```text
identify owning page/data record
→ update the current bounded claim
→ preserve new status/scope/provenance
→ update affected cross-routes
→ preserve old wording through Git history by default
```

Add an explicit superseded/incorrect note when readers are likely to encounter the old claim elsewhere, when compatibility/history matters, or when the correction itself is important knowledge.

Do not keep two active contradictory pages merely to preserve history.

Do not rewrite source-project evidence to make old observations look as if they were recorded with later understanding.

---

## 9. Reader-facing page responsibility

A knowledge page should normally answer the useful current question first and keep provenance behind it.

When appropriate, pages should make visible:

- what the thing/mechanism/tool/framework is;
- current bounded behavior or rule;
- important limitations/traps;
- native vs framework/tool scope when relevant;
- status/confidence;
- build/version/framework scope;
- related topics;
- provenance/evidence route or authoritative tool/framework source.

### First accepted page structure

The first promoted animation/reference/hook/combat pages established this default structure:

```text
title
→ compact Knowledge status + Scope header
→ Purpose
→ answer-first body organized around reader questions/mechanism
→ Important limitation / warning where needed
→ Related pages when useful
→ Provenance at the end
```

For non-trivial promoted technical knowledge, `Provenance` should normally identify:

```text
source project
+ exact source baseline commit/revision
+ smallest practical source authority path/section
```

An external evidence ID or deeper raw artifact is optional when the source authority already routes reliably to it. Do not make ordinary reader pages reproduce the evidence ledger.

Reference-table pages may be primarily tables; explanatory mechanism pages may be primarily prose/flows. They still use the same status/scope/provenance boundary.

A page may omit `Related pages` when no useful cross-route exists. A trivial/non-technical landing page may use a lighter header. Do not force empty sections merely to satisfy a template.

This convention is now **accepted**, not provisional, for ordinary Markdown knowledge pages. Website-specific metadata/frontmatter remains separately unfrozen.

Framework pages use the additional accepted convention in §5. Tool-directory entries remain unfrozen until the first real tools index is created.

### Guide vs reference vs provenance

Use the smallest fitting role:

```text
guide      = how / mechanism explanation / task path
reference  = exact lookup / definition / table / symbol / value
provenance = why we believe it / evidence route
```

A guide may link to reference entries; a reference entry may link to deeper research. Avoid maintaining the same full explanation in each layer.

---

## 10. Structured-data convention

Use structured data when the material behaves like a dataset and benefits from filtering, generation or validation.

Potential examples include:

- animation-name inventories;
- parsed animation components;
- actions/phases/UseTypes/poses;
- symbols/functions/hooks/RVAs;
- frame-effect catalogs;
- curated tool/resource records when the directory grows large enough to benefit from generation/validation.

The authoritative source may be structured data with generated reader pages, or a human page may remain authoritative with structured data as a retrieval aid. Decide this per domain and record the owner in `KNOWLEDGE_REGISTRY.md`.

Do not maintain two independently editable canonical copies of the same dataset.

The first time a structured-data format/schema is accepted for a recurring domain, §0 applies: capture the canonical owner, format/schema convention and generated-vs-human ownership boundary before a second independently designed dataset creates a competing pattern.

---

## 11. Search and retrieval conventions

The normal retrieval path is:

```text
search / domain index
→ owning topic/reference/framework/tool page
→ exact provenance only when needed
```

Future Chats should similarly use:

```text
SESSION_ENTRYPOINT
→ one-time domain orientation route when needed
→ exact topic authority
→ provenance/source detail only for the active question
```

Searchability should be improved through meaningful titles, exact technical terms, cross-links and structured indexes rather than by copying the same explanation into many pages.

Exact engine names/symbols/tokens, framework feature names and tool names should be written in their canonical spelling so full-text search can find them.

A searchable static documentation website is an intended presentation layer, but website tooling does not become the knowledge authority. Markdown/data in the repository remain the durable source of truth unless a future deliberate architecture decision changes that boundary.

The first accepted website/tooling configuration that establishes reusable build, navigation, metadata or deployment conventions is governed by §0 and must be captured before later site work independently reinvents those conventions.

---

## 12. Standard knowledge-addition flow

For ordinary additions:

```text
identify candidate reusable Gothic 3 or modding-ecosystem knowledge
→ classify native vs framework/mod-specific vs tool/resource
→ locate or choose one owning page/data authority
→ retrieve provenance needed to state it safely
→ distinguish observation from interpretation
→ state scope + epistemic status where material
→ write/update canonical knowledge
→ add only necessary cross-links/index routes
→ verify a fresh reader can find and understand it without confusing its knowledge class
→ if this addition created the first accepted instance of a recurring convention, execute §0 first-use capture
→ maintain current project state only if the active responsibility changed
```

Bulk migration is not the default. The first representative knowledge slice has now validated the ordinary Markdown page model; broader promotion should still proceed domain-by-domain rather than by copying source documentation wholesale.

---

## 13. Pipeline change control

A material convention change should record, proportionately:

- old convention;
- new convention;
- reason;
- effective boundary;
- treatment of existing artifacts/pages;
- affected authorities/routes.

Do not retroactively rename historical provenance merely for visual uniformity.

When the change affects taxonomy, source-of-truth responsibility, provenance semantics or reader-facing status meaning, treat it as a consequential project architecture decision and update the relevant manifest/plan/registry authorities as triggered.

---

## Core rule

> **Keep the knowledge flexible but the operating grammar stable: do not pre-design machinery without need, but capture the first durable repeatable pattern before a second instance can drift; distinguish native Gothic 3 knowledge from framework/mod-specific contracts and tools/resources without excluding any of them when they are genuinely useful; preserve one owner for current meaning; preserve scope and provenance; and change conventions deliberately instead of allowing each new context to restyle the repository.**
