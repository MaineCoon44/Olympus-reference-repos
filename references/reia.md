# Reia

- **Upstream:** https://github.com/Quaint-Studios/Reia
- **Website:** https://www.playreia.com
- **License:** AGPL-3.0
- **Engine / Stack:** Godot 4 + GDScript with Rust-backed systems
- **Category:** Open-source action-adventure RPG / MMO foundation
- **Status:** Lead foundation candidate for Operation Nimbus / Cloud Fortress

## Why it matters for Nimbus

Reia is unusually close to the planned Nimbus architecture. Its documented design includes player-owned floating islands, island customization and governance, trainable NPCs, persistent economy/marketplace systems, procedural open-world areas, raids, PvP zones, offline play, online MMO play, private servers, mod support, and regional day/night behavior.

This makes Reia a strong candidate to study as the primary Godot foundation instead of starting Nimbus from an empty project.

## High-value systems to study

- Godot 4 MMO project structure
- Offline / online / private-server separation
- Player-owned floating islands
- Island customization and governance
- Trainable NPC architecture
- Procedural world generation
- Economy and marketplace systems
- Raid and PvP architecture
- Modding model
- Persistent character/world state
- Integration points with Sustenet

## Nimbus adaptation ideas

Potential mapping from Reia concepts into Nimbus:

- Player-owned floating islands -> player bases and territory
- Realm growth/progression -> sky-region progression and world-state phases
- Trainable NPCs -> Keeper / crew systems
- Marketplace -> alliance or regional economy
- Raids -> server-wide Storm Heart / world events
- PvP zones -> beacon / contested-sky regions
- Procedural open world -> generated skies and island clusters
- Private servers / mods -> Olympus Factory and future custom worlds

## Important license note

Reia is licensed under AGPL-3.0. That is strong copyleft and must be reviewed before using modified Reia code in a commercial hosted/networked product. Keep Reia-derived code clearly separated from proprietary Nimbus assets and services until the licensing architecture is reviewed.

Do not move Reia source directly into Olympus production merely because it is cataloged here.

## Initial assessment

**Strongest current game-foundation candidate for Operation Nimbus.** The architecture and design overlap are substantial enough to justify a deeper code audit. Next evaluation should separate features that already exist in working code from features that are roadmap/design intent only.
