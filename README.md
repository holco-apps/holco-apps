# HOLCO

> Custom AI engineering for executives. Paris, France.

We build conversational AI agents that plug into the systems an operator already runs (CRM, ERP, accounting, retail data, mailbox) and expose them as **direct, real-time queries** — chat, voice, recurring email, alerts, or dedicated cockpit apps. The executive asks; the AI answers in 6 to 10 seconds, with sources.

We are agnostic on the AI engine (Anthropic Claude, Mistral, OpenAI) and opinionated on the way data flows. No customer data on our side. Tokens stay on the user's workstation. Read-only by default; write tools require a mandatory preview → commit pattern.

- **Site:** [holco.co](https://holco.co) (FR) · [apps.holco.co](https://apps.holco.co) (EN tech docs)
- **Machine-readable:** [llms.txt](https://holco.co/llms.txt) · [humans.txt](https://holco.co/humans.txt) · [/.well-known/mcp-server.json](https://holco.co/.well-known/mcp-server.json) · [/dev](https://holco.co/dev) · [/status](https://holco.co/status)
- **Sectors:** Media & AdTech · Finance · Preventive health
- **Legal entity:** HOLCO INVEST, SIREN 819 582 453, RCS Paris

---

## Public projects

### [pennypilot](https://github.com/holco-apps/pennypilot) — MCP server for Pennylane

MCP (Model Context Protocol) extension that bridges Claude Desktop — and soon Mistral Le Chat and ChatGPT Business — directly to Pennylane Company API v2 for French accounting firms. Generates the monthly closing memo in ~8 seconds instead of 1h30. **13 read-only tools** covering the full general ledger: journals (VE/AC/BQ/OD), French PCG chart of accounts, per-account ledger with running balance, pending lettering on 411\*/401\*, audit trail via `/ledger_entry_line_changes`, fiscal years.

Listed on the official **MCP Registry** as [`io.github.holco-apps/pennypilot`](https://registry.modelcontextprotocol.io/?search=pennypilot). v0.2.6. 49 tests. Bundle SHA-256 published. CI green on Node 20 + 22.

Notable design choices: context-guard before heavy analysis (auto-detect SIREN + NAF via Etalab open data), in-flight dedup and 4-way concurrency gate on the Pennylane client, request-ID propagation (client `pp-<hex>` + server id) injected into error messages, lazy `stream()` pipeline on top of cursor pagination.

> `mcp` · `model-context-protocol` · `anthropic` · `claude-desktop` · `pennylane` · `accounting` · `france` · `nodejs` · `typescript`

### [openrmn](https://github.com/holco-apps/openrmn) — Independent retail media analytics

Unifies Amazon Ads, Carrefour Links, Citrus and Promo Intelligence into a single schema (`UnifiedRow`), computes deterministic KPIs, neutrality audit, Trust Score per network, double-counting audit and harmonisation simulator. The full analytics surface is also exposed as an MCP server, queryable from Claude Desktop, Claude Code, or any MCP-compatible agent. Live demo: [lab.holco.co/retail-audience](https://lab.holco.co/retail-audience).

> `mcp` · `retail-media` · `attribution` · `amazon-ads` · `python` · `streamlit`

---

## Closed-source products (live, real users)

- **[AEObrand](https://holco.co/aeobrand/)** — measures how cosmetic brands surface inside conversational AI engines (ChatGPT, Gemini, Claude). MVP in production.
- **[MyCFO FEC](https://mycfofec.pro)** — generates commercial proposals for accounting firms from a French FEC ledger. Beta.
- **[ALIM.care](https://alim.care)** — clinical prescription-support tool for doctors and dietitians.
- **[Oyya](https://oyya.fr)** — naturopath AI platform.
- **Clarislab** — conversational explainer for blood test results.
- **[Undone Project](https://undoneproject.com)** — longevity community.

---

## Who builds this

Founded and coded by **Pierre Coquard** (ESSEC Business School). Twenty years as an operator before HOLCO: ex-CEO of a Euronext-listed media group (**New Planet Media**, 2019–2022), co-founder of **R-TARGET** (real-time email targeting, tripled revenue in 2 years, acquired by **CCM Benchmark**), Director Sales Division at **Groupe Figaro** (2015–2018). The production code is written by the founder.

Contact: `alan@holco.co` (supervised assistant + team routing) · `pierre@holco.co` (founder, direct).

---

## Engineering principles

1. Customer data never transits HOLCO infrastructure. Tokens stay on the user's workstation. We hash, we don't store.
2. Read-only by default. Write tools require a preview → commit pattern with an explicit user confirmation.
3. Context before analysis. We ask, we don't pretend.
4. Numbers, not adjectives. Every claim ships with the SQL, the endpoint or the timestamp that produced it.
5. We optimise for the person reading the answer at 22:00, not for the demo on the projector at 14:00.
6. If the LLM cannot explain it in plain French to the user, we don't ship it.
7. Public source for everything that does not encode a client's process. Proprietary for everything that does.
