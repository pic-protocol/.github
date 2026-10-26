<p align="center">
  <img src="https://raw.githubusercontent.com/pic-protocol/.github/main/profile/assets/hero.png" alt="PIC. Authority is continued, not possessed. Provenance Identity Continuity: receiver-verified authority continuity for distributed systems and AI agents. A chain of three steps, s0, s1 and s2, linked by Proof of Relationship, where each authority context is a subset of the previous one." width="860">
</p>

<p align="center">
  <a href="https://www.pic-protocol.org"><b>Website</b></a> ·
  <a href="https://www.pic-protocol.org/why-pic"><b>Why PIC</b></a> ·
  <a href="https://www.pic-protocol.org/formal-model"><b>Formal model</b></a> ·
  <a href="https://github.com/pic-protocol/pic-spec"><b>Specification</b></a> ·
  <a href="https://github.com/pic-protocol/pic-x"><b>PIC-X</b></a> ·
  <a href="https://join.slack.com/t/picprotocol/shared_invite/zt-3wpt1lro7-poD6BSrcoVbVnyzqX1oxYQ"><b>Slack</b></a>
</p>

**Provenance Identity Continuity (PIC)** is a formal model of how authority travels through distributed execution: services, workloads, tools and AI agents.
A receiving boundary accepts propagated authority only as a **verifiable, non-expansive continuation** of the execution it came from, not merely because a credential is valid and possessed.

## The problem

<p align="center">
  <img src="https://raw.githubusercontent.com/pic-protocol/.github/main/profile/assets/problem.png" alt="The question a receiving boundary has to answer: is this authority the next valid continuation of the execution it came from? With possession, an executor holding authority A for execution 1 and authority B for execution 2 can select B while serving execution 1: both are authentic and held, so every credential check passes. With continuity, the boundary requires the successor to be bounded by its predecessor and a Proof of Relationship to that execution, so authority from another lineage is rejected. Authenticity is not attribution." width="860">
</p>

An executor that serves many requests can hold several valid authorities at once.
Possession proves *who holds an artifact*, not *which execution its use continues*.
When an untrusted executor selects the wrong one, every credential check still passes: that is the confused deputy, and an AI agent holding credentials for several tasks is one wrong association away from it.
PIC moves the decision to the receiving boundary, which verifies the continuation itself instead of trusting the executor's choice.

## The model

<p align="center">
  <img src="https://raw.githubusercontent.com/pic-protocol/.github/main/profile/assets/model.png" alt="The model in three steps. Origin: a permissioned entity's intent creates the root PIC Context of Authority, the upper bound of its lineage. Hop: each advancement proves its relationship to exactly one predecessor and never expands authority, PoR(s_i, s_i+1) and C_i+1 subset of C_i. Chain: valid hops compose into a Proof of Continuity, re-checked at every receiving boundary. Preserved or attenuated, never expanded, within the protocol itself." width="860">
</p>

| Step   | What it requires                                                                                       |
| ------ | ------------------------------------------------------------------------------------------------------ |
| Origin | A root **PIC Context of Authority** (PCA), created from permissioned intent, bounds the whole lineage. |
| Hop    | A **Proof of Relationship** to exactly one predecessor, and successor authority no greater than it.    |
| Chain  | A **Proof of Continuity**: the composition of valid hops, from the origin to the current state.        |

Within the stated model, authority absent from the origin cannot appear in a valid continuation, and independent lineages cannot be accepted as one.
The problems this answers are written up one by one:

| Problem                                                                                                 | The question                                                                           |
| ------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| [The threat model](https://www.pic-protocol.org/why-pic/threat-model)                                   | What the security argument is not permitted to assume.                                 |
| [Authority propagation](https://www.pic-protocol.org/why-pic/authority-propagation)                     | How authority created at an origin travels, only narrowing, through executors.         |
| [The N+1 unknown executor](https://www.pic-protocol.org/why-pic/n-plus-1-unknown-executor-problem)      | Authority must reach a successor that does not exist yet when its predecessor acts.    |
| [The N+1 outcome on unknown facts](https://www.pic-protocol.org/why-pic/n-plus-1-outcome-unknown-facts) | The outcome may not exist when the user signs: sign the predicate, check the evidence. |
| [The N+1 invalid state](https://www.pic-protocol.org/why-pic/authority-mixing)                          | A predecessor must never be able to hand on an invalid state that validates.           |

## How the pieces relate

<p align="center">
  <img src="https://raw.githubusercontent.com/pic-protocol/.github/main/profile/assets/ecosystem.png" alt="How the pieces relate. The PIC Model, the formal theory with five dated publications and Lean, Tamarin and ProVerif proofs, is stated normatively by the PIC Specification, draft 0.2 in pic-spec. PIC Protocols, concrete wire formats, implement the Specification; none is published yet. Implementations, the pic-protocol Rust crates and PIC-X, run it; until a protocol is published, an implementation implements the Specification directly." width="860">
</p>

| Repository                                                                       | What it holds                                                                               |
| -------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [pic-spec](https://github.com/pic-protocol/pic-spec)                             | The PIC Specification: draft 0.2, five documents, in Markdown and RFC-style renderings.     |
| [pic-x](https://github.com/pic-protocol/pic-x)                                   | PIC-X, the PIC Authority Broker and Exchange Server, in Rust.                               |
| [pic-rust](https://github.com/pic-protocol/pic-rust)                             | The `pic-protocol` and `pic-continuity` crates: Profile 0.2 artifacts, Prover and Verifier. |
| [pic-protocol.github.io](https://github.com/pic-protocol/pic-protocol.github.io) | The source of [pic-protocol.org](https://www.pic-protocol.org).                             |
| [.github](https://github.com/pic-protocol/.github)                               | This profile, and the governance and contribution files shared by every repository.         |

## Research record

The PIC Model was originally developed by **Nicola Gallo**.
Its public record is five dated publications:

| Date              | Publication                                                                                                           | Reference                                                          |
| ----------------- | --------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------ |
| 1 December 2025   | *PIC Model — Provenance Identity Continuity for Distributed Execution Systems* (archived working paper)               | [10.5281/zenodo.17777421](https://doi.org/10.5281/zenodo.17777421) |
| 5 December 2025   | *Authority Propagation Models: PoP vs PoC and the Confused Deputy Problem*                                            | [10.5281/zenodo.17833000](https://doi.org/10.5281/zenodo.17833000) |
| 9 July 2026       | *Proof-of-Continuity: A Temporal Model for Authority Propagation in Distributed Systems and AI Agents*                | [arXiv:2607.08906](https://arxiv.org/abs/2607.08906)               |
| 25 September 2026 | *Beyond Proof of Possession: A Relational Theory of Authority*                                                        | [10.5281/zenodo.23102206](https://doi.org/10.5281/zenodo.23102206) |
| 2 October 2026    | *Full Provenance on the COSS Causal Axis: An Event-Level Closure of Causal Attribution and Confused-Deputy Exclusion* | [10.5281/zenodo.23102373](https://doi.org/10.5281/zenodo.23102373) |

Three proof artifacts accompany it: **Lean** proves the abstract mathematics, **Tamarin** checks stateful message-level safety, and **ProVerif** gives an independent symbolic check of the authentication core.
See the [formal model](https://www.pic-protocol.org/formal-model) for what each one proves.
A peer-reviewed paper on Authority Continuity will be presented at **IEEE NCA 2026**.

## What PIC claims, and what it does not

| PIC establishes                                                                                          | PIC does not claim                                               |
| -------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| Propagated authority is accepted only as a verified continuity advancement of the execution it came from | That an executor's subjective intent can be proven               |
| Authority is preserved or attenuated across a hop, never expanded                                        | That an executor's internal behavior or side effects are correct |
| The receiving boundary decides admissibility, not the executor                                           | That any given implementation or deployment is secure            |

Every guarantee holds under the stated [threat model](https://www.pic-protocol.org/why-pic/threat-model), within the protocol itself.
Claims about concrete protected effects also need complete causal dependencies, sound evidence for each causal edge, and complete mediation.

## Status

The PIC Specifications are **public drafts, not standards**: no standards-development organization has adopted them, and they may change between versions.
No PIC Protocol specification has been published yet.
PIC-X 0.2.3 implements the current Profile 0.2 settlement subset at the `artifact-linked` assurance level, a partial level that is not full PIC continuity.
Its [continuity design](https://github.com/pic-protocol/pic-x/blob/main/docs/continuity-design.md) lists what is implemented and what is not.

## Origin and stewardship

The PIC Specifications are published and maintained by **Nitro Agility S.r.l.** as Specification Steward.
Specification materials are licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/); code repositories carry their own license.
For origin, attribution and canonical versions, see the specification [NOTICE](https://github.com/pic-protocol/pic-spec/blob/main/NOTICE.md).
