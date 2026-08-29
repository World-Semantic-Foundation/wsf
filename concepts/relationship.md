# Relationship

> **A semantic connection between two entities, concepts, or assertions that carries specific meaning, governed identity, and defined properties.**

---

## Semantic Identity

```yaml
semantic_id: wsf:Relationship
preferred_name: Relationship
aliases: [Semantic Relationship, Conceptual Relationship]
status: Normative
version: 1.0.0
classification: Tier 1 (Foundational)
parent: wsf:Concept
authority: WSF
```

---

## Definition

A **Relationship** is a semantic connection between two entities, concepts, or assertions that carries specific meaning, has a governed identity, and participates in semantic assertions.

A Relationship is NOT:
- A mere structural edge (with no semantic content);
- A database join (implementation detail);
- An anonymous graph connection;
- A property of a single entity.

A Relationship IS:
- A first-class semantic artifact;
- The element connecting Subject to Object in assertions;
- Identified by meaning (per ADR-WSF-18);
- Specified with domain and range;
- Governed through the ADR/CR process.

---

## Why Relationship Is Foundational

Relationship is foundational because:

1. **Assertions require relationships** — "OTCHERE possesses Capability" uses the possesses relationship.
2. **Semantic graphs are made of relationships** — concepts relate to each other through relationships.
3. **Specialization is a relationship** — Business Capability specializes Capability.
4. **Temporal/causal/provenance connections are relationships** — events, causes, sources.
5. **Cross-system integration requires shared relationship semantics** — relationships enable shared understanding.

Without Relationship as a foundational type, we can only model structural connections, not semantic ones.

---

## Relationship Pattern

The basic relationship pattern is:

```
Subject ──Relationship──► Object
```

Or, in semantic assertion form:

```yaml
- assertion:
  subject: <Entity or Concept>
  relationship: <Relationship identity>
  object: <Entity or Concept>
  context: <Context (optional)>
```

This is the core pattern of WSF semantic assertions (per ADR-WSF-12).

---

## Relationship Categories

WSF distinguishes seven categories of Relationships (per ADR-WSF-19):

### 1. Structural Relationships

Connect entities to entities by composition, containment, or instantiation.

Examples:
- `wsf-rel:has-part` — A has part B
- `wsf-rel:is-part-of` — A is part of B (inverse of has-part)
- `wsf-rel:contains` — A contains B
- `wsf-rel:instantiates` — A is an instance of B

### 2. Semantically Significant Relationships

Connect entities/concepts with specific semantic meaning.

Examples:
- `wsf-rel:possesses` — Entity possesses Capability
- `wsf-rel:has-capability` — Entity has Capability
- `wsf-rel:assumes-role` — Entity assumes Role
- `wsf-rel:realizes` — Activity realizes Outcome
- `wsf-rel:enables` — X enables Y
- `wsf-rel:produces` — Activity produces Outcome
- `wsf-rel:governs` — Authority governs Artifact
- `wsf-rel:specializes` — Concept specializes Concept
- `wsf-rel:asserts` — Subject asserts Assertion

### 3. Temporal Relationships

Connect events, states, and intervals in time.

Examples:
- `wsf-rel:before` — Event A before Event B
- `wsf-rel:after` — Event A after Event B
- `wsf-rel:during` — Event during Interval
- `wsf-rel:holds-during` — State holds during Interval

### 4. Causal Relationships

Connect causes and effects.

Examples:
- `wsf-rel:causes` — X causes Y
- `wsf-rel:triggers` — X triggers Y
- `wsf-rel:contributes-to` — X contributes to Y

### 5. Normative Relationships

Connect normative semantic elements (permissions, obligations, authorizations).

Examples:
- `wsf-rel:obligates` — Agreement obligates Party
- `wsf-rel:authorizes` — Authority authorizes Action
- `wsf-rel:permits` — Permit allows Action
- `wsf-rel:prohibits` — Prohibition disallows Action

### 6. Provenance Relationships

Connect semantic artifacts to their origins.

Examples:
- `wsf-rel:asserted-by` — Assertion asserted by Agent
- `wsf-rel:derived-from` — Assertion derived from Source
- `wsf-rel:supported-by` — Assertion supported by Evidence

### 7. Identity Relationships

Connect identities.

Examples:
- `wsf-rel:same-as` — X is identical to Y
- `wsf-rel:supersedes` — X supersedes Y

---

## Relationship Properties

Relationships have explicit properties (per ADR-WSF-19):

### Symmetry

A relationship is symmetric if X-R-Y implies Y-R-X.

Example: `wsf-rel:same-as` is symmetric.

### Transitivity

A relationship is transitive if X-R-Y and Y-R-Z implies X-R-Z.

Example: `wsf-rel:same-as` is transitive.

### Antisymmetry

A relationship is antisymmetric if X-R-Y and Y-R-X implies X=Y.

Example: `wsf-rel:is-parent-of` is antisymmetric.

### Functionality

A relationship is functional if each X has at most one Y.

Example: `has-biological-mother` is functional.

### Inverse

Some relationships have natural inverses.

Example: `wsf-rel:contains` is inverse of `wsf-rel:is-contained-in`.

---

## Relationship Structure

A Relationship SHALL carry:

