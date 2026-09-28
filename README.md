# PROD-W

**Moderated AI-Assisted Product Development Workflow**

> A protocol-first approach to evidence-governed, human-moderated AI-assisted product development.

**Status:** Early research and protocol design

---

## What is PROD-W?

PROD-W is an experimental methodology and protocol for using AI in product development while preserving human authority over consequential product decisions.

It explores how AI agents can assist with:

- product discovery
- problem definition
- market and domain research
- evidence gathering
- hypothesis formation
- counter-evidence research
- product definition
- product refinement
- positioning
- product claims
- validation planning
- transition into implementation

without allowing plausible AI-generated reasoning, repeated assumptions, or agent consensus to become substitutes for evidence.

The central concern is not simply how to make AI more productive in product development.

It is:

> **How can AI-assisted product development remain evidence-governed, challengeable, traceable, and under meaningful human authority?**

---

## Why PROD-W?

Generative AI can rapidly produce convincing product narratives:

- plausible customer problems
- plausible market opportunities
- plausible differentiation
- plausible features
- plausible competitive analysis
- plausible positioning
- plausible business cases

The danger is that one AI-generated inference can become context for the next agent, which then treats it as established knowledge.

Repeated often enough, this can create **synthetic consensus**.

PROD-W is being developed around a different principle:

> **Agent agreement is not evidence.**

Instead of optimizing for consensus, PROD-W aims to make evidence, assumptions, counter-evidence, disagreement, uncertainty, and decision authority explicit.

---

## Protocol First

PROD-W is intended to be **protocol-based rather than instruction-based**.

The normative behavior of the workflow should eventually be expressed through a machine-readable protocol defining concepts such as:

- roles
- authority
- states
- permitted actions
- transitions
- evidence requirements
- challenge requirements
- artifact contracts
- validation rules
- decision gates
- escalation
- revalidation
- provenance
- human authorization

Human-readable documentation and agent instructions may be generated from or operate against that protocol.

The goal is to avoid relying solely on natural-language instructions such as:

> "The agent should not approve its own work."

Where practical, important governance constraints should instead become enforceable protocol rules.

For example:

```text
author == reviewer
→ independent_review = invalid
```

or:

```text
PROPOSED
    ↓ independent challenge required
CHALLENGED
    ↓ Product Moderator authority required
ACCEPTED
```

The exact protocol representation and runtime architecture have **not yet been selected**.

---

## Human Authority

PROD-W assumes that consequential product judgments remain human decisions.

AI may:

- research
- propose
- challenge
- compare
- synthesize
- classify evidence
- identify uncertainty
- search for counter-evidence
- generate experiments
- analyze results

AI should not silently decide that:

- a problem is real
- evidence is sufficient
- a customer segment is validated
- a product is commercially viable
- a product should be built
- a claim is true
- a market opportunity exists
- conflicting evidence has been resolved

Those decisions require explicit authority.

PROD-W refers to the responsible human role as the **Product Moderator**.

---

## Evidence Before Confidence

PROD-W is expected to distinguish different epistemic states rather than allowing them to collapse into prose.

Candidate categories include:

- **FACT**
- **EVIDENCE**
- **INFERENCE**
- **HYPOTHESIS**
- **ASSUMPTION**
- **DECISION**

A hypothesis does not become evidence merely because several agents repeat it.

An inference does not become fact because it appears in a later artifact.

Material claims should retain provenance and, where appropriate, supporting evidence, counter-evidence, challenges, unresolved questions, and the decisions that depend on them.

---

## Divergence Is Useful

PROD-W does not assume that disagreement between agents must be resolved automatically.

A disagreement may itself be important information.

For example:

```text
Claim C-017

Product Advocate:
    supported

Product Skeptic:
    unsupported

Supporting evidence:
    [...]

Counter-evidence:
    [...]

State:
    DIVERGENT

Resolution authority:
    Product Moderator
```

`DIVERGENT` may therefore be a legitimate protocol state rather than an orchestration failure.

