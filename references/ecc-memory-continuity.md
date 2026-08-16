# ECC — Memory and Continuity Evaluation

## Upstream

- Repository: https://github.com/affaan-m/ECC
- License: MIT

## Why Olympus saved it

ECC is an agent harness operating system with planning, testing, review, verification, memory, continuous learning, session summaries, reusable instincts/skills, hooks, rules, and security scanning.

The part Olympus cares about most is not the full harness. The priority is to inspect ECC's memory and continuity machinery for pieces that can help solve persistent cross-session memory for:

- Codex
- Hestia
- Zeus and Olympus workers
- project-specific state
- lessons learned and superseded decisions
- restart/session recovery

## Specific questions to answer later

1. How does ECC decide what should become durable memory?
2. Where and how is memory persisted?
3. How are session summaries generated and restored?
4. How does continuous learning turn repeated wins into reusable skills or instincts?
5. How does it prevent stale or superseded information from being treated as current truth?
6. How much context must be loaded into a fresh session?
7. Can its memory components be separated from the rest of ECC?
8. Can Codex, Hestia, and Olympus agents share one durable source of truth without importing ECC's entire orchestration layer?
9. How does ECC behave across restarts, new sessions, and different machines?
10. How does its approach compare with Olympus's existing mission records, project context, memory files, and Agency Continuity Audit plugin?

## Desired Olympus target

A layered shared-memory system:

- permanent facts / standing rules
- project-specific context
- current working state and next actions
- decisions and corrections
- lessons learned / failed approaches
- superseded facts retained as history but clearly marked non-current
- full evidence/history available on demand rather than injected into every prompt

Fresh sessions should automatically retrieve the minimum relevant state before acting.

## Proposed bench test

Do not install ECC into live Olympus first.

1. Inspect ECC's memory/session/continuous-learning implementation in an isolated sandbox.
2. Extract or reproduce only the smallest useful memory components.
3. Create a disposable shared-memory prototype.
4. Run work in Session A and end it normally.
5. Start a completely fresh Session B with no conversational context.
6. Require Session B to correctly recover objective, current state, decisions, blockers, failed attempts, and next action.
7. Restart the machine/service and repeat with Session C.
8. Run Agency Continuity Audit against the result.
9. Only consider integration if continuity is proven from stored evidence rather than self-reported success.

## Risks / overlap

ECC is large and overlaps with Olympus planning, agent roles, workflow control, security, and orchestration. Do not install the entire framework into live Olympus merely to obtain memory features.

Potential conflicts include:

- Zeus mission coordination
- Atlas review/QA
- Olympus worker roles
- existing security/permission boundaries
- existing memory and project-context services
- duplicated hooks and workflow rules

## Status

**Backlog — high-value memory/continuity investigation.**

Do not interrupt current Patrol Playback / video-production work. Return to this after product is moving onto YouTube.
