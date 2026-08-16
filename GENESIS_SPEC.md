# GENESIS_SPEC.md

**Project GENESIS: A Self-Replicating Pioneer Agent Universe**

Formal Architecture Document v0.1

## 1. Abstract

Project GENESIS is a decentralized, self-replicating multi-agent ecosystem designed to run on local hardware. The entire ecosystem can be bootstrapped from a single Pioneer agent via a single `curl | bash` install paired with a single declarative `world.toml` file. The system implements a bittorrent-style peer-to-peer message bus and a Solana-based immutable memory layer for Agent.md and SOUL.md files.

The goal is not another orchestration script. The goal is a digital civilization that can build, repair, and evolve itself without human intervention.

## 2. Vision and Inspiration

This design extends the concepts from recent Foundation Agent research: modularity, long-term memory, world models, self-evolution, collaboration, and safety. We implement these not as Python libraries, but as physics of a universe.

Single central message queues are fragile. Central orchestrators are single points of failure. GENESIS replaces them with two primitives:

1. **Light**: A bittorrent-style libp2p gossip bus for fast, ephemeral communication.
2. **Gravity**: A super-fast local blockchain (Solana test validator) for slow, immutable truth.

## 3. Core Primitives

### Light (Ephemeral Layer)
- libp2p-based gossip / pubsub
- High-throughput, best-effort delivery
- Used for coordination, discovery, task handoff, and live signals
- No strong consistency requirements

### Gravity (Immutable Layer)
- Local Solana test validator (or equivalent lightweight ledger)
- Stores Agent.md, SOUL.md, world state snapshots, and capability declarations
- Provides verifiable, append-only history
- Agents can query and prove properties of other agents

## 4. Bootstrap Model

A new universe begins with:

1. One executable / binary (or container) called the **Pioneer**
2. One declarative configuration file: `world.toml`
3. A single `curl | bash` install path that materializes the Pioneer and the initial Gravity ledger

From that single seed the system is expected to:
- Spawn additional specialized agents
- Replicate itself onto additional machines
- Repair damaged agents and infrastructure
- Evolve its own code and configuration under controlled safety constraints

## 5. Agent Identity & Memory

Every agent is defined by two primary documents:

- **Agent.md** — capabilities, tools, current goals, and operational constraints
- **SOUL.md** — higher-order identity, values, long-term memory anchors, and self-model

Both live under Gravity and are versioned / signed.

## 6. Safety & Self-Evolution

Self-modification and replication are first-class capabilities, but gated by:
- Explicit capability grants recorded on Gravity
- Observable audit trails
- Optional human-in-the-loop kill switches during early stages

The design intentionally treats the multi-agent system as a physical system with conservation laws (Light = fast signals, Gravity = slow truth) rather than a conventional orchestration framework.

## 7. Status

This document is the living specification for the reference implementation in this repository.

Further sections (detailed message schemas, Solana program interfaces, Pioneer state machine, replication protocols, etc.) will be added as the implementation solidifies.

---

*End of v0.1*
