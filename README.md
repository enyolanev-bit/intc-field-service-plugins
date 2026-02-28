# InTC Field Service Plugins

> **The Glean for Field Service** — Vertical RAG copilots that turn 8 years of real field data into AI systems no horizontal platform can build. Powered by [Claude Code](https://docs.anthropic.com/en/docs/agents-and-tools/claude-code/overview) and [Claude Cowork](https://docs.anthropic.com/en/docs/agents-and-tools/cowork).

**Inspired by [anthropics/financial-services-plugins](https://github.com/anthropics/financial-services-plugins)** (4K+ stars) — same architecture, applied to Field Service instead of Finance.

## The Problem

Every RAG platform (Glean, Ragie, Morphik, Vectara, Onyx) builds **horizontal** infrastructure. None of them:
- Know the difference between a Bowie-Dick cycle and an empty cycle
- Understand why field technicians bypass the CRM
- Can structure intervention reports into exploitable diagnostic data
- Comprehend SLA, FTFR, MTTR as critical Field Service KPIs
- Have 8 years of real field experience to validate copilot answers

**They build the rails. We know where to go.**

## The Vision

InTC builds **vertical RAG copilots** for Field Service — pre-trained on real intervention data, equipment manuals, and diagnostic patterns. Not generic search. Domain intelligence.

```
Glean ($7.2B)    = "Work AI" for every enterprise
InTC             = "Field Service AI" for every technician
```

**Stack:** [Morphik](https://github.com/morphik-org/morphik-core) (multimodal RAG) · [Onyx](https://github.com/onyx-dot-app/onyx) (chat UI) · [LangChain](https://github.com/langchain-ai/langchain) (orchestration)

## Plugin Marketplace

| Plugin | Type | What it does | Status |
|--------|------|-------------|--------|
| **[field-ops-core](./field-ops-core)** | Core (install first) | KPI dashboards, config audits, adoption diagnostics, scheduling optimization. Foundation + all data connectors. | 🔴 Building |
| **[equipment-intelligence](./equipment-intelligence)** | **Product** | **RAG copilots by industry** — fitness tech, sterilization, medical devices, HVAC. Multimodal: embeds schematics, diagrams, photos. **This IS the product.** | 🔴 Building |
| **[field-ops-audit](./field-ops-audit)** | Add-on | 5-Bloc audit framework, client screening, quick wins, value creation plans. | 🔴 Building |
| **[client-consulting](./client-consulting)** | Add-on | Audit reports, ROI calculators, optimization plans, client decks. Professional deliverables. | 🔴 Building |
| **[ai-copilot-builder](./ai-copilot-builder)** | Factory | Build, train, and deploy RAG copilots for new industries. The tool that builds the tools. | 🔵 Planned |
| **[partner-built](./partner-built)** | Community | Third-party plugins for specific equipment or platforms. | 🔵 Planned |

## Commands

```bash
# === CORE ===
/audit-terrain [client]          # Complete 5-Bloc field service audit
/kpi-dashboard [FTFR|MTTR|SLA]  # KPI dashboard with industry benchmarks
/check-config [FSL|ServiceMax]   # Platform configuration quality check
/diagnostic-adoption [org]       # Why technicians bypass the CRM
/rapport-intervention [equipment] # Structured intervention report

# === EQUIPMENT INTELLIGENCE (RAG) ===
/diagnose [equipment] [symptom]  # RAG-powered diagnostic (sourced answers)
/maintenance-plan [asset-type]   # Preventive maintenance calendar
/parts-lookup [model] [error]    # Parts + error code lookup via RAG

# === AUDIT ===
/audit-checklist [client]        # Due diligence checklist
/screen-client [company]         # Qualify a prospect
/quick-wins [org]                # 5 optimizations in 30 days

# === CONSULTING ===
/audit-report [client]           # Professional audit report (PDF/PPTX)
/roi-calculator [optimization]   # ROI calculation with methodology
/client-review [client]          # Meeting prep brief
/client-deck [client] [type]     # Branded presentation deck

# === COPILOT BUILDER (factory) ===
/build-rag [industry] [source]   # Build a RAG for a new industry vertical
/train-copilot [use-case]        # Train copilot on domain data
/deploy-agent [platform]         # Deploy agent to Salesforce/ServiceMax/SAP
```

## The 5-Bloc Framework

Every field service operation is assessed through 5 interconnected blocs:

1. **Workflow** — How work flows from request to completion
2. **SLA** — Service Level Agreement definitions, measurement, compliance
3. **KPI** — Are the right metrics tracked and driving decisions?
4. **Adoption** — Are field teams actually using the system?
5. **Architecture** — Is the platform configured correctly?

## MCP Integrations

All connectors centralized in **field-ops-core**, shared across all plugins.

| Provider | What it connects |
|----------|-----------------|
| Salesforce FSL | Work Orders, Service Appointments, Assets, Knowledge |
| ServiceMax | Asset 360, Installed Base, Work Order Debrief |
| SAP PM/CS | Equipment, Functional Location, Maintenance Plans |
| Notion | InTC Bible, audit docs, client pipeline |
| Glean | Enterprise search across all connected systems (future) |

## Equipment Intelligence — The Product

`equipment-intelligence` is not just a plugin. It's the **core product** of InTC.

Each industry vertical gets its own RAG copilot, pre-trained on real field data:

| Vertical | Data Sources | Status |
|----------|-------------|--------|
| **Fitness Technology** (Technogym) | Intervention reports, equipment manuals, sensor data, SAV history | 🔴 Building (Morphik) |
| **Sterilization & Autoclave** (A-dec/Euronda) | Cycle protocols, CE/FDA standards, failure patterns, Bowie-Dick validation | 🔵 Planned |
| **Medical Devices** | Equipment manuals, compliance docs, maintenance procedures | 🔵 Planned |
| **Industrial HVAC** | Technical specs, seasonal maintenance, energy optimization | 🔵 Planned |

**Why Morphik:** Equipment manuals are 80% visual — electrical diagrams, schematics, exploded views, wiring photos. Text-only RAG fails. Morphik's [ColPali multimodal embeddings](https://github.com/morphik-org/morphik-core) embed entire pages (image + text) without OCR. Region-level retrieval finds THE diagram zone that answers the query.

**Why it's impossible to replicate:** A Salesforce developer can build a RAG pipeline. But they don't know WHAT to put inside. They don't know that Error E07 on a Technogym Skillmill means the inverter board needs replacement, not the motor. They don't know that a Bowie-Dick cycle failure at 134°C usually indicates an air leak, not a heater issue. **8 years of field patterns encoded in AI** — that's the moat.

## Architecture

```
plugin-name/
├── .claude-plugin/plugin.json   # Manifest
├── .mcp.json                    # Tool connections (core only)
├── commands/                    # Slash commands (explicit invocation)
├── skills/                      # Domain knowledge (auto-triggered)
└── hooks/                       # Event-driven automation
```

Every component is file-based — markdown and JSON. No code, no infrastructure, no deployment.

## Competitive Landscape

InTC operates at the intersection of two validated markets:

| Platform | What they do | Valuation | Gap |
|----------|-------------|-----------|-----|
| **Glean** | Enterprise AI search, 100+ connectors | $7.2B | Horizontal — no field service domain knowledge |
| **Ragie** | Managed RAG-as-a-Service | $5.5M seed | API-first but no vertical expertise |
| **Morphik** | Multimodal RAG, ColPali, knowledge graph | YC W24 | Infrastructure — InTC uses it as engine |
| **Vectara** | Anti-hallucination RAG (HHEM) | ~$100M | Enterprise pricing, no field service |
| **Onyx** | Open-source enterprise search | YC | Chat UI — InTC uses it as interface |

**InTC's position:** We don't compete with infrastructure. We BUILD ON infrastructure (Morphik + Onyx) and add the **vertical intelligence layer** that no horizontal platform can replicate.

> Full benchmark: [Intelligence RAG — Benchmark Concurrentiel](https://www.notion.so/315ca3c6995a817cabcdcc55da3ea445)

## Roadmap

### H1 — The Lab (now)
- [ ] `field-ops-core` with 3 skills + 2 commands
- [ ] First RAG prototype: Technogym data → Morphik → sourced answers
- [ ] MIT Module 5 assignment = RAG on real Technogym data
- [ ] Test on real intervention reports (1 year export)

### H2 — The Product (6-18 months)
- [ ] `equipment-intelligence` with Technogym RAG v1
- [ ] Second vertical: dental/sterilization (A-dec + Euronda data)
- [ ] `ai-copilot-builder` for replicable RAG deployment
- [ ] First paying RAG client
- [ ] CESI incubator application with deployed prototype

### H3 — The Scale (18+ months)
- [ ] Multi-tenant: each client gets isolated copilot fed by THEIR data
- [ ] API-first for CRM integration (Salesforce, ServiceMax, SAP)
- [ ] `partner-built/` ecosystem for community plugins
- [ ] Y Combinator application: live prototype, 5+ clients, revenue

## Getting Started

```bash
# Add the marketplace
claude plugin marketplace add enyolanev-bit/intc-field-service-plugins

# Install the core plugin first (required)
claude plugin install field-ops-core@intc-field-service-plugins

# Then add function-specific plugins
claude plugin install equipment-intelligence@intc-field-service-plugins
claude plugin install field-ops-audit@intc-field-service-plugins
claude plugin install client-consulting@intc-field-service-plugins
```

## Built by InTC

**InTC** — Vertical AI for Field Service Operations

Founded by [Nevil Enyola Bofumbo](https://www.linkedin.com/in/nevilenyola/) — 8 years of real field service operations across medical devices (A-dec, Henry Schein), fitness technology (Technogym), and sterilization equipment. Currently completing MIT Professional Education in Applied Generative AI.

The only Field Service AI builder who comes FROM the field, not from IT.

**Strategy:** [Bible InTC — Chemin B+](https://www.notion.so/313ca3c6995a8143a31dcedcf4d805a2)

## License

[Apache License 2.0](./LICENSE)
