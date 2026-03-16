---
date: 2026-03-16
project: project-memory
topic: implement-ideas-preset-and-idea-triage-flow
source: agent
status: active
---
# Session Note

## Summary

Implemented the `ideas` preset as a draft-decision inbox across core query normalization, CLI/MCP surfaces, repository docs, and automated tests.

## Actions

- Added the `ideas` list-documents preset with default filtering to draft decisions ordered newest first.
- Preserved existing `backlog` semantics and added regression coverage for the legacy backlog behavior.
- Updated CLI/MCP-visible descriptions and repository docs to make the `ideas` inbox discoverable.
- Committed the tool-repo implementation as `06e8cd0 feat: add ideas preset for draft decision inbox`.

## Follow-up

- Consider a separate follow-up only if idea triage needs a richer dedicated UX beyond the list preset.
