# Entity

> **The foundational concept of existence — what exists, can be identified, and can participate in semantic assertions.**

---

## Semantic Identity

```yaml
semantic_id: wsf:Entity
preferred_name: Entity
status: Baseline
version: 0.1.0
defined_by: ADR-WSF-17 (Foundational Semantic Architecture)
classification: Foundational
domain: Existence
```

---

## Definition

An **Entity** is a distinguishable existent that can be identified and about which semantic assertions may be made.

**Entity** is not synonymous with:
- Physical object
- Database record
- Thing
- Individual

**Entity** is more general than any of these. It includes:
- Physical objects (a chair, a person)
- Organizations (OTCHERE Inc)
- Software systems (OTCHERE DC-01)
- Conceptual entities (a role, a concept)
- Events (when viewed as identifiable occurrences)
- Documents (when viewed as identifiable artifacts)

---

## Key Distinctions

| Concept | Relationship to Entity |
|---|---|
| **Entity** | This concept — what exists |
| **Concept** | A semantic category, NOT an entity |
| **Identity** | The persistent identifier of an entity |
| **Identifier** | A concrete representation of identity |
| **Event** | Something that happens, can be an entity when viewed as identifiable |
| **State** | A condition, NOT itself an entity |

---

## Canonical Example

```yaml
- entity:
    semantic_id: wsf-ex:OTCHERE-Inc
    preferred_name: OTCHERE Inc
    classification: Organization
    identity: wsf-id:OTCHERE-Inc-stable-id
    type: Organization
    state: Active
    context:
      domain: Enterprise
      jurisdiction: ...
    relationships:
      has_part: [Kwesi]
      operates: [OTCHERE-DC-01]
      possesses: [OrderManagementCapability]
    provenance:
      source: OTCHERE Inc Articles of Incorporation
      asserted_by: Architecture Team
      asserted_at: 2026-08-29
```

### KWESI (Individual)

```yaml
- entity:
    semantic_id: wsf-ex:Kwesi
    preferred_name: Kwesi
    classification: Person
    identity: wsf-id:Kwesi-stable-id
    type: Person
    role:
      - Enterprise Architect
      - Capability Owner
    relationships:
      works_for: [OTCHERE Inc]
    provenance:
      source: HR System
      asserted_by: OTCHERE Inc HR
```

---

## Relationships

### Entity participates in

- `is_identified_by` → Identity
- `has_state` → State (temporal)
- `undergoes` → Event (temporal)
- `possesses` → Disposition / Capability
- `occupies` → Role
- `participates_in` → Relationship
- `located_in` → Spatial Region

---

## Properties

- **Identity**: Stable persistent identifier
- **Type**: Classification (Organization, Person, System, Resource, etc.)
- **State**: Current condition (temporal)
- **Context**: Conditions of interpretation
- **Relationships**: Connections to other entities and concepts
- **Provenance**: Source/authority of assertions about this entity

---

## Constraints

- An Entity MUST have a stable identity (per Principle 4 — Identity Separation)
- An Entity's identity SHOULD be preserved through versioning
- An Entity's state MUST be qualified temporally
- An Entity's assertions MUST have provenance

---

## Specialization Patterns

```
WSF Entity
    │
    ├── Organization      (e.g., OTCHERE Inc)
    ├── Person            (e.g., Kwesi)
    ├── System            (e.g., OTCHERE DC-01)
    ├── Resource          (contextual role)
    ├── Service           (provision construct)
    ├── Document          (information carrier)
    ├── Event             (when viewed as identifiable occurrence)
    └── ...
```

Specialization must preserve Entity semantics (per ADR-WSF-04 — Semantic Inheritance).

---

## Canonical Distinction: Entity ≠ Concept

```
Entity:    OTCHERE Inc     (this company exists)
Concept:   Enterprise       (semantic category for classification)

Entity:    OTCHERE DC-01   (this data center exists)
Concept:   DataCenter       (semantic category)
```

An Entity is classified by a Concept. The Entity IS; the Concept CATEGORIZES.

---

## Related Concepts

- **Identity** (wsf:Identity) — Persistent identifier of an Entity
- **Concept** (wsf:Concept) — Semantic category
- **State** (wsf:State) — Current condition
- **Event** (wsf:Event) — Occurrence involving an Entity
- **Role** (wsf:Role) — Contextual participation
- **Disposition** (wsf:Disposition) — Potential of an Entity

---

## Cross-References

- ADR-WSF-17: Foundational Semantic Architecture (parent)
- Investigation 7: Existence-Occurrence (refined Entity semantics)
- Investigation 2: Semantic Representation (Entity ≠ Concept)
- Investigation 4: Ontological Classification (Entity classification)
- ADR-WSF-08: Foundational Concept Relationships
- ADR-WSF-09: Foundational Concept Taxonomy

---

*Entity is a Tier 1 foundational concept. Status: Baseline.*
