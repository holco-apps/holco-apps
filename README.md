# HOLCO

Custom AI engineering for executives. We build conversational agents that
plug into the systems an operator already runs — CRM, ERP, accounting,
point-of-sale, scheduling — and expose them as direct, real-time queries
in the format that fits the operator's rhythm.

Paris, France · [holco.co](https://holco.co) · [apps.holco.co](https://apps.holco.co)

## Public projects

### [pennylane-cabinet](./pennylane-cabinet)

Claude Desktop extension (`.mcpb`) for French accounting firms running
on Pennylane. Three read-only MCP tools : overdue customer invoices,
synthetic P&L, monthly close report. Local execution, no third-party
server in the data path. Status: restricted pilot. The bundle is
shipped to pilot firms after a scoping call — request via
[alan@holco.co](mailto:alan@holco.co).

`mcp` · `claude-desktop` · `pennylane` · `accounting` · `france`

### [openrmn](./openrmn)

Independent retail media analytics layer. Unifies Amazon Ads, Criteo
and Unlimitail into a single schema (`UnifiedRow`), computes
deterministic KPIs, neutrality audit, Trust Score per network,
double-counting audit and harmonization simulator. The full analytics
surface is also exposed as an MCP server, queryable from Claude
Desktop, Claude Code or any MCP-compatible agent. Live demo :
[lab.holco.co/retail-audience](https://lab.holco.co/retail-audience).

`mcp` · `retail-media` · `attribution` · `amazon-ads` · `criteo` · `adcp`

## Stack and dependencies

- **Models** : Anthropic (Claude Sonnet / Opus / Haiku), Mistral, OpenAI
  — model selection is per use case, no exclusive partnership.
- **Integration layer** : Model Context Protocol (MCP) as the primary
  bridge between AI runtimes and customer systems. AdCP for retail
  media.
- **Hosting** : EU only (DigitalOcean FRA1). Self-hosted runtimes on
  request.

## Engineering posture

- **Local first.** Customer data should not transit through a HOLCO
  server unless the use case requires it. `pennylane-cabinet` is the
  reference pattern : Claude Desktop talks directly to the third-party
  API ; we ship the bundle, never see the data.
- **Read-only by default.** Write tools follow a mandatory `preview →
  commit` pattern.
- **Auditable.** Every tool documents its inputs, outputs and the
  upstream references it cites.
- **No training on customer data.** API runtimes are configured to
  exclude inputs/outputs from training corpora.

## Contact

[alan@holco.co](mailto:alan@holco.co) — pilot enrolment, integration
questions, security disclosures.

HOLCO INVEST — Paris, France — SIREN 819 582 453 — Paris RCS.
