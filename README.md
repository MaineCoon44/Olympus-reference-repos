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
- **Potential Olympus value:**
  - Provider abstraction
  - Local-model routing
  - OpenAI/Anthropic-compatible proxying
  - Model/provider switching
  - Controlled fallback patterns
  - Admin/configuration interface concepts
  - Cost-control opportunities by routing routine work to local or lower-cost models
- **Important note:** This does not make paid models cheaper by itself. Savings come from routing work to lower-cost or local models when appropriate.
- **Adoption decision:** Do not integrate directly into Olympus until architecture, security, fallback behavior, licensing, and cost controls have been reviewed.

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