The objective is not to manufacture consensus.

It is to make consequential differences visible to the person responsible for deciding what happens next.

---

## Product Advocate and Product Skeptic

One area under investigation is explicit separation between constructive and adversarial product reasoning.

A **Product Advocate** may develop the strongest evidence-supported case for a proposition.

A **Product Skeptic** may independently develop the strongest evidence-supported challenge to it.

Neither role decides the outcome.

Their purpose is not debate for its own sake and not forced consensus.

Their purpose is to improve the evidence available to the Product Moderator.

---

## Product Intent Comes First

Not every product-shaped effort has the same objective.

A project may be:

- commercial
- internal
- research
- experimental
- educational
- portfolio/demonstration

PROD-W should therefore establish **product intent before evaluating product success**.

Technical feasibility, research value, commercial viability, and demonstration value are different things.

A useful research project is not necessarily a failed commercial product.

---

## Counter-Evidence

PROD-W is expected to treat counter-evidence as a first-class artifact.

Important propositions should be challenged by questions such as:

- What evidence supports this claim?
- What credible evidence contradicts it?
- What remains unknown?
- What assumption is being made?
- What observation would falsify the hypothesis?
- Has the evidence actually been independently obtained?
- Are multiple agents merely repeating the same source or assumption?

A possible starting null hypothesis for commercial product investigation is:

> **H0: This product should not be built.**

The workflow should not attempt to "prove the product is good."

It should improve the evidence available for the next human decision.

---

## Avoiding Artificial Precision

PROD-W should avoid converting uncertain product knowledge into unsupported scores such as:

```text
Product viability: 84/100
Recommendation: GO
```

A more useful representation may be:

```text
Problem existence        Supported
Problem frequency        Uncertain
Problem severity         Uncertain
Target user              Partially supported
Buyer                    Unknown
Differentiation          Hypothesis
Technical feasibility    Supported
Willingness to pay       Unknown
```

The Product Moderator can then see the actual evidence state rather than an artificial aggregate score.

---

## Product Development Is Not Strictly Linear

PROD-W is not intended to assume:

```text
Product Definition
      ↓
Implementation
      ↓
Finished Product
```

Implementation frequently produces new product knowledge.

A more realistic relationship is:

```text
PROD-W
   ⇅
MOD-W
```

Product research and definition inform implementation.

Implementation can expose:

- incorrect assumptions
- ambiguous requirements
- semantic problems
- technical constraints
- previously invisible product questions

Those discoveries may legitimately return upstream for product reconsideration.

The protocol should eventually define how such changes affect downstream artifacts and when revalidation is required.

---

## Relationship to MOD-W

PROD-W grew partly from experience developing and using **MOD-W**, the Moderated AI-Assisted Development Workflow.

MOD-W focuses primarily on governing AI-assisted software development:

- implementation
- technical review
- independent verification
- evidence
- quality gates
- human moderation

PROD-W explores the corresponding problems earlier in the lifecycle:

- What should be built?
- Why?
- What evidence supports the problem?
- Which claims are assumptions?
- What contradicts them?
- What remains unknown?
- What product decisions are justified by the available evidence?

The two projects are related but should remain distinct.

PROD-W determines and continuously challenges **product intent and product knowledge**.

MOD-W governs **software realization and verification**.

---

## Relationship to CAV

Some of the thinking behind PROD-W has also been influenced by work on **Continuous Alignment Verification (CAV)**.

One useful shared principle is:

> **Surface consequential differences rather than prematurely resolving them.**

In CAV, this applies to divergence in observed system behavior.

In PROD-W, similar thinking may apply to divergence between:

- claims and evidence
- supporting and contradictory evidence
- assumptions and observations
- Advocate and Skeptic interpretations
- product intent and implementation evidence

PROD-W is not an implementation of CAV, but the concept of preserving and surfacing meaningful divergence is relevant to its design.

---

## Protocol, Schema, and State

PROD-W currently distinguishes three related concerns:

### Protocol

Defines:

> **What is allowed to happen?**

