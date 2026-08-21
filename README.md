# Arkova Studio

Private, template-first creative tooling for Arkova. The objective is to replace the repeatable 80% of Canva usage while giving people, Codex, Claude, and Arkova services the same safe product surface.

## Decision

- Build on [Fabric.js](https://github.com/fabricjs/fabric.js) (MIT) behind an Arkova-owned, versioned `ArkovaDesign` JSON schema.
- Start with 8–12 locked brand templates, a light human editor, an asset library, and PNG/SVG/PDF export.
- Treat presentations as multi-page designs; evaluate PptxGenJS only after the core workflow is proven.
- Use [Tela](https://github.com/heyimjames/tela) and [Open Design](https://github.com/clawnify/open-design) only as pattern references. Evaluate [Penpot](https://github.com/penpot/penpot) only if a full design suite becomes necessary.

## Agent contract

The REST API is the source of truth and the MCP server is a thin policy adapter. Initial tools: `templates_list`, `templates_get`, `designs_create`, `designs_get`, `designs_apply_operations`, `assets_list`, `assets_upload`, `renders_create`, `renders_status`, and `designs_validate_brand`.

Agents submit schema-validated declarative operations. They never execute JavaScript in the editor or render worker.

## V1 guardrails

- No arbitrary remote asset URLs; assets are ingested, byte-verified, size-limited, and scanned first.
- Sanitize imported/exported SVG and isolate render workers with no outbound network.
- Require optimistic version checks and idempotency keys for mutations.
- Record font and asset licensing plus generated-asset provenance.
- Defer live collaboration, stock libraries, plugins, video, and animation.

## Delivery gate

Run a one-week spike with three real Arkova templates. Proceed only if browser/server output is acceptably consistent for fonts, crop/mask, PNG, SVG, and PDF. A production MVP is estimated at 12–18 engineer-weeks, so this is not a cost-saving project unless the narrow template workflow proves materially smaller.

See [docs/product-contract.md](docs/product-contract.md) for scope and acceptance criteria.