```yaml
relationship:
  semantic_id: wsf-rel:<name>
  preferred_name: Human-readable name
  aliases: [Alternative names]
  status: governance status
  version: semantic version
  definition: Human-readable definition
  domain: What the relationship connects from
  range: What the relationship connects to
  properties:
    symmetric: boolean
    transitive: boolean
    antisymmetric: boolean
    functional: boolean
    inverse: wsf-rel:<name>
  cardinality: 1:1 | 1:N | N:1 | N:M
  constraints:
    - constraint description
  context_applicability: List of contexts
  specialization_of: wsf-rel:<parent>
  created: ISO timestamp
  last_modified: ISO timestamp
  authority: WSF
  provenance:
    source: Where the relationship originated
    asserted_by: Who established it
```

---

## Relationship Examples

### Possesses (Entity → Capability)

```yaml
- relationship: possesses
  semantic_id: wsf-rel:possesses
  domain: wsf:Entity
  range: wsf:Capability
  properties:
    symmetric: false
    transitive: false
  cardinality: N:M
  specialization_of: wsf-rel:has
```

### Specializes (Concept → Concept)

```yaml
- relationship: specializes
  semantic_id: wsf-rel:specializes
  domain: wsf:Concept
  range: wsf:Concept
  properties:
    symmetric: false
    transitive: true
    antisymmetric: true
  cardinality: N:1 (each child has one parent; parents have many children)
  specialization_of: wsf-rel:related-to
```

### Causes (Event → Event)

```yaml
- relationship: causes
  semantic_id: wsf-rel:causes
  domain: wsf:Event
  range: wsf:Event
  properties:
    symmetric: false
    transitive: true
  cardinality: N:M
```

### Asserted-By (Assertion → Agent)

```yaml
- relationship: asserted-by
  semantic_id: wsf-rel:asserted-by
  domain: wsf:Assertion
  range: wsf:Agent
  properties:
    functional: false
  cardinality: N:1 (each assertion has one asserted-by agent)
```

---

## Relationship Validation

Relationships SHALL be validated:

1. **Domain check**: Subject type matches relationship domain.
2. **Range check**: Object type matches relationship range.
3. **Cardinality check**: Cardinality constraints satisfied.
4. **Symmetry/Transitivity check**: Mathematical properties hold.
5. **Context check**: Relationship applies in asserted context.
6. **Identity check**: Relationship identity is known.
7. **Constraint check**: Any additional constraints satisfied.

Example validation:
```yaml
- validation:
  subject: wsf-ex:OTCHERE-Inc    # Entity
  relationship: wsf-rel:possesses # Entity → Capability
  object: wsf-cap:OrderFulfillment # Capability
  result: VALID
  reasoning:
    - Subject is Entity ✓
    - Object is Capability ✓
    - Domain: Entity matches ✓
    - Range: Capability matches ✓
    - Cardinality: N:M allows this ✓
```

---

## Relationship vs Property (Critical Distinction)

| Aspect | Relationship | Property |
|---|---|---|
| **Connects** | Two entities/concepts | Entity to value |
| **Example** | OTCHERE possesses Capability | OTCHERE has Name = "OTCHERE Inc" |
| **Identity** | Has own semantic identity | Is characteristic of entity |
| **Range** | Entity/Concept | Value (often literal) |
| **Governance** | Governed vocabulary | Governed schema |

Both are needed. Relationships connect to other semantic artifacts; properties connect to values.

---

## Relationship Specialization

Relationships MAY be specialized:

```
wsf-rel:has (parent)
   ↓ specializes
wsf-rel:possesses
   ↓ specializes
wsf-rel:possesses-business-capability
```

Specialization follows Concept specialization rules (per ADR-WSF-04).

---

## Relationship Composition

Relationships MAY compose to form more complex relationships:

```
A -possesses→ B
B -has-part→ C
   ↓
A -possesses (transitively)→ C
```

Composition rules are specified per relationship. Some compose; others do not.

---

## Relationship Lifecycle

Relationships follow the 6-stage Semantic Status Model (per Governance docs):

```
Candidate → Investigating → Proposed → Normative → Deprecated → Retired
```

Relationships MAY be deprecated without losing their historical meaning.

---

## Related Concepts

- [Entity](./entity.md) — Things that participate in relationships
- [Concept](./concept.md) — Abstract ideas related to each other
- [Assertion](./assertion.md) — Uses relationships (per ADR-WSF-12)
- [Identity](./identity.md) — Relationships have identity
- [Capability](./capability.md) — Example of what is possessed

---

## Related ADRs

- ADR-WSF-19 — Semantic Relationship Model (governs this concept)
- ADR-WSF-04 — Semantic Inheritance (specializes relationships)
- ADR-WSF-08 — Foundational Concept Relationships (initial relationship set)
- ADR-WSF-12 — Semantic Assertion Model (relationships in assertions)
- ADR-WSF-18 — Concept Identity (relationships have identity)

---

## Cross-Repository References

- Canonical semantic asset: [wsf/concepts/relationship.md](https://github.com/World-Semantic-Foundation/wsf/blob/main/concepts/relationship.md)
- ADR-WSF-19: [wsf-governance/ADR/ADR-WSF-19-Semantic-Relationship-Model.md](https://github.com/World-Semantic-Foundation/wsf-governance/blob/main/ADR/ADR-WSF-19-Semantic-Relationship-Model.md)
