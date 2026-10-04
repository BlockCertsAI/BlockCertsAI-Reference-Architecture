---
canon_id: L01
title: Trust, Truth, Transparency — Foundational Design Objectives
domain: Foundations
version: 2.1
status: UNDER_ENGINEERING_REVIEW
sequence_semantics: documentation_order
supersedes:
  - ROOT_NARRATIVE.md (axiom portions)
  - README.md (principle portions)
  - L01 v1.0 (asserted Trust-Truth-Transparency as operational root)
  - L01 v2.0 (overclaimed downstream dependency, finality, and disambiguation scope)
depends_on: []
referenced_by:
  - L03_SVS
  - L08_PERU
  - L18_Governance_and_Constraints
  - L19_Attestations
  - L26_MAIAi
last_updated: 2026-10-04
open_questions:
  - "Precise Canon authority hierarchy (intent vs. implementation ranking, and MAIAi Gen2's standing as an authoritative architectural source) to be formalized in CANON_ACCEPTANCE_GATE."
  - "Validation/finality protocol terminology and mechanics resolved separately; deliberately absent from L01 (see L19, L25). If finality is confirmed, the Truth objective may be strengthened from 'verifiable' toward 'final'."
---

# L01 · Trust, Truth, Transparency — Foundational Design Objectives

## Purpose
This layer is the entry point to the BlockCertsAI (BCAI) canon. It states the
design objectives the architecture exists to produce, declares the evidence
posture the whole canon is held to, and names a core architectural invariant
enforced across the downstream architecture.

It is deliberately **not** the operational root. Trust, Truth, and Transparency
are what the architecture *produces* — they are not themselves the enforcement
mechanism. The mechanisms that enforce them are defined downstream (Identity,
Authentication, Vaults, Execution, Authority, Governance, Proof).

## Two Kinds of Foundation
The canon distinguishes two things that are easy to conflate. Both are true;
they are not the same.

| | Explanatory foundation | Operational foundation |
|---|---|---|
| **Question it answers** | Why does BCAI matter, and what changes for users and businesses? | What must BCAI enforce in order to function? |
| **Principle** | Ownership precedes everything (ownership-first, outside-in) | Authenticated identity plus protocol-level authority/compliance enforcement before execution |
| **Where it lives** | L01 (this layer), expressed through Trust, Truth, Transparency | The enforcement layers (Identity → Authentication → Vaults → Execution → Authority → Governance → Proof) |

Trust, Truth, and Transparency are the **design objectives** of the explanatory
foundation. The operational foundation is stated here in **mechanism-neutral**
terms and is specified — including how it is named and implemented — in the
downstream layers, not in L01.

## The Three Design Objectives

### Trust — enforced, not assumed
BCAI is an execution substrate for environments where trust cannot be assumed
and must therefore be enforced by protocol rather than by institutions,
applications, or after-the-fact remediation. The objective is that enforcement
occurs **before** execution, not after damage. *How* that enforcement works is
defined in the downstream authority, authorization, and execution layers.

### Truth — attributable and verifiable
The objective is that what the substrate records is attributable to an
authenticated origin and can be independently verified. Authenticated execution
creates attributable records whose integrity and finality characteristics are
defined in the Proof and Consensus layers (L19, L25), not asserted here. This
objective rests directly on the architectural invariant stated below.

### Transparency — includes the gaps
An architecture that cannot be read cannot be critiqued, and an architecture
that cannot be critiqued should not be trusted. This canon is published while
under engineering review **specifically so its gaps are visible** — including to
its authors. Where a boundary exists, the canon documents the boundary rather
than overstating it (see *Documented Boundaries*, below).

## The Architectural Invariant
One hard architectural claim anchors L01. It is stated here as an invariant and
enforced downstream:

> **State-transitioning execution requires an authenticated, attributable origin.**

Nothing transactional on the BlockCerts blockchain occurs until the participant
is authenticated. The mechanisms that make this true — identity binding at
genesis, authentication, authority, and validation — are defined in the Identity,
Authentication, Execution, Authority, and Proof layers. L01 states the
invariant; it does not specify the protocol that enforces it.

## Documented Boundaries
Transparency requires naming where the current architecture does not yet meet
its own objective.

- **Administrative-layer boundary.** The objective that protocol-sealed
  execution is not subject to post-hoc adjudication holds for execution the
  protocol has sealed. It does **not** yet hold for platform-level
  administrative functions (provisioning, scope configuration, deployment
  setup), which currently sit above the protocol layer and are not yet
  cryptographically constrained. This boundary is documented, not overstated.
  Work to place these functions under multi-signature / smart-contract
  governance is tracked in the delegation and governance layers.

## Evidence Posture
Every canon file carries a `status` field:

- `UNDER_ENGINEERING_REVIEW` — specified, not yet validated against the running system.
- `TRUE` — validated against the running system.

The canon distinguishes **architectural intent** from **observed
implementation**. These are not necessarily identical: running software can
contain defects, incomplete implementations, transitional behavior, or legacy
code, none of which necessarily represent intent. When intent and implementation
disagree, the canon **records the divergence** rather than collapsing one into
the other or silently preferring either. The precise authority hierarchy for
resolving such conflicts is formalized in CANON_ACCEPTANCE_GATE.

## Sequence Semantics
Canon layer numbers (L01, L02, …) represent **documentation/conceptual order
only**. They do **not** encode runtime execution sequence or technical
dependency. Runtime sequence, where it matters, is documented inside the
relevant layer (e.g., the Process-Flow Chain layer), not inferred from
numbering. This is machine-readable via the `sequence_semantics:
documentation_order` field in each file header.

## Governing Consequences
These objectives and the invariant impose constraints on every downstream layer:

| Source | Downstream obligation |
|---|---|
| Trust is enforced | No layer may rely on institutional or application-level trust as a substitute for protocol enforcement. |
| Truth is attributable | No layer may permit state-transitioning execution without an authenticated, attributable origin. |
| Transparency includes gaps | No layer may claim `TRUE` until validated against the running system; unverified claims and boundaries are marked, not hidden. |

## Not To Be Confused With
BCAI is not the MIT Media Lab "Blockcerts" credentialing standard. Blockcerts is
an open standard for issuing and verifying credentials. BlockCertsAI is the
platform and architecture documented by this canon. The two are unrelated
systems despite the similarity in name.

## Project Timeline Note
BCAI's genesis-era work dates to May 2016; May 2026 marks the ten-year
anniversary. Treated as canonical and closed.

## Open Questions
- Precise Canon authority hierarchy (intent vs. implementation; MAIAi Gen2's
  standing as an authoritative architectural source) — to be formalized in
  CANON_ACCEPTANCE_GATE.
- Validation/finality protocol terminology and mechanics — resolved separately
  (L19, L25); deliberately absent from L01. If finality is confirmed, the Truth
  objective may be strengthened from "verifiable" toward "final."
