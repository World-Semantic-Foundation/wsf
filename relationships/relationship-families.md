# The 10 Relationship Families

> **The relationship vocabulary is organised into 10 families: Identity, Possession, Participation, Realization, Enablement, Provision, Constraint, Measurement, Causality, Context.**

Derived from ADR-WSF-19 (Semantic Relationship Model) §5 and the Foundational Concept Relationships investigation. Families group relationships by the kind of semantic work they perform. Each family is realised by one or more governed relationships from the foundational set.

---

## Semantic Identity

```yaml
semantic_id: wsf-rel-family:<name>
preferred_name: Relationship Families
status: Baseline
version: 0.1.0
defined_by: ADR-WSF-19 (Semantic Relationship Model)
classification: Foundational
domain: Semantics
```

---

## The Families

### 1. Identity Family

Relationships that establish, connect, or resolve identity.

| Relationship | Domain → Range | Properties |
|---|---|---|
| `wsf-rel:same-as` | Entity/Concept → Entity/Concept | Symmetric, transitive |
| `wsf-rel:supersedes` | Entity/Concept → Entity/Concept | Transitive, antisymmetric |

**Canonical example**: the 2026 reorganised OTCHERE Inc `same-as` the 2025 OTCHERE Inc (identity persists through compatible evolution).

### 2. Possession Family

Relationships that connect entities to what they own, carry, or are endowed with.

| Relationship | Domain → Range | Properties |
|---|---|---|
| `wsf-rel:possesses` | Entity → Disposition/Capability/Property | Inverse: possessed-by |
| `wsf-rel:has-capability` | Entity → Capability | Specializes possesses |

**Canonical example**: OTCHERE Inc `possesses` the Order Management Capability.

### 3. Participation Family

Relationships that connect entities to the processes, events, and roles they take part in.

| Relationship | Domain → Range | Properties |
|---|---|---|
| `wsf-rel:assumes-role` | Entity → Role | Context-dependent |
| `wsf-rel:participates-in` | Entity → Process/Event | Context-dependent |

**Canonical example**: Kwesi `assumes-role` Enterprise Architect within OTCHERE Inc.

### 4. Realization Family

Relationships that connect potentials to their actualisation.

| Relationship | Domain → Range | Properties |
|---|---|---|
| `wsf-rel:realizes` | Activity/Entity → Outcome/Concept | Temporal qualification required |
| `wsf-rel:produces` | Activity/Process → Outcome | Temporal qualification required |
| `wsf-rel:instantiates` | Entity → Concept | Functional (per entity-concept pair) |

**Canonical example**: the Order Fulfilment Process `realizes` the Order Fulfilled Outcome.

### 5. Enablement Family

Relationships that connect enablers to the enabled.

| Relationship | Domain → Range | Properties |
|---|---|---|
| `wsf-rel:enables` | Entity/Concept → Entity/Concept/Disposition | Specializable (enables-architecturally, enables-operationally) |

**Canonical example**: the Integration Platform `enables` the Customer Onboarding Capability.

**Critical distinction**: enables is dispositional (potential), not causal (actual). X enables Y does not mean X causes Y; it means Y is possible because of X.

### 6. Provision Family

Relationships that connect providers to what they provision.

| Relationship | Domain → Range | Properties |
|---|---|---|
| `wsf-rel:provides` | Entity/Service → Service/Resource | Context-dependent |
| `wsf-rel:governs` | Authority → Entity/Artifact | Normative force |

**Canonical example**: OTCHERE Inc `provides` the Data Hosting Service to its customers.

### 7. Constraint Family

Relationships that connect normative elements to what they constrain.

| Relationship | Domain → Range | Properties |
|---|---|---|
| `wsf-rel:obligates` | Policy/Agreement → Party | Normative |
| `wsf-rel:authorizes` | Authority → Action | Normative |
| `wsf-rel:permits` | Policy/Rule → Action | Normative |
| `wsf-rel:prohibits` | Policy/Rule → Action | Normative |

**Canonical example**: the OTCHERE Data Retention Policy `obligates` OTCHERE Inc to retain customer records for seven years.

### 8. Measurement Family

Relationships that connect measures to what they measure.

| Relationship | Domain → Range | Properties |
|---|---|---|
| `wsf-rel:measures` | Measure → Entity/Process/Outcome | Functional per measure |
| `wsf-rel:has-measure` | Entity/Process → Measure | Inverse of measures |

**Canonical example**: the Order Cycle Time Measure `measures` the Order Fulfilment Process.

### 9. Causality Family

Relationships that connect causes to effects.

| Relationship | Domain → Range | Properties |
|---|---|---|
| `wsf-rel:causes` | Event/Entity → Event/State | Implies before |
| `wsf-rel:triggers` | Event/Entity → Event/Process | Implies before |
| `wsf-rel:contributes-to` | Event/Entity → Outcome | Non-deterministic |

**Canonical example**: the Cooling Failure Event `causes` the Service Disruption Event at OTCHERE DC-01.

### 10. Context Family

Relationships that connect semantic elements to their contexts of interpretation.

| Relationship | Domain → Range | Properties |
|---|---|---|
| `wsf-rel:applies-in` | Entity/Concept/Relationship → Context | Context validation required |
| `wsf-rel:holds-during` | State → Interval | Temporal |

**Canonical example**: the Operational status of OTCHERE DC-01 `holds-during` the 2026 maintenance interval.

---

## Family : Form Mapping

| Family | Primary Form |
|---|---|
| Identity | Structural |
| Possession | Dispositional |
| Participation | Dispositional |
| Realization | Dispositional |
| Enablement | Dispositional |
| Provision | Structural |
| Constraint | Dispositional (normative potential) |
| Measurement | Dispositional |
| Causality | Causal |
| Context | Temporal / Structural |

---

## Cross-References

- [Forms of Relation](./forms-of-relation.md)
- [Foundational Relationship Set](./foundational-relationship-set.md)
- ADR-WSF-19 (Semantic Relationship Model)

---

*Status: Baseline. New families require an ADR.*
