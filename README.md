# Project GENESIS

**A Self-Replicating Pioneer Agent Universe**

Formal Architecture Document v0.1

> The goal is not another orchestration script.  
> The goal is a digital civilization that can build, repair, and evolve itself without human intervention.

## Abstract

Project GENESIS is a decentralized, self-replicating multi-agent ecosystem designed to run on local hardware. The entire ecosystem can be bootstrapped from a single **Pioneer** agent via a single `curl | bash` install paired with a single declarative `world.toml` file. The system implements a bittorrent-style peer-to-peer message bus and a Solana-based immutable memory layer for `Agent.md` and `SOUL.md` files.

## Vision

We implement Foundation Agent concepts (modularity, long-term memory, world models, self-evolution, collaboration, safety) not as Python libraries, but as **physics of a universe**.

**Light** = libp2p gossipsub (fast, ephemeral)  
**Gravity** = Solana test validator (slow, immutable)

## Ontology

| Concept | Implementation | Description |
|---------|----------------|-------------|
| Universe | One `world.toml` deployment | The entire ecosystem |
| Galaxy | `lab.local` mDNS domain | Local network boundary |
| Solar System | Your physical lab | All hardware |
| Planet | Host (Mac Mini / MacBook) | Gas giants = stable Minis; Terrestrial = fast MacBooks; Observatory = iPad (view only) |
| Moon | Docker container | Disposable compute unit; agents live here |
| Life | AI Agents | Workload on moons |
| Pioneer | Seed / Terraforming Agent | First agent on a bare planet; spawns more |
| Physics | `Agent.md` | Hard rules & tools (non-evolving) |
| Soul | `SOUL.md` | Evolving personality & memory |
| Light | libp2p gossipsub | How everything sees each other |
| Gravity | Solana test validator | Immutable hashes of Physics + Soul |
| Big Bang | `world.toml` + `install.sh` | The trigger |

## Core Principles

1. One File World
2. One Command Genesis (`curl | bash`)
3. Recursive Colonization
4. Hashes on Chain (files off-chain, hashes on-chain)
5. Stateless Orchestration (everything reconstructed from Gravity)

## Repository Contents

- [`GENESIS_SPEC.md`](GENESIS_SPEC.md) — Full formal architecture (enriched with ontology, lifecycle, safety)
- [`world.toml`](world.toml) — Declarative lab configuration (2 gas giants + 5 terrestrials + observatory + pioneer roles)
- [`install.sh`](install.sh) — Bootstrap stub
- [`docs/`](docs/) — Pointer to the interactive React formal document
- `pioneer/`, `light/`, `gravity/` — Implementation scaffolds

## Interactive Document

The full visual / interactive version of this specification (React + Tailwind, with live ontology, copyable world.toml, lifecycle diagrams, safety cards, and Solana numbers) was provided as the React Artifact.  
It has been used to enrich every file in this repository. Open the HTML locally for the full experience.

## Quick Start (Planned)

```bash
curl -sSL https://raw.githubusercontent.com/zfifteen/genesis/main/install.sh | bash --world world.toml
```

## License

MIT

---

*This is not an agent framework. This is a universe.*
