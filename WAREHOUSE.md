# Olympus Tool Warehouse

This repository is the staging warehouse for external tools, frameworks, MCP servers, security systems, document tools, and reference projects that may help Olympus.

## Warehouse policy

- New tools may be added for evaluation without committing Olympus to use them.
- Default status is **Shelf / Not Installed**.
- Evaluate in isolated test environments before production use.
- Never copy secrets, API keys, passwords, or production configuration into this warehouse.
- If a tool is not used, tested, or actively planned for 30 days, mark it for review and possible removal from the warehouse index.
- Third-party source remains authoritative upstream unless we intentionally fork it.
- Record license and security implications before integration.

## Current inventory

### AI routing / model gateway

#### Free Claude Code
- Upstream: https://github.com/Alishahryar1/free-claude-code
- Category: Model/provider gateway
- Status: Shelf / Under evaluation
- Olympus use: Reference implementation for routing local, low-cost, and premium models.

### AI observability / cost tracking

#### Langfuse
- Upstream: https://github.com/langfuse/langfuse
- Clone: https://github.com/langfuse/langfuse.git
- Category: LLM observability, tracing, evaluation, cost visibility
- Status: Shelf / High priority
- Olympus use: Trace model calls, agents, latency, token use, failures, and cost. Candidate for Olympus AI black-box recorder.

### Browser control

#### Browser Use
- Upstream: https://github.com/browser-use/browser-use
- Clone: https://github.com/browser-use/browser-use.git
- Category: AI browser automation
- Status: Shelf / High priority
- Olympus use: Browser hands for Hestia and approved agents. Test in isolated browser profiles with least-privilege credentials.

### Documents / RAG

#### Docling
- Upstream: https://github.com/docling-project/docling
- Clone: https://github.com/docling-project/docling.git
- Category: Document parsing and structured ingestion
- Status: Shelf / High priority
- Olympus use: PDFs, scanned paperwork, tax/L&I documents, manuals, and RAG pipelines.

### Deterministic automation

#### n8n
- Upstream: https://github.com/n8n-io/n8n
- Clone: https://github.com/n8n-io/n8n.git
- Category: Workflow automation
- Status: Shelf / Evaluate
- Olympus use: Deterministic workflows that do not need an LLM, reducing token/API spend.

### Agent / mission orchestration

#### LangGraph
- Upstream: https://github.com/langchain-ai/langgraph
- Clone: https://github.com/langchain-ai/langgraph.git
- Category: Stateful agent/workflow orchestration
- Status: Shelf / Evaluate
- Olympus use: Checkpoints, resumable missions, conditional routing, human approval points, controlled retries.

## Hades security shelf

### Wazuh
- Upstream: https://github.com/wazuh/wazuh
- Clone: https://github.com/wazuh/wazuh.git
- Category: XDR / SIEM / endpoint monitoring
- Status: Shelf / High priority for Hades
- Hades use: Central security telemetry, file-integrity monitoring, vulnerability events, endpoint alerts, and response coordination.

### Gitleaks
- Upstream: https://github.com/gitleaks/gitleaks
- Clone: https://github.com/gitleaks/gitleaks.git
- Category: Secret detection
- Status: Shelf / High priority for Hades
- Hades use: Pre-commit, repository, file, and CI secret scanning. Candidate component for Hades Secret Gate.

### TruffleHog
- Upstream: https://github.com/trufflesecurity/trufflehog
- Clone: https://github.com/trufflesecurity/trufflehog.git
- Category: Secret discovery and credential verification
- Status: Shelf / High priority for Hades
- Hades use: Second independent secret detector; useful for scanning repositories, files, and historical commits.

### Microsoft Defender integration
- Upstream system: Windows Microsoft Defender / Defender PowerShell APIs
- Category: Antivirus / endpoint protection
- Status: Native Windows capability; no third-party repo required
- Hades use: Read Defender health, scan status, signatures, and threat history; initiate approved scans/updates.

### Future Hades candidates
- YARA-X — malware/rule-based file inspection
- Sigma — portable security detection rules
- ClamAV — secondary malware scanner
- Sysmon — richer Windows process/network telemetry

## Media / production shelf

### Unreal Engine MCP for Daedalus
- Upstream: https://github.com/gimmeDG/UnrealEngine5-mcp
- Category: Unreal MCP tool layer
- Status: Shelf / High priority
- Olympus use: Give Daedalus direct controlled Unreal Editor operations.

### UE5 MCP Field Manual
- Upstream: https://github.com/ibrews/ue5-mcp
- Category: Unreal agent knowledge / skill
- Status: Shelf / High priority
- Olympus use: Teach Daedalus UE5 failure modes, safe sequences, verification, and known editor traps.

### DaVinci Resolve MCP
- Upstream: https://github.com/lordhoell/davinci-resolve-mcp
- Category: DaVinci Resolve MCP + agent skill
- Status: Shelf / High priority
- Olympus use: Programmatic editing, Fusion, color, captions, media management, and rendering.

## Evaluation labels

- **Shelf / Not Installed** — recorded, not tested
- **Under evaluation** — actively being inspected
- **Prototype** — running only in a test environment
- **Approved** — reviewed for Olympus integration
- **Rejected** — keep notes briefly, then remove
- **30-day review** — no use/activity for 30 days; decide whether to keep or purge
