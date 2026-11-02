# The Concept Identity Model

> **A concept identity has four distinct components: the identity, its references, its semantic specification, and its status/version. These SHALL NOT be conflated.**

Per ADR-WSF-18 (Concept Identity) §4.

---

## Semantic Identity

```yaml
semantic_id: wsf:ConceptIdentity
preferred_name: Concept Identity Model
status: Baseline
version: 0.1.0
defined_by: ADR-WSF-18 (Concept Identity)
classification: Foundational
domain: Identity
```

---

## The Four Components

```
Concept Identity (the stable, persistent identity)
   │
   ├── References (ways to refer to the identity)
   │     ├── URI (canonical machine reference)
   │     ├── IRI (internationalized URI)
   │     ├── Namespaced Identifier (e.g., wsf:Capability)
   │     ├── CURIEs (compact URIs)
   │     └── Human-readable labels (preferred name, aliases)
   │
   ├── Semantic Specification (the meaning)
   │     ├── Definition
   │     ├── Constraints
   │     ├── Relationships
   │     ├── Scope
   │     └── Context applicability
   │
   ├── Status (governance state)
   │     ├── Candidate
   │     ├── Investigating
   │     ├── Proposed
   │     ├── Normative
   │     ├── Deprecated
   │     └── Retired
   │
   └── Version (evolution)
         ├── Semantic Version
         ├── Specification Version
         └── Representation Version
```

---

## Identity Metadata

Every Concept Identity SHALL carry the following metadata (ADR-WSF-18 §13):

```yaml
concept_identity:
  semantic_id: wsf:<concept-name>           # The stable identity
  type: Concept | Relationship | Assertion | Context | etc.
  preferred_name: Human-readable name
  aliases: [Alternative names]
  status: Candidate | Investigating | Proposed | Normative | Deprecated | Retired
  version: Semantic Version
  definition: Human-readable definition
  specification_ref: Path to semantic specification
  authority: Who governs this concept
  parent: Parent concept identity (if specialized)
  context_applicability: List of applicable contexts
  created: ISO timestamp
  last_modified: ISO timestamp
  superseded_by: New identity (if deprecated/superseded)
  provenance:
    source: Where the concept originated
    asserted_by: Who established it
    authority: Governance authority
```

---

## Identity Resolution

When two or more identities claim the same semantic space, resolution proceeds by (ADR-WSF-18 §8):

1. Compare definitions (identical semantics may indicate one identity);
2. Compare provenance (which authority governs each);
3. Prefer the identity governed by the higher authority in the Semantic Authority Chain;
4. If unresolved, raise a CR for explicit governance decision.

Identity collisions within WSF are resolved by the governance authority; collisions across federated namespaces follow ADR-WSF-21 §10 (Cross-Namespace Integration).

---

## Canonical Example

```yaml
concept_identity:
  semantic_id: wsf:Capability
  type: Concept
  preferred_name: Capability
  aliases: [Business Capability]
  status: Baseline
  version: 0.1.0
  definition: A stable, reusable potential of an entity to produce an outcome
  authority: WSF
  parent: wsf:Disposition
  provenance:
    source: wsf-examples worked example
    asserted_by: WSF
```

The identity `wsf:Capability` persists whether referred to by URI, CURIE, preferred name, or any of its representations in Turtle, OpenAPI, or Protobuf.

---

## Cross-References

- [Identifier Scheme](./identifier-scheme.md)
- [Identity Lifecycle](./identity-lifecycle.md)
- ADR-WSF-18, ADR-WSF-21
