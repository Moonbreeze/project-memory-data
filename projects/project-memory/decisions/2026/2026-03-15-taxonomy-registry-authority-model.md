---
date: 2026-03-15
project: project-memory
topic: taxonomy-registry-authority-model
source: user
status: active
---
# Decision

## Context

The project needs a deterministic taxonomy authority model so canonical documents do not invent scopes, topics, or authority boundaries implicitly. Previous taxonomy decisions established that topic and scope belong to a control-plane layer, but the model still needed explicit rules for singleton authority, bootstrap circularity, registry-backed canonical truth, aliases, and the lifecycle vocabulary for changing taxonomy over time. Without those rules, agents would have to infer semantic equivalence and scope legitimacy from names and local context, which is too weak for reliable automation.

## Decision

Use one active taxonomy registry per project as the authoritative control-plane surface for registered topics, scopes, aliases, authority ownership, migration status, lifecycle state, and explicit mappings. Store this registry as a reserved canonical document inside the managed document model. Reserve one project-level scope and topic for the taxonomy registry itself, and treat that reserved registry scope as a bootstrap primitive that does not require prior self-registration when bootstrap creates the registry document. Require every non-registry canonical document to be registry-backed. Keep ordinary document topics distinct from registered taxonomy topics: every document keeps exactly one topic, but only canonical documents must use registered taxonomy entries. Allow aliases only for semantically equivalent names that preserve the same semantic unit and authority boundary. Treat taxonomy changes as explicit operations with distinct semantics: alias-add, rename, split, merge, boundary-change, create-topic, and retire-topic. A boundary-change keeps topic lineage while intentionally redefining the authority boundary for the same topic and must not be used when the correct model is a split or merge. A retire-topic removes a registered topic from active taxonomy use and must record whether it is superseded, historical-only, or removed without replacement.

## Consequences

- Every project has one deterministic taxonomy authority surface from bootstrap onward.
- Canonical truth depends on prior taxonomy declaration rather than implicit naming conventions.
- The bootstrap circularity for the registry is resolved explicitly through the reserved registry scope/topic primitive.
- Ordinary project documents can keep lightweight local topics without polluting the registered taxonomy.
- Aliases become an explicit compatibility mechanism rather than fuzzy semantic inference.
- Renames, splits, merges, boundary changes, topic creation, and topic retirement become explicit taxonomy operations with auditable intent.
