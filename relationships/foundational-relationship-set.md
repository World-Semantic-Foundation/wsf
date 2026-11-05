# The Foundational Relationship Set

> **The initial governed vocabulary of semantic relationships per ADR-WSF-19 §12: 29 relationships across 7 categories.**

Each entry below carries the metadata required by ADR-WSF-19 §4. The machine-readable registry is maintained in [foundational-relationships.yaml](./foundational-relationships.yaml). This set SHALL be refined only through subsequent ADRs and CRs.

---

## Semantic Identity

```yaml
semantic_id: wsf-rel:<name>
preferred_name: Foundational Relationship Set
status: Baseline
version: 0.1.0
defined_by: ADR-WSF-19 (Semantic Relationship Model) §12
classification: Foundational
domain: Semantics
```

---

## Structural

| Relationship | Definition | Domain → Range | Properties |
|---|---|---|---|
| `wsf-rel:has-part` | Entity composition | Entity → Entity | Transitive, antisymmetric; inverse of is-part-of |
| `wsf-rel:is-part-of` | Entity decomposition | Entity → Entity | Transitive, antisymmetric; inverse of has-part |
| `wsf-rel:contains` | Containment | Entity/Space → Entity | Inverse of is-contained-in |
| `wsf-rel:instantiates` | Instance-of | Entity → Concept | Functional per entity |

## Semantically Significant

| Relationship | Definition | Domain → Range | Properties |
|---|---|---|---|
| `wsf-rel:possesses` | Entity possesses Capability/Property | Entity → Disposition/Capability | Dispositional |
| `wsf-rel:has-capability` | Entity has Capability | Entity → Capability | Specializes possesses |
| `wsf-rel:assumes-role` | Entity assumes Role | Entity → Role | Context-dependent |
| `wsf-rel:realizes` | Activity realizes Outcome | Activity → Outcome | Temporal qualification required |
| `wsf-rel:produces` | Activity produces Outcome | Activity/Process → Outcome | Temporal qualification required |
| `wsf-rel:enables` | X enables Y | Entity/Concept → Entity/Concept | Dispositional, specializable |
| `wsf-rel:specializes` | Concept specializes Concept | Concept → Concept | Transitive, antisymmetric |
| `wsf-rel:governs` | Authority governs Artifact | Authority → Entity/Artifact | Normative |
| `wsf-rel:asserts` | Subject asserts Assertion | Agent → Assertion | Provenance-bearing |

## Temporal

| Relationship | Definition | Domain → Range | Properties |
|---|---|---|---|
| `wsf-rel:before` | Event A before Event B | Event → Event | Transitive, asymmetric |
| `wsf-rel:after` | Event A after Event B | Event → Event | Transitive, asymmetric; inverse of before |
| `wsf-rel:during` | Event during Interval | Event → Interval | Temporal containment |
| `wsf-rel:holds-during` | State holds during Interval | State → Interval | Temporal validity |

## Causal

| Relationship | Definition | Domain → Range | Properties |
|---|---|---|---|
| `wsf-rel:causes` | X causes Y | Event/Entity → Event/State | Implies before |
| `wsf-rel:triggers` | X triggers Y | Event/Entity → Event/Process | Implies before |
| `wsf-rel:contributes-to` | X contributes to Y | Event/Entity → Outcome | Non-deterministic |

## Normative

| Relationship | Definition | Domain → Range | Properties |
|---|---|---|---|
| `wsf-rel:obligates` | Agreement obligates Party | Policy/Agreement → Party | Normative force |
| `wsf-rel:authorizes` | Authority authorizes Action | Authority → Action | Normative force |
| `wsf-rel:permits` | Permit allows Action | Policy/Rule → Action | Normative force |
| `wsf-rel:prohibits` | Prohibition disallows Action | Policy/Rule → Action | Normative force |

## Provenance

| Relationship | Definition | Domain → Range | Properties |
|---|---|---|---|
| `wsf-rel:asserted-by` | Assertion asserted by Agent | Assertion → Agent | Functional |
| `wsf-rel:derived-from` | Assertion derived from Source | Assertion → Assertion/Source | Transitive (derivation chain) |
| `wsf-rel:supported-by` | Assertion supported by Evidence | Assertion → Evidence | Cardinality 1:N |

## Identity

| Relationship | Definition | Domain → Range | Properties |
|---|---|---|---|
| `wsf-rel:same-as` | X is identical to Y | Entity/Concept → Entity/Concept | Symmetric, transitive |
| `wsf-rel:supersedes` | X supersedes Y | Entity/Concept → Entity/Concept | Transitive, antisymmetric |

---

## Canonical Example

```yaml
- assertion:
    subject: wsf-ex:OTCHERE-Inc
    relationship: wsf-rel:possesses
    object: wsf-ex:OrderManagementCapability
    context: wsf-ctx:enterprise-architecture
    time: { from: 2026-01-01, to: null }
    provenance:
      asserted_by: wsf-ex:Kwesi
      asserted_at: 2026-08-29
```

---

## Validation

Every use of a foundational relationship SHALL satisfy the six validation checks of ADR-WSF-19 §13 (domain, range, cardinality, mathematical properties, context, identity).

---

## Cross-References

- [Forms of Relation](./forms-of-relation.md)
- [Relationship Families](./relationship-families.md)
- [Machine-Readable Registry](./foundational-relationships.yaml)
- ADR-WSF-19 (Semantic Relationship Model)

---

*Status: Baseline. Additions require an ADR and CR.*
