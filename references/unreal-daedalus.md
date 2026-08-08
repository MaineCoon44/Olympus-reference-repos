# Unreal Engine / Daedalus Reference Stack

## Goal

Equip Daedalus to operate Unreal Engine as a specialist agent using MCP tools plus Unreal-specific knowledge, rather than trying to train a foundation model from scratch.

## Primary reference repo

### gimmeDG/UnrealEngine5-mcp

- Upstream: https://github.com/gimmeDG/UnrealEngine5-mcp
- License: MIT
- Status: Under evaluation
- Purpose: Natural-language control of Unreal Engine 5.6+ through MCP.
- Strongest features:
  - Blueprint creation and node-graph editing
  - Gameplay Ability System support
  - Actor, material, transform, and asset operations
  - PCG tooling
  - RAG over Unreal Python API documentation
  - Python execution in Unreal with documentation-assisted recovery
- Why it matters to Olympus: This can become the tool layer that lets Daedalus actually manipulate Unreal Editor rather than only advise Alan what to click.
- Important caution: Experimental. Must be tested in disposable Unreal projects before production use.

Local evaluation command:

```bash
git clone https://github.com/gimmeDG/UnrealEngine5-mcp.git
```

## Agent knowledge / field manual

### ibrews/ue5-mcp

- Upstream: https://github.com/ibrews/ue5-mcp
- License: MIT (declared by upstream)
- Status: High-priority knowledge reference
- Purpose: Server-agnostic field manual for AI agents driving UE5 through MCP.
- Why it matters:
  - Documents silent-failure patterns
  - Documents known crash patterns
  - Requires inspect-before-edit and verify-after-mutate behavior
  - Covers reflection naming, Blueprint class paths, async operations, saving, graph mutation, materials, Niagara, MetaSound, UMG, and other Unreal-specific traps
  - Designed to reduce repeated agent mistakes and rediscovery
- Olympus use: Feed this knowledge into Daedalus's skill/knowledge layer after review.

Local evaluation command:

```bash
git clone https://github.com/ibrews/ue5-mcp.git
```

## Native Epic path

Epic also ships an experimental native Model Context Protocol implementation in newer Unreal Engine versions. Before installing third-party tooling into a production Unreal project, compare the native Epic MCP capabilities against the community MCP server above.

## Recommended Daedalus architecture

```text
Daedalus model
    -> UE5 field-manual knowledge
    -> MCP client
    -> Unreal MCP server
    -> Unreal Editor
    -> verify result after every mutation
```

## Adoption rule

Do not merge these projects into Olympus or an Unreal production project yet. First use a disposable Unreal test project to prove:

1. Connection stability
2. Blueprint creation
3. Asset inspection
4. Material changes
5. Sequencer/animation capability if available
6. Save/reload correctness
7. No silent corruption
8. Recovery after Unreal restart
9. Agent verification after each mutation

Final decision after testing: reference only / prototype / approved for Daedalus integration.
