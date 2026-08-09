# Agent Reach

- **Upstream:** https://github.com/Panniantong/Agent-Reach
- **License:** MIT
- **Category:** Internet capability layer / multi-platform research tooling for AI agents
- **Status:** Under evaluation

## What it does

Agent Reach gives command-capable AI agents a common access layer for internet research across multiple platforms. It installs and health-checks platform-specific backends and can route around broken access methods with primary/fallback backends.

Current documented capabilities include web reading, web search, GitHub read/search, YouTube read/search with subtitles and metadata through yt-dlp, RSS, Twitter/X, Reddit, Facebook, Instagram, LinkedIn, Bilibili, XiaoHongShu, podcasts, and other platform-specific tools. Some platforms are zero-configuration; others require cookies, a logged-in browser session, or optional setup.

## Why it may help Olympus

Agent Reach is a strong candidate for the starting point of an **Olympus Internet Capability Layer**. Instead of teaching every Olympus agent how to scrape or access each website separately, Olympus could expose approved capabilities such as:

- `web.read`
- `web.search`
- `youtube.search`
- `youtube.inspect`
- `github.search`
- `reddit.search`
- `rss.read`

Olympus would remain the authority over which agents are allowed to use each capability, while Agent Reach or selected adapters provide the underlying access method.

## High-value Olympus use cases

### YouTube research

The YouTube path is especially valuable. Agent Reach currently uses yt-dlp for video metadata/subtitles and search across YouTube and many other supported video sites.

Potential Olympus workflow:

1. Search for relevant videos in a market or topic.
2. Capture title, channel, date, duration, description, metadata, and available subtitles/transcript.
3. Analyze opening hooks, topic structure, narration, recurring language, pacing from transcript timestamps, and subject trends.
4. Combine this later with a separate visual-analysis pipeline that samples frames/scenes, thumbnails, graphics, on-screen text, B-roll, animation style, and other visual features.
5. Store the resulting competitive research in the appropriate project documentation and memory system.

This could support automated research for AI videos, true crime, history/collapse, scary stories, trending subjects, top-10 content, game-development tutorials, Unreal Engine training material, and other Olympus projects.

### Research agents

Hestia and approved research agents could use Agent Reach to gather information without each agent having independent unrestricted internet implementations.

### Adapter/fallback architecture

A major design idea worth preserving is that the **capability should be stable even if the backend changes**. Example:

```text
Olympus YouTube Capability
        |
        +-- preferred backend
        +-- fallback backend
        +-- future official API backend
        +-- future transcript/vision backend
```

Hestia should ask for a capability such as `youtube.inspect`; she should not need to know whether yt-dlp, an official API, a browser tool, or another adapter is fulfilling it.

## Components worth studying or reusing

- Capability abstraction by platform
- Primary/fallback backend routing
- Health diagnostics (`agent-reach doctor` concept)
- Skill-based integration for command-capable agents
- yt-dlp YouTube metadata/subtitle/search workflow
- Jina Reader web-page normalization pattern
- GitHub CLI integration pattern
- RSS ingestion
- Optional per-platform configuration rather than requiring every dependency up front
- Local handling of cookies/credentials where applicable

## Security concerns

Do **not** give every Olympus agent unrestricted internet access.

Recommended Olympus controls:

- Allow-list capabilities by agent and role.
- Route all externally accessible traffic through the Olympus secure gateway/front door where applicable.
- Keep internal Olympus services private.
- Store cookies, tokens, browser credentials, and API secrets outside repositories and outside prompts.
- Treat browser-session/cookie-based access as sensitive.
- Sandbox third-party command-line tools before production use.
- Log each external research request with requesting agent, capability, target domain/platform, result status, duration, and cost if any.
- Add rate limits and kill switches.
- Prefer read-only access unless a mission explicitly requires a write action and receives appropriate approval.

## Cost implications

The upstream project states that its tools/APIs are free, with possible proxy cost in restricted networks. However, Olympus should independently verify each backend before production use because third-party pricing, rate limits, availability, and terms can change.

YouTube transcript/metadata analysis itself can be inexpensive, but downstream LLM analysis and future full-frame/video vision analysis may create significant compute/API costs. All such work should go through Olympus cost tracking and model routing.

## Important limitation: transcript analysis is not full visual watching

Agent Reach's current YouTube capability primarily provides metadata, search, and subtitle/transcript access. This lets an agent understand what was said and many structural properties of a video, but it does not by itself guarantee full visual understanding of every frame.

For Olympus, plan a second stage for true visual study:

```text
YouTube URL
    |
    +-- Agent Reach / yt-dlp
    |      +-- metadata
    |      +-- subtitles/transcript
    |      +-- timing information
    |
    +-- Olympus Video Analysis
           +-- sampled frames
           +-- scene changes
           +-- on-screen text
           +-- thumbnails
           +-- visual hooks
           +-- graphics/B-roll
           +-- pacing/style
```

## Proposed Olympus adoption path

1. **Reference only:** keep this upstream project cataloged here.
2. **Sandbox prototype:** test Agent Reach in an isolated environment with no production secrets.
3. **YouTube-first evaluation:** confirm search, metadata, subtitle/transcript retrieval, diagnostics, and failure handling.
4. **Internet Capability API:** design an Olympus-owned interface above it so Hestia and other agents call stable Olympus capabilities rather than third-party commands directly.
5. **Security and observability:** add permissions, logging, rate limits, cost tracking, and health reporting.
6. **Visual video analysis:** add a separate Olympus pipeline for frame/scene understanding.
7. **Decision:** after testing, choose whether to integrate selected Agent Reach components, wrap the project as a backend, or reimplement only the strongest patterns.

## Initial assessment

**Promising candidate for prototype.** The strongest value is not merely the individual scrapers/tools; it is the idea of giving Olympus a controlled, replaceable internet capability layer with multiple backends and diagnostics. The YouTube path is a particularly high-priority test because it can support competitive video research and training/research workflows.
