# DaVinci Resolve Agent Reference Stack

## Goal

Equip an Olympus video-production specialist to operate DaVinci Resolve programmatically for editing, timelines, color, Fusion, captions/audio, and rendering.

## Primary reference repo

### lordhoell/davinci-resolve-mcp

- Upstream: https://github.com/lordhoell/davinci-resolve-mcp
- License: MIT
- Status: Under evaluation
- Purpose: MCP server exposing the DaVinci Resolve scripting API to an AI agent.
- Upstream currently documents 440+ tools across Resolve.
- Major areas:
  - Project management
  - Timeline editing
  - Media pool organization
  - Clip operations
  - Color grading
  - Rendering
  - Fusion compositing
  - Gallery/stills
  - Captions/audio
  - Resolve application control
- Includes an agent skill explaining object chaining, workflows, Fusion wiring, and render settings.
- Requirements noted upstream: Resolve 19+; Python 3.10+; MCP server on the same machine as Resolve.
- Why it matters to Olympus: This can provide the actual hands/tools for a video-production agent instead of having an LLM merely describe editing steps.

Local evaluation command:

```bash
git clone https://github.com/lordhoell/davinci-resolve-mcp.git
```

## Recommended agent architecture

```text
Video-production agent
    -> Resolve workflow skill
    -> MCP client
    -> DaVinci Resolve MCP
    -> Resolve scripting / Fusion API
    -> DaVinci Resolve
    -> render/test/verify output
```

## First evaluation tests

Use disposable media and a disposable Resolve project. Prove the agent can:

1. Detect/open Resolve
2. Create or open a project
3. Import media
4. Create a timeline
5. Add clips in a requested order
6. Add a title
7. Perform a basic color operation
8. Generate or manage captions if supported
9. Configure a render
10. Render a short test video
11. Verify the output file exists and is playable

## Safety / production rule

Do not point an experimental agent at irreplaceable Resolve projects. Back up the project before agent-driven edits. Keep source media read-only where practical during early testing.

Final decision after testing: reference only / prototype / approved for video-agent integration.
