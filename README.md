# Olympus Reference Repositories

This repository is an index of third-party/open-source projects being evaluated as reference material for Olympus.

The goal is to keep useful external projects easy to find without mixing third-party source code into the Olympus production repository.

## Rules

- Treat every listed project as external reference material until it has been separately reviewed and approved.
- Do not copy third-party source code into Olympus production just because it is listed here.
- Record the upstream repository, license, purpose, evaluation notes, and possible Olympus use before adopting anything.
- Preserve Olympus security rules, including the single secure gateway/front door and private internal services.
- Never commit secrets, API keys, passwords, or tokens to this repository.

## Reference Projects

### Free Claude Code

- **Upstream:** https://github.com/Alishahryar1/free-claude-code
- **Category:** AI model/provider router and compatibility proxy
- **Status:** Under evaluation
- **Why we saved it:** It overlaps strongly with the model-routing and AI-egress layer planned for Olympus. It can route Claude Code/Codex-style traffic to multiple backends, including local models and cloud providers.
- **Potential Olympus value:** provider abstraction, local-model routing, model/provider switching, controlled fallbacks, admin/configuration concepts, and cost-control opportunities.
- **Important note:** This does not make paid models cheaper by itself. Savings come from routing work to lower-cost or local models when appropriate.
- **Adoption decision:** Do not integrate directly into Olympus until architecture, security, fallback behavior, licensing, and cost controls have been reviewed.

### Unreal Engine / Daedalus

- **Primary MCP:** https://github.com/gimmeDG/UnrealEngine5-mcp
- **Agent field manual:** https://github.com/ibrews/ue5-mcp
- **Category:** Unreal Engine agent tooling and knowledge
- **Status:** Under evaluation
- **Notes:** See `references/unreal-daedalus.md`.

### DaVinci Resolve Agent

- **Primary MCP:** https://github.com/lordhoell/davinci-resolve-mcp
- **Category:** AI-driven video editing / Resolve automation
- **Status:** Under evaluation
- **Notes:** See `references/davinci-resolve-agent.md`.

### VoxCPM2

- **Upstream:** https://github.com/OpenBMB/VoxCPM
- **Category:** Local/open-source text-to-speech and voice cloning
- **License:** Apache-2.0
- **Status:** High-priority prototype candidate
- **Why we saved it:** Tokenizer-free TTS with controllable and high-fidelity voice cloning, 48 kHz output, multilingual support, local inference, and production-serving options. Potential replacement or fallback for recurring commercial TTS workloads.
- **Potential Olympus value:** Hestia voice, Patrol Playback narration, Daily Operations narration, PM Videos, batch voice generation, and a provider-independent internal voice service.
- **Notes:** See `references/voxcpm2.md`.

## Suggested evaluation record for future repos

For every new reference project, add:

1. Project name
2. Upstream URL
3. License
4. What it does
5. Why it may help Olympus
6. Security concerns
7. Cost implications
8. Components worth studying/reusing
9. Components to avoid
10. Final decision: reject / reference only / prototype / approved for integration
