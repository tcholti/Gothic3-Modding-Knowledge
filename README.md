# Gothic 3 Modding Knowledge

A long-term, searchable technical knowledge base for **Gothic 3 modding and engine research**.

The goal is to turn reusable discoveries from Gothic 3 modding projects into documentation that other modders can actually look up: engine mechanisms, SDK/API behavior, hooks, animations, actions, phases, UseTypes, combat/collision behavior, tested addresses, practical guides and other technical knowledge as the project grows.

This repository is deliberately **not** a dump of one mod project's internal documentation or research history. Source projects act as laboratories; this repository is the shared library. Reusable findings are distilled here with their important scope, confidence and provenance preserved.

## Current status

The sustained-project foundation has been established. Substantial Gothic 3 knowledge migration has **not** started yet.

The next stage is to validate the knowledge format with a small representative slice of established material — initially animation semantics, actions/phases/UseTypes and source/hook reference knowledge — before building out the larger repository or final documentation website.

## Project architecture

- [Knowledge Base Plan](docs/KNOWLEDGE_BASE_PLAN.md) — intended knowledge-base shape and development direction
- [Project Manifest](docs/PROJECT_MANIFEST.md) — purpose, scope and authority topology
- [Project Pipeline](docs/PROJECT_PIPELINE.md) — stable naming, taxonomy, provenance/status and promotion conventions
- [Knowledge Registry](docs/KNOWLEDGE_REGISTRY.md) — knowledge ownership and update triggers
- [Session Entry Point](docs/SESSION_ENTRYPOINT.md) — durable continuation route for future project contexts

Reader-facing Gothic 3 subject matter will live under `knowledge/` as it is created. Structured reference datasets may live under `data/` when that representation is more appropriate than prose.

## Guiding principle

> **Build a Gothic 3 library, not another project diary.**

Make current useful knowledge easy to find, keep uncertainty visible, and preserve a route back to the evidence when deeper verification matters.