Examples:

- who may perform an action
- which transitions are permitted
- what evidence is required
- who may authorize progression
- when independent challenge is mandatory

### Schema

Defines:

> **What does valid structured information look like?**

Examples:

- required fields in a Claim
- allowed Evidence types
- required properties of a Review
- valid state names

### State

Defines:

> **Where is a particular artifact or investigation now?**

For example:

```text
Claim C-017
state = CHALLENGED
```

The eventual architecture will likely use all three.

---

## Research: Protocol State in Document Metadata

One research direction is whether structured document metadata could carry some PROD-W protocol information alongside human-readable artifacts.

For example, an artifact might eventually contain metadata describing:

- artifact type
- protocol version
- lifecycle state
- creator role
- dependencies
- provenance
- required review
- evidence references
- authorization status

This could allow protocol state to travel with the artifact while remaining visible to Git and machine validation.

However:

> **This is currently a research idea, not a PROD-W architectural decision.**

PROD-W has not committed to:

- document metadata as authoritative protocol state
- YAML front matter
- JSON sidecar files
- a central state store
- a database-backed runtime
- any specific protocol serialization

These alternatives will be evaluated during protocol design.

---

## Current Research Questions

Early PROD-W work is expected to investigate questions such as:

1. What are the minimum protocol invariants?
2. Which decisions must remain under human authority?
3. What constitutes independent evidence?
4. How should claims and evidence retain provenance?
5. How should counter-evidence be represented?
6. When must an independent challenge occur?
7. How should unresolved disagreement be represented?
8. How should upstream changes invalidate or trigger revalidation of downstream work?
9. How should product intent affect evaluation?
10. How can the protocol prevent agent self-approval?
11. How should PROD-W interact with implementation workflows such as MOD-W?
12. Which protocol state should live with artifacts and which should be centralized?
13. Which parts of the protocol can be mechanically enforced?
14. How should human-readable views be generated from protocol state?
15. What existing workflow and agent protocols can PROD-W reuse rather than reinvent?

---

## Early Protocol Invariants

Candidate invariants currently include:

1. **Human authority must be explicit.**
2. **No agent may approve its own work.**
3. **Product intent precedes product evaluation.**
4. **Evidence and inference are distinct.**
5. **Material claims require provenance.**
6. **Material hypotheses require counter-evidence or independent challenge.**
7. **Agent agreement is not independent evidence.**
8. **Unresolved disagreement must remain visible.**
9. **Absence of discovered competition is not evidence of novelty.**
10. **Technical feasibility does not establish commercial viability.**
11. **Implementation evidence may cause product assumptions to be revisited.**
12. **Marketing claims must remain traceable to evidence.**
13. **Uncertainty should not be hidden behind artificial precision.**
14. **Consequential decisions require explicitly authorized human judgment.**

These are research candidates, not yet a stable PROD-W specification.

---

## Current Status

PROD-W is currently in **early research and protocol-definition work**.

There is not yet:

- a stable protocol
- a normative schema
- a runtime
- a CLI
- an agent implementation
- a finalized role model
- a fixed artifact model
- a conformance specification

The repository will initially be used to investigate the protocol and document the reasoning that leads to those decisions.

---

## Non-Goals

At this stage, PROD-W is not intended to be:

- an autonomous product manager
- an AI product-idea generator
- a system that automatically decides whether products should be built
- a product viability scoring engine
- a forced-consensus multi-agent framework
- a replacement for human customer research
- a generic agent orchestration framework
- a marketing-content generator
- a replacement for MOD-W

---

## Design Principle

The current design direction can be summarized as:

> **Don't use automation to hide uncertainty or manufacture consensus. Surface consequential differences, preserve the evidence, and leave consequential judgment with the human who has the authority and context to make it.**

---

## License

PROD-W is licensed under the MIT License. See [LICENSE](LICENSE).

---

**PROD-W is experimental and under active design. Terminology, protocol structure, roles, and architecture are expected to change substantially during the research phase.**
