# InTC Field Service Plugins

> Plugins that turn Claude into a specialist for Field Service Operations — audit, KPI, RAG, copilot. Built for [Claude Code](https://claude.com/product/claude-code) and [Claude Cowork](https://claude.com/product/cowork).

**Inspired by [anthropics/financial-services-plugins](https://github.com/anthropics/financial-services-plugins)** (4K+ stars) — same architecture, applied to Field Service instead of Finance.

## Why Plugins

These plugins encode **8 years of real field service experience** (A-dec, Henry Schein, Technogym) into reusable skills, commands, and MCP connectors. A Salesforce developer can build a plugin. But they don't know WHAT to put inside. We do.

## Plugin Marketplace

| Plugin | Type | How it helps | Connectors |
|--------|------|-------------|------------|
| **[field-ops-core](./field-ops-core)** | Core (install first) | KPI dashboards, config audits, adoption diagnostics, scheduling optimization. Provides the shared foundation and all data connectors. | Salesforce FSL, ServiceMax, SAP PM, Notion, Glean |
| **[field-ops-audit](./field-ops-audit)** | Add-on | Audit checklists, client screening, quick wins, value creation plans. The 5-Bloc Framework for systematic field service assessment. | — |
| **[client-consulting](./client-consulting)** | Add-on | Audit reports, ROI calculators, optimization plans, client presentation decks. Professional deliverables for consulting engagements. | — |

**13 skills, 11 commands, 5 MCP integrations**

## Getting Started

```bash
# Add the marketplace
claude plugin marketplace add enyolanev-bit/intc-field-service-plugins

# Install the core plugin first (required)
claude plugin install field-ops-core@intc-field-service-plugins

# Then add function-specific plugins
claude plugin install field-ops-audit@intc-field-service-plugins
claude plugin install client-consulting@intc-field-service-plugins
```

Once installed, slash commands are available:

```bash
/audit-terrain [client]          # Complete 5-Bloc field service audit
/kpi-dashboard [FTFR|MTTR|SLA]  # KPI dashboard with industry benchmarks
/check-config [FSL|ServiceMax]   # Platform configuration quality check
/diagnostic-adoption [org]       # Why technicians bypass the CRM
/audit-checklist [client]        # Due diligence checklist
/screen-client [company]         # Qualify a prospect for InTC
/quick-wins [org]                # 5 optimizations in 30 days
/audit-report [client]           # Professional audit report
/roi-calculator [optimization]   # ROI calculation with methodology
/client-review [client]          # Meeting prep brief
/client-deck [client] [type]     # Branded presentation deck
```

## The 5-Bloc Framework

Every field service operation is assessed through 5 interconnected blocs:

1. **Workflow** — How work flows from request to completion
2. **SLA** — Service Level Agreement definitions, measurement, compliance
3. **KPI** — Are the right metrics tracked and driving decisions?
4. **Adoption** — Are field teams actually using the system?
5. **Architecture** — Is the platform configured correctly?

## MCP Integrations

All connectors are centralized in **field-ops-core** and shared across all plugins.

| Provider | Description |
|----------|-------------|
| Salesforce FSL | Work Orders, Service Appointments, Assets, Knowledge |
| ServiceMax | Asset 360, Installed Base, Work Order Debrief |
| SAP PM/CS | Equipment, Functional Location, Maintenance Plans |
| Notion | InTC Bible, audit documentation, client pipeline |
| Glean | Enterprise search across all connected systems (future) |

## How Plugins Work

```
plugin-name/
├── .claude-plugin/plugin.json   # Manifest
├── .mcp.json                    # Tool connections
├── commands/                    # Slash commands you invoke explicitly
└── skills/                      # Domain knowledge Claude draws on automatically
```

Every component is file-based — markdown and JSON, no code, no infrastructure.

## Built by InTC

**InTC** — Field Service Operations &amp; CRM Optimization

Founded by Nevil Enyola Bofumbo — 8 years of real field service operations (medical devices, fitness technology, sterilization equipment). The only Field Service consultant who comes FROM the field, not from IT.

## License

[Apache License 2.0](./LICENSE)
