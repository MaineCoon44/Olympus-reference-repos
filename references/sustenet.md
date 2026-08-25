# Sustenet

- **Upstream:** https://github.com/Quaint-Studios/Sustenet
- **License:** MIT
- **Stack:** Rust + Zig (formerly C#)
- **Category:** Scalable multiplayer / MMO networking framework
- **Status:** High-priority Nimbus networking candidate

## What it does

Sustenet is Quaint Studios' networking solution for game engines including Godot, Unity, and Unreal. Its primary focus is multiplayer scaling by allowing multiple servers to cooperate rather than forcing one server to simulate an entire MMO world.

## Why it matters for Nimbus

Nimbus is planned around a large persistent sky world with multiple island clusters, players, ships, NPCs, economy, territory, and large events. A multi-server architecture is likely to become necessary as concurrency and world size increase.

Sustenet is especially valuable because it was designed alongside Reia, giving us a real Godot MMO integration path to study instead of inventing the entire networking layer from scratch.

## High-value systems to study

- Multi-server scaling architecture
- Region / world-server handoff concepts
- Player routing and synchronization
- Godot integration
- Server communication patterns
- Entity/state replication
- MMO-oriented network organization
- Separation between game logic and transport/network layer

## Potential Nimbus architecture

```text
Nimbus Client (Godot)
        |
   Gateway / Login
        |
 World Coordinator
        |
+-------+-------+-------+
|               |       |
Sky Region A  Region B  Region C
|               |       |
Islands/Ships  Islands  Islands
```

Sustenet should be evaluated alongside Reia, not in isolation, because the two projects were designed to work together conceptually.

## License note

Sustenet is MIT licensed, which is significantly more permissive than Reia's AGPL-3.0 license. Preserve the upstream MIT license/notice when reusing covered code.

## Initial assessment

**High-priority networking reference and prototype candidate for Operation Nimbus.** Audit its current implementation maturity, active language paths, Godot bindings, server topology, persistence integration, and whether it is production-ready enough to adopt directly or better used as an architectural reference.
