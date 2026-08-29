# Concept

> **A unit of semantic meaning ; a distinguishable abstract idea that can participate in semantic definitions, specializations, and assertions.**

---

## Semantic Identity

```yaml
semantic_id: wsf:Concept
preferred_name: Concept
aliases: [Semantic Concept, Conceptual Entity]
status: Normative
version: 1.0.0
classification: Tier 1 (Foundational)
parent: wsf:Entity
authority: WSF
```

---

## Definition

A **Concept** is a unit of semantic meaning ; an abstract idea that can be defined, referenced, specialized, and used in semantic assertions.

A Concept is NOT:
- A specific concrete thing (use `wsf:Entity` for that);
- An event that occurs (use `wsf:Event` for that);
- A relationship between things (use `wsf:Relationship` for that);
- A property or attribute (use `wsf:Disposition` or specific properties).

A Concept IS:
- A distinguishable abstract idea;
- A candidate for definition and specification;
- The "what" that semantic assertions are about;
- A unit that can be specialized into more specific concepts.

---

## Examples

| Concept | Semantic ID | Definition |
|---|---|---|
| Capability | wsf:Capability | A grounded potential of an Entity to accomplish an effect |
| Function | wsf:Function | An intended purpose or activity |
| System | wsf:System | An organized assembly of components |
| Process | wsf:Process | A structured transformation |
| Goal | wsf:Goal | An intended outcome |
| Value | wsf:Value | Something of worth or significance |
| Role | wsf:Role | A relational position |

These are concepts. They are NOT:
- Specific things (e.g., "OTCHERE Inc" is an Entity, not a Concept);
- Specific events (e.g., "Order #12345 was placed" is an Event, not a Concept);
- Specific assertions (e.g., "OTCHERE has Order Fulfillment Capability" is an Assertion).

---

## Why Concept Is Foundational

Concept is foundational because:

1. **Semantic assertions are about concepts** : "OTCHERE possesses Capability" uses the concept Capability.
2. **Specialization operates on concepts** : Business Capability specializes Capability.
3. **Definitions describe concepts** : a definition defines what a concept means.
4. **Cross-system reference requires shared concepts** : integration requires shared concept identity.

Without Concept as a foundational type, the architecture cannot talk about meaning, only about data structures.

---

## Concept vs Entity (Critical Distinction)

| Aspect | Concept | Entity |
|---|---|---|
| **Nature** | Abstract idea | Concrete (or concretely-modeled) thing |
| **Examples** | Capability, Function, Role | OTCHERE Inc, Kwesi, Order #12345 |
| **Identity** | Identified by meaning | Identified by stable identity |
| **Participates in** | Definitions, specializations | Assertions |
| **Specializes** | Through specialization | Through classification (instance-of) |
| **Lives in** | Semantic foundation | Modeled world |

```
Concept ──instance-of──► Entity
   ↑                        │
   │                        │
   └── instance-of          │
        │                   │
        ▼                   │
   Entity ◄─────────────────┘
```

Both can have semantic identities. Both can be specialized. But they are fundamentally different categories of semantic artifact.

---

## Concept Structure

A Concept MAY have:

- **Identity**: Stable semantic identity (per ADR-WSF-18)
- **Definition**: Human-readable definition
- **Specification**: Formal semantic specification (per ADR-WSF-20)
- **Constraints**: What is/isn't included
- **Relationships**: How it relates to other concepts
- **Specializations**: More specific concepts
- **Examples**: Reference instances or applications
- **Status**: Governance status (per Semantic Status Model)
- **Version**: Semantic version (per ADR-WSF-16)

A Concept SHALL NOT be:

- A synonym for "any data structure"
- A synonym for "any database record"
- A synonym for "any named thing"
- Reducible to its representation

---

## Concept Categories

WSF distinguishes these categories of Concept (per INV-R13 and ADR-WSF-09):

1. **Foundational Concepts**: Core semantic primitives (Entity, Concept, Relationship, Event, State, Disposition, Proposition, Assertion, Identity, Context, Time, Space)
2. **Domain Concepts**: Concepts emerging from foundational composition (Capability, Function, System, Resource, Service, Process, Information, Data, Outcome, Value, Goal, Requirement, Metric, Workflow, Rule, Policy, Scenario)
3. **Mechanism Concepts**: How things happen (Commitment, Obligation, Authorization, Condition, Decision, Action, Observation, Measurement, Validity)
4. **Governance Concepts**: Authority, Provenance, Trust, Evidence

Each category has its own architectural role.

---

## Concept Specialization

Concepts are specialized through:

```
Parent Concept
   ↓
   specializes
   ↓
Child Concept (more specific)
```

Specialization MUST:
- Identify the parent concept;
- Preserve inherited meaning;
- Add additional constraints;
- Remain semantically conformant (per ADR-WSF-04).

Example:
```
wsf:Capability (parent)
   ↓ specializes
wsf:BusinessCapability (child — OpenDEA specialization)
```

---

## Concept Lifecycle

Per Semantic Status Model:

```
Candidate → Investigating → Proposed → Normative → Deprecated → Retired
```

A Concept MAY move from any state to Retired but MUST maintain its identity through evolution (per ADR-WSF-16).

---

## Assertion Pattern

Concepts participate in semantic assertions through this pattern:

```
Subject ──Relationship──► Object
   │            │              │
   │            │              └─ The Concept being asserted about
   │            └─ The Concept describing the relationship
   └─ The Entity asserting the relationship with
```

Example:
```
OTCHERE Inc ──possesses──► Order Fulfillment Capability
   (Entity)      (Relationship)  (Concept)
```

The relationship and object are **Concepts**, not specific entities. This is what allows the assertion to be semantically general.

---

## Related Concepts

- [Entity](./entity.md) : Concrete things that participate in assertions
- [Relationship](./relationship.md) : How concepts connect
- [Identity](./identity.md) : Stable identification
- [Capability](./capability.md) : Example of a Tier 3 concept
- [Disposition](./disposition.md) : Concepts of tendency/potential

---

## Related ADRs

- ADR-WSF-18 : Concept Identity (this concept has a stable identity)
- ADR-WSF-09 : Foundational Concept Taxonomy
- ADR-WSF-11 : Semantic Concept Specification
- ADR-WSF-12 : Semantic Assertion Model

---

## Cross-Repository References

- Canonical semantic asset: [wsf/concepts/concept.md](https://github.com/World-Semantic-Foundation/wsf/blob/main/concepts/concept.md)
- ADR-WSF-18: [wsf-governance/ADR/ADR-WSF-18-Concept-Identity.md](https://github.com/World-Semantic-Foundation/wsf-governance/blob/main/ADR/ADR-WSF-18-Concept-Identity.md)
