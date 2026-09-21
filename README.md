# Gothic 3 Modding Knowledge

A long-term, searchable technical knowledge base for **Gothic 3 modding and engine research**.

The goal is to turn reusable discoveries from Gothic 3 modding projects into documentation that other modders can actually look up: engine mechanisms, SDK/API behavior, hooks, animations, actions, phases, UseTypes, combat/collision behavior, tested addresses, practical guides and other technical knowledge as the project grows.

This repository is deliberately **not** a dump of one mod project's internal documentation or research history. Source projects act as laboratories; this repository is the shared library. Reusable findings are distilled here with their important scope, confidence and provenance preserved.

## Start here

**[Open the Gothic 3 knowledge base](knowledge/index.md)**

Current reader-facing material includes:

- Gothic 3 animation filename structure and interpretation;
- combat `gEAction` / `gEPhase` reference;
- `gEUseType` to animation-token normalization;
- practical hook/source-research rules;
- tested build-specific RVAs and call sites;
- CombatMove execution, script suspension and continuation behavior.

The knowledge base will continue to grow domain-by-domain as established reusable findings are promoted from Gothic 3 modding/research projects.

## Project continuation / recovery

This root README is the **stable discoverable first hop** for project collaboration as well as the public repository front page.

For ordinary continuation:

1. read [Session Entry Point](docs/SESSION_ENTRYPOINT.md);
2. follow only the additional routes it triggers for the current responsibility.

If the previous Chat ended unexpectedly, hit a context limit, became unusable, or may have stopped before maintenance completed:

> Open `tcholti/Gothic3-Modding-Knowledge` on `main`. Read this root `README.md` and follow the **Project continuation / recovery** route before claiming readiness. Use the repository as authority; do not reconstruct or scan the whole project.

In that case, enter the adopted CAM **Recovery Lock**: treat the session entry point as a clue until the recent durable tail and any missed maintenance have been reconciled. This README owns discoverability and routing, not current project state.

## Project architecture

These files sustain the repository itself; ordinary readers do not need them to use the Gothic 3 knowledge pages.

- [Knowledge Base Plan](docs/KNOWLEDGE_BASE_PLAN.md) — intended knowledge-base shape and development direction
- [Project Manifest](docs/PROJECT_MANIFEST.md) — purpose, scope and authority topology
- [Project Pipeline](docs/PROJECT_PIPELINE.md) — stable naming, page, taxonomy, provenance/status and promotion conventions
- [Knowledge Registry](docs/KNOWLEDGE_REGISTRY.md) — knowledge ownership, orientation routes and update triggers
- [Session Entry Point](docs/SESSION_ENTRYPOINT.md) — durable continuation route for future project contexts

Reader-facing Gothic 3 subject matter lives under `knowledge/`. Structured reference datasets may live under `data/` when that representation is more appropriate than prose.

## Guiding principle

> **Build a Gothic 3 library, not another project diary.**

Make current useful knowledge easy to find, keep uncertainty visible, and preserve a route back to the evidence when deeper verification matters.
