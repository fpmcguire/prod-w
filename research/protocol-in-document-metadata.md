## Is there precedent to use document metadata to hold the protocol of such a project?

Yes - there is precedent, and I think there is a very interesting version of this idea for PROD-W. But I would make one distinction:

Use document metadata to carry the document's protocol identity, state, authority, dependencies, provenance, and evidence references — not to duplicate the entire protocol definition inside every document.

That pattern has strong precedents.

Jupyter notebooks, for example, have structured metadata at both notebook and cell level and explicitly allow custom namespaced metadata. The notebook format itself is schema-validated, although consumers may ignore optional metadata. Quarto uses project- and document-level YAML metadata that can be inherited across a project.

More formally, RO-Crate uses a machine-readable metadata document to describe a collection of artifacts, including their provenance, software/workflows involved, creators, relationships, and context. W3C PROV goes further and provides a model of entities, activities, agents, usage, generation, and responsibility specifically so provenance and process history can travel with digital objects.

And Common Workflow Language provides a particularly useful lesson: CWL documents contain structured metadata, but anything that actually changes execution semantics must be represented as an explicit requirement, not merely tucked away as descriptive metadata.

That last distinction is probably the one PROD-W should adopt.

What this could mean for PROD-W

Imagine that a human-readable product artifact remains something like:

---

prodw:
protocol: "prod-w/0.1"
artifact: product-hypothesis
id: PH-003
state: challenged

created_by:
role: product-advocate

authority:
transition: - product-moderator

depends_on: - RESEARCH-007 - EVIDENCE-012

requires: - skeptic-challenge - counter-evidence-search

reviews: - id: SC-004
role: product-skeptic
verdict: unresolved

provenance:
supersedes: PH-002

---

# Product Hypothesis

...

The prose remains easy for you, an AI agent, or a reviewer to read.

But the top of the document now carries a machine-readable protocol envelope.

A PROD-W runtime could inspect that metadata and know:

what kind of artifact this is;
which protocol version governs it;
its current lifecycle state;
who created it;
who has authority over its next transition;
what it depends on;
which challenge/evidence artifacts are required;
what it supersedes;
whether required independent review occurred.

That starts to become very powerful.

The protocol itself would still live elsewhere

I would not put this inside every document:

rules:
product_advocate_may_not_approve: true
moderator_required_for_acceptance: true
skeptic_review_required: true
...

That's the actual protocol and should have one normative source.

For example:

prod-w/
│
├── protocol/
│ ├── protocol.yaml
│ ├── roles.yaml
│ ├── states.yaml
│ ├── transitions.yaml
│ └── evidence.yaml
│
├── schemas/
│ ├── artifact.schema.json
│ ├── claim.schema.json
│ └── review.schema.json
│
└── product/
├── hypothesis-003.md
└── ...

Then an artifact says:

prodw:
protocol: "prod-w/0.1"
artifact: product-hypothesis
state: challenged

The validator consults the central protocol and determines whether the document is in a legal state.

So there are three different things:

PROTOCOL
What transitions and actions are legal?

SCHEMA
What must a ProductHypothesis document contain?

DOCUMENT METADATA
What artifact is THIS, what is its state,
and how does it relate to the protocol?
I think this may be better than a separate central state database

For PROD-W specifically, there is something attractive about making the protocol state travel with the artifact.

If I open hypothesis-003.md, I shouldn't have to inspect another database to determine whether it is:

draft, challenged, accepted, superseded, or revalidation-required.

Its metadata tells me.

Git then gives us version history almost for free:

commit A:
state: proposed

commit B:
state: challenged

commit C:
state: unresolved

commit D:
state: accepted

The repository itself becomes an auditable evolution of product knowledge.

And that's closely aligned with what we have been trying to achieve manually in MOD-W.

It could go considerably further

The metadata doesn't have to be limited to workflow state.

For PROD-W, I can imagine something like:

prodw:
protocol: "0.1"
artifact: claim
id: C-017

epistemic:
type: hypothesis
evidence_state: partially-supported

evidence:
supporting: - E-021 - E-028
contradicting: - E-034

challenge:
required: true
completed_by: product-skeptic
result: divergent

decision:
authority: product-moderator
status: unresolved

Now the metadata expresses something extremely important:

The disagreement is not buried in the prose. It is part of the artifact's machine-readable state.

A query could find:

all material claims where:
challenge.result == divergent
AND decision.status == unresolved

That's very much in line with the surfacing philosophy we've developed through CAV.

One caution: native document properties are different

If by "document metadata" you mean the hidden metadata fields inside Word, PDF, etc., I would not make those authoritative.

They are often:

hard to inspect;
difficult to diff in Git;
inconsistently preserved by editors;
easy for tooling to strip;
poor for code review.

I'd prefer visible structured metadata, such as YAML front matter or a structured JSON/YAML companion representation.

So:

DOCX custom properties as protocol state: probably no.

Markdown/YAML front matter as protocol state: potentially excellent.

A hybrid model may be strongest

I can imagine PROD-W eventually using:

                  PROD-W PROTOCOL
                    normative
                       │
                       ▼
               protocol/*.yaml
                       │
              validates/enforces
                       │
        ┌──────────────┼──────────────┐
        ▼              ▼              ▼

artifact A artifact B artifact C
.md .md .md
│ │ │
YAML metadata YAML metadata YAML metadata
│ │ │
└──────────────┼──────────────┘
▼
human content

The protocol is centralized.

The protocol state is distributed with the artifacts.

The schema validates their structure.

Git preserves the history.

That strikes me as a particularly natural architecture for PROD-W.

And I think this is worth investigating before we commit ourselves to a central state-machine implementation, because it could preserve one of MOD-W's biggest strengths — the repository remains understandable simply by opening it — while solving one of its biggest weaknesses: the governance semantics are no longer buried only in Markdown instructions.
