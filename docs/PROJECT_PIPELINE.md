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

Optional areas such as `research/`, `tools/` or site configuration should be created only when real content/work requires them.

### Separation rule

`docs/` is project infrastructure. `knowledge/` is Gothic 3 subject matter.

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
```

Subdirectories under `engine/` may include scripting, animation-system, combat, collision, damage, entities, inventory, movement, AI and other real domains as content appears.

### Taxonomy rule

Choose the category based on what the reader is trying to retrieve, not on which project discovered the knowledge.

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
- `Verified` must expose important scope limits such as game build, actor family, action path or tested configuration when relevant;
- do not upgrade status merely because a claim is repeated in multiple documents that share the same original source;
- source/API declarations, static findings, runtime observations and interpretations should remain distinguishable when that distinction matters;
- disagreement or uncertainty should be made visible rather than silently averaged into confident prose.

The exact visual/page metadata representation will be finalized using real Stage 1 content rather than frozen abstractly now.

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
→ distill current reusable meaning
→ preserve scope + status + provenance
→ update the owning knowledge/reference page
→ update retrieval routes only if needed
```

The reusable-knowledge check is:

> **Would another Gothic 3 modder benefit from knowing this independently of the source project that discovered it?**

### Promote meaning, not machinery

Do not copy source-project material wholesale when it exists mainly to operate that project.

Normally exclude:

- transient handoffs;
- task contracts;
- build/deployment procedures;
- collaboration protocols;
- probe chronology with no continuing reusable value;
- project-specific state pointers;
- obsolete implementation scaffolding.

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

- what the thing/mechanism is;
- current bounded behavior or rule;
- important limitations/traps;
- status/confidence;
- build/version scope;
- related topics;
- provenance/evidence route.

Do not force every page to contain every field. Exact page templates will be validated against the first real content slice.

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
- frame-effect catalogs.

The authoritative source may be structured data with generated reader pages, or a human page may remain authoritative with structured data as a retrieval aid. Decide this per domain and record the owner in `KNOWLEDGE_REGISTRY.md`.

Do not maintain two independently editable canonical copies of the same dataset.

The first time a structured-data format/schema is accepted for a recurring domain, §0 applies: capture the canonical owner, format/schema convention and generated-vs-human ownership boundary before a second independently designed dataset creates a competing pattern.

---

## 11. Search and retrieval conventions

The normal retrieval path is:

```text
search / domain index
→ owning topic/reference page
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

Exact engine names/symbols/tokens should be written in their canonical spelling so full-text search can find them.

A searchable static documentation website is an intended presentation layer, but website tooling does not become the knowledge authority. Markdown/data in the repository remain the durable source of truth unless a future deliberate architecture decision changes that boundary.

The first accepted website/tooling configuration that establishes reusable build, navigation, metadata or deployment conventions is governed by §0 and must be captured before later site work independently reinvents those conventions.

---

## 12. Standard knowledge-addition flow

For ordinary additions:

```text
identify candidate reusable Gothic 3 knowledge
→ locate or choose one owning page/data authority
→ retrieve provenance needed to state it safely
→ distinguish observation from interpretation
→ state scope + epistemic status where material
→ write/update canonical knowledge
→ add only necessary cross-links/index routes
→ verify a fresh reader can find and understand it
→ if this addition created the first accepted instance of a recurring convention, execute §0 first-use capture
→ maintain current project state only if the active responsibility changed
```

Bulk migration is not the default. The first representative knowledge slice must validate this model before large-scale promotion begins.

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

> **Keep the knowledge flexible but the operating grammar stable: do not pre-design machinery without need, but capture the first durable repeatable pattern before a second instance can drift; separate project infrastructure from public subject matter, organize by reader question, preserve one owner for current meaning, distinguish status and provenance, promote reusable knowledge rather than source-project machinery, and change conventions deliberately instead of allowing each new context to restyle the repository.**
