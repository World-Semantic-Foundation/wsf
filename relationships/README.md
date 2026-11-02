# WSF Relationships Module

> **The foundational semantic relationship assets of WSF: the 4 Forms of Relation, the 10 relationship families, and the governed foundational relationship set.**

Defined by ADR-WSF-19 (Semantic Relationship Model). Relationships in WSF carry semantic meaning, not merely structural connection. Every relationship has a stable identity (per ADR-WSF-18), a specified domain and range, explicit mathematical properties, and is governed through the ADR/CR process.

---

## Module Structure

```
relationships/
├── README.md                        (this file)
├── forms-of-relation.md             The 4 Forms of Relation
├── relationship-families.md         The 10 relationship families
├── foundational-relationship-set.md The governed initial relationship set (ADR-WSF-19 §12)
└── foundational-relationships.yaml  Machine-readable relationship registry
```

---

## Governing Principle

> **A relationship in WSF carries semantic meaning, not merely structural connection.**

Semantic Relationships therefore:

- Have stable identities (per ADR-WSF-18);
- Have specified domains and ranges (the kinds of entities/concepts they connect);
- Have specified semantics (what they mean, not just how they connect);
- Are governed through the ADR/CR process;
- Participate in semantic assertions in controlled ways.

---

## Relationship Structure

Every governed relationship SHALL carry the following metadata (per ADR-WSF-19 §4):

```yaml
relationship:
  semantic_id: wsf-rel:<name>          # Stable identity
  preferred_name: Human-readable name
  aliases: [Alternative names]
  status: Candidate | Investigating | Proposed | Normative | Deprecated | Retired
  version: Semantic Version
  definition: Human-readable definition
  domain: What the relationship connects from
  range: What the relationship connects to
  properties:
    symmetric: boolean
    transitive: boolean
    antisymmetric: boolean
    functional: boolean
    inverse: wsf-rel:<name>             # if applicable
  cardinality: 1:1 | 1:N | N:1 | N:M
  context_applicability: List of contexts
  specialization_of: wsf-rel:<parent>   # if applicable
  authority: WSF
  provenance:
    source: Where the relationship originated
    asserted_by: Who established it
```

---

## Relationship vs Property (Critical Distinction)

| Aspect | Relationship | Property |
|---|---|---|
| **Connects** | Two entities/concepts | One entity to a value |
| **Example** | `OTCHERE possesses Capability` | `OTCHERE has Name = "OTCHERE Inc"` |
| **Identity** | Has its own semantic identity | Is a characteristic of the entity |
| **Range** | Entity/Concept (usually) | Value (often literal) |
| **Governance** | Governed vocabulary | Governed schema |

---

## Assets

- [Forms of Relation](./forms-of-relation.md) : Structural / Temporal / Causal / Dispositional
- [Relationship Families](./relationship-families.md) : Identity, Possession, Participation, Realization, Enablement, Provision, Constraint, Measurement, Causality, Context
- [Foundational Relationship Set](./foundational-relationship-set.md) : the initial governed vocabulary per ADR-WSF-19 §12
- [Machine-Readable Registry](./foundational-relationships.yaml) : the complete registry with metadata

---

## Validation

Relationships SHALL be validated through (per ADR-WSF-19 §13):

1. **Domain validation**: Subject type matches relationship domain.
2. **Range validation**: Object type matches relationship range.
3. **Cardinality validation**: Cardinality constraints satisfied.
4. **Symmetry/Transitivity validation**: Mathematical properties hold.
5. **Context validation**: Relationship applies in the asserted context.
6. **Identity validation**: Relationship identity is known.

---

## Cross-References

- ADR-WSF-19: Semantic Relationship Model (parent decision)
- ADR-WSF-18: Concept Identity (identity model)
- ADR-WSF-22: Assertion and Provenance Model (assertion participation)
- [Relationship concept definition](../concepts/relationship.md)

---

*Changes to the relationship vocabulary occur only through the ADR/CR process.*
