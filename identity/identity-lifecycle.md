# The Identity Lifecycle

> **How identities are assigned, stabilised, persisted through evolution, deprecated, and retired.**

Per ADR-WSF-18 (Concept Identity) §5-6 and ADR-WSF-16 (versioning relationship).

---

## Semantic Identity

```yaml
semantic_id: wsf:IdentityLifecycle
preferred_name: Identity Lifecycle
status: Baseline
version: 0.1.0
defined_by: ADR-WSF-18 (Concept Identity)
classification: Foundational
domain: Identity
```

---

## Lifecycle Stages

```
1. Concept Candidate Identified
       ↓
2. Identity Assigned (provisional)
       ↓
3. Semantic Specification Drafted
       ↓
4. Identity Stabilized (upon Proposed status)
       ↓
5. Identity Normative (upon Accepted ADR)
       ↓
6a. Identity Persists (through compatible evolution)
6b. Identity Replaced (semantic breaking change)
6c. Identity Deprecated (no longer recommended)
6d. Identity Retired (preserved for historical reference)
```

---

## Identity Persistence Through Evolution

Identity persists when changes are compatible:

- Clarifying the definition without changing meaning;
- Adding relationships, constraints, or examples;
- Adding optional metadata;
- Version increments that preserve the semantic contract.

Identity is replaced when the change is a semantic breaking change:

- Redefinition that changes what the concept denotes;
- Removal of required components;
- Change of parent that alters inheritance semantics.

On replacement, the new identity records `supersedes` pointing to the replaced identity; the replaced identity records `superseded_by`. Both retain full provenance.

### Canonical Example

```
wsf:Network (ADR-WSF-37)
   status: Deprecated (2026-09-28)
   superseded_by: ES-side canonical (ES-031/ES-032)
   rationale: Network moved to ES-side canonical per user-authoritative model
```

---

## Identity Collision Resolution

Per ADR-WSF-18 §14:

1. Detect collision (two identities claiming overlapping semantics);
2. Compare semantic specifications;
3. Prefer the identity governed by the higher authority in the Semantic Authority Chain;
4. Record the decision in a CR;
5. The losing identity is Deprecated with a `same-as` or `supersedes` link as appropriate.

---

## Status : Lifecycle Mapping

| Semantic Status | Identity State |
|---|---|
| Candidate | Provisional identity assigned |
| Investigating | Identity stable, semantics under investigation |
| Proposed | Identity stabilized |
| Normative | Identity normative; persists through compatible evolution |
| Deprecated | Identity retained; successor recorded |
| Retired | Identity preserved for historical reference only |

---

## Cross-References

- [Identity Model](./identity-model.md)
- [Identifier Scheme](./identifier-scheme.md)
- ADR-WSF-18, ADR-WSF-16
- Semantic Status Model (see wsf-governance/GOVERNANCE/SEMANTIC-STATUS-MODEL.md in the wsf-governance repository)
