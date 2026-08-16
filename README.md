# Project GENESIS

**A Self-Replicating Pioneer Agent Universe**

Formal Architecture Document v0.1

> The goal is not another orchestration script.  
> The goal is a digital civilization that can build, repair, and evolve itself without human intervention.

## Abstract

Project GENESIS is a decentralized, self-replicating multi-agent ecosystem designed to run on local hardware. The entire ecosystem can be bootstrapped from a single **Pioneer** agent via a single `curl | bash` install paired with a single declarative `world.toml` file. The system implements a bittorrent-style peer-to-peer message bus and a Solana-based immutable memory layer for `Agent.md` and `SOUL.md` files.

## Vision and Inspiration

This design extends the concepts from recent Foundation Agent research: modularity, long-term memory, world models, self-evolution, collaboration, and safety. We implement these not as Python libraries, but as **physics of a universe**.

Single central message queues are fragile. Central orchestrators are single points of failure. GENESIS replaces them with two primitives:

1. **Light** — A bittorrent-style libp2p gossip bus for fast, ephemeral communication.
2. **Gravity** — A super-fast local blockchain (Solana test validator) for slow, immutable truth.

## Core Design Principles

- **Bootstrap from one** — A single Pioneer agent + one `world.toml` can spawn an entire civilization.
- **No central orchestrator** — Light (libp2p) + Gravity (local Solana) replace fragile message queues and single points of failure.
- **Immutable memory** — `Agent.md` and `SOUL.md` live on a local Solana ledger.
- **Self-replication & self-repair** — Agents can create, diagnose, and heal other agents and the infrastructure itself.
- **Local-first** — Runs entirely on local hardware; no required cloud dependency.

## Repository Status

This repository is the formal architecture and reference implementation scaffold for Project GENESIS.

- `GENESIS_SPEC.md` — Full architecture specification
- `world.toml` — Example declarative world configuration
- `pioneer/` — Pioneer agent bootstrap and core logic (incoming)
- `light/` — libp2p gossip bus implementation (incoming)
- `gravity/` — Local Solana memory layer (incoming)

## Quick Start (Planned)

```bash
curl -sSL https://raw.githubusercontent.com/zfifteen/genesis/main/install.sh | bash
# then edit world.toml and run the Pioneer
```

## License

MIT (or as declared)

---

*This is not an agent framework. This is a universe.*
