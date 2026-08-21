# Product contract

## Outcome

A human or authorized agent can create an on-brand asset from an approved template, safely change semantic fields, preview it, and export it without Canva.

## Canonical model

`ArkovaDesign` owns schema version, pages, allow-listed primitives, brand-token references, semantic template roles, constraints, asset IDs, locks, and revision. Fabric JSON is an implementation detail, not a public storage or API contract.

## Acceptance criteria

- Brand kit and at least eight approved templates.
- Text, image, rectangle, ellipse, line, SVG logo/icon, groups, layers, align, lock, duplicate, crop, undo/redo, and page reorder.
- Deterministic PNG, sanitized SVG, and multi-page PDF exports.
- Human UI and REST/MCP capability parity for the supported operations.
- Signed short-lived downloads, scoped service tokens, tenant-safe object keys, audit log, quotas, and revision conflicts.
- Fuzzed scene/SVG inputs and sandboxed rendering with CPU, memory, time, filesystem, and network limits.

## Explicit non-goals

Real-time multiplayer, CRDTs, public template marketplace, stock media integrations, arbitrary plugins, animation/video, and editable PPTX.
