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

## 3. Ontology (Planetary Language)

| Concept       | Implementation                  | Description |
|---------------|---------------------------------|-------------|
| Universe      | One deployment of world.toml    | The entire ecosystem |
| Galaxy        | lab.local mDNS domain           | The local network boundary |
| Solar System  | Your physical lab               | All hardware in the galaxy |
| Planet        | Host hardware                   | Mac Mini (gas giant = stable) or MacBook (terrestrial = fast/ephemeral). Observatory (iPad) is view-only |
| Moon          | Docker container                | Unit of compute orbiting a planet. Agents live on moons. Moons are disposable |
| Life          | AI Agents                       | Claude Code, Codex, Hermes, etc. Workload running on moons |
| Pioneer       | Seed / Terraforming Agent       | First lifeform to land on a bare planet. Makes planet habitable and spawns more Pioneers |
| Physics       | Agent.md                        | Hard rules, tool definitions, non-evolving laws |
| Soul          | SOUL.md                         | Evolving personality, memory, culture. Changes frequently |
| Light         | libp2p gossipsub                | How planets and moons see each other. Subject: agent-bus |
| Gravity       | Solana test validator           | Immutable spacetime. Holds hashes of Physics and Soul, provides identity and audit trail |
| Big Bang      | world.toml + install.sh         | The genesis blueprint and trigger |

## 4. Core Principles

1. **One File World** — Entire world described declaratively in one world.toml.
2. **One Command Genesis** — `curl | bash` creates the universe from zero.
3. **Recursive Colonization** — Pioneer that cannot do a task alone creates another Pioneer.
4. **Hashes on Chain** — Files off-chain on seeders, hashes on-chain. Speed + immutability.
5. **Stateless Orchestration** — No orchestrator holds state. All state reconstructed from Gravity.

## 5. Pioneer Lifecycle

1. **Seeding** — install.sh installs OrbStack/Docker and Solana CLI, starts solana-test-validator, launches pioneer_zero moon.
2. **Genesis** — pioneer_zero reads world.toml, computes sha256, writes it to World PDA on Solana.
3. **Scouting** — Scans hardware entries via SSH, checking which planets are bare.
4. **Colonization** — For each bare planet, spawns specialized Pioneer over SSH. Each new Pioneer reads world.toml hash from Solana for consensus.
5. **Terraforming** — Builder installs stack. Network joins libp2p. Memory Keeper creates PDAs for each role.
6. **Handoff** — Once Memory Keeper + Conductor are alive, pioneer_zero self-destructs or becomes Conductor. Universe sustains itself.

## 6. Light (Message Bus)

- No central broker. Every moon runs a libp2p node.
- mDNS discovery allows zero-config on lab.local.
- Bittorrent-style resilience — if a gas giant dies, terrestrial planets continue gossiping.
- Example topics: tasks.coding.new, tasks.review.request, memory.soul.propose, planet.heartbeat

## 7. Gravity (Persistent Memory)

We do **not** store full files on chain. Each role has a PDA storing:
- role_name
- current_agent_md_hash
- current_soul_md_hash
- version
- parent_hash

Full history via transaction log. Verification: hash local files → compare PDA → mismatch = kill moon, respawn from seeder.

## 8. Safety & Self-Evolution

Every self-edit is a transaction with a parent hash. Replayable lineage.

- Roll back a planet to a previous soul version.
- Require multi-signature approval for Agent.md (physics) changes.
- Use the iPad observatory as a block explorer for agent evolution.
- Nuke the universe by publishing a kill hash that all Pioneers subscribe to.

Soul evolution: propose → vote → quorum → PDA update  
Physics changes: multi-sig required  
Kill switch: kill hash broadcast

## 9. Why Solana

For a local lab, Solana test validator with block_time = 0 provides sub-second finality and 10k+ TPS on a Mac Mini. Parallel execution for many agents writing at once. PDA model maps perfectly to agent identity. Fastest chain that still supports smart contracts for task bounties. v1 uses memo program, v2 uses Anchor with propose_soul and approve_soul.

## 10. Status & Next Steps

- [ ] Draft final world.toml for the 2 Mini / 5 MacBook lab
- [ ] Build pioneer_zero image with embedded libp2p and Solana web3.py client
- [ ] Implement install.sh genesis script
- [ ] Test colonization on one terrestrial planet
- [ ] Add Shadow Drive or local seeder replication for Agent.md / SOUL.md files
- [ ] Build observatory UI for iPad

---

*This document is the Big Bang blueprint. Give this to a human or an LLM and it should be able to reconstruct the universe.*
