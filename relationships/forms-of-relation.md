# The 4 Forms of Relation

> **Every semantic relationship in WSF takes one of four fundamental forms: Structural, Temporal, Causal, or Dispositional.**

Defined by ADR-WSF-19 (Semantic Relationship Model) §5. The Forms of Relation are the top-level categorisation of the relationship vocabulary. Every governed relationship belongs to exactly one Form; families and individual relationships specialise the Forms.

---

## Semantic Identity

```yaml
semantic_id: wsf-rel-form:Structural | wsf-rel-form:Temporal | wsf-rel-form:Causal | wsf-rel-form:Dispositional
preferred_name: Forms of Relation
status: Baseline
version: 0.1.0
defined_by: ADR-WSF-19 (Semantic Relationship Model)
classification: Foundational
domain: Semantics
```

---

## The Four Forms

### 1. Structural Form

Connects entities to entities, and entities to concepts. Answers: what is composed of, contained in, classified as, or part of what?

- Composition and decomposition: `wsf-rel:has-part`, `wsf-rel:is-part-of`
- Containment: `wsf-rel:contains`
- Classification: `wsf-rel:instantiates`
- Specialization: `wsf-rel:specializes`

**Canonical example**: OTCHERE Inc `has-part` Order Management Department; OTCHERE DC-01 `instantiates` the Data Center concept.

### 2. Temporal Form

Connects events, states, and intervals in time. Answers: what happened before, after, or during what?

- Order: `wsf-rel:before`, `wsf-rel:after`
- Containment in time: `wsf-rel:during`
- State holding: `wsf-rel:holds-during`

**Canonical example**: the Order Received event `before` the Order Fulfilled event; the Operational state of OTCHERE DC-01 `holds-during` the 2026 fiscal year.

**Critical distinction**: Precedence is not Causality. A before B does not imply A caused B. Temporal Form relations carry no causal commitment.

### 3. Causal Form

Connects causes and effects. Answers: what brings about, triggers, or contributes to what?

- Production: `wsf-rel:causes`, `wsf-rel:triggers`, `wsf-rel:contributes-to`
- Enablement (as causal potential): `wsf-rel:enables`
- Prevention: `wsf-rel:prevents`

**Canonical example**: the Data Center Cooling Failure event `causes` the Service Disruption event.

### 4. Dispositional Form

Connects entities to their potentials, capabilities, roles, and properties. Answers: what can, tends to, or is disposed to do what?

- Possession: `wsf-rel:possesses`, `wsf-rel:has-capability`
- Role assumption: `wsf-rel:assumes-role`
- Realization: `wsf-rel:realizes`, `wsf-rel:produces`
- Governance: `wsf-rel:governs`, `wsf-rel:asserts`

**Canonical example**: OTCHERE Inc `possesses` the Order Management Capability; Kwesi `assumes-role` Enterprise Architect.

---

## Form Properties

| Form | Connects | Transitive (typically) | Causal commitment | Temporal commitment |
|---|---|---|---|---|
| **Structural** | Entity : Entity/Concept | Often (has-part) | None | None |
| **Temporal** | Event/State : Event/State/Interval | Often (before) | None | Inherent |
| **Causal** | Event/Entity : Event/State/Entity | Sometimes | Inherent | Implied order |
| **Dispositional** | Entity : Disposition/Role/Concept | Rarely | Potential, not actual | None (until realized) |

---

## Composition Across Forms

Forms MAY compose in controlled ways (per ADR-WSF-19 §8):

```
OTCHERE Inc -possesses (Dispositional)→ OrderManagementCapability
OrderManagementCapability -realizes (Dispositional)→ OrderFulfilmentOutcome
OrderPlaced event -causes (Causal)→ OrderFulfilled event
OrderPlaced event -before (Temporal)→ OrderFulfilled event
```

A Causal relation implies a Temporal relation (cause precedes effect); the converse does not hold.

---

## Cross-References

- [Relationship Families](./relationship-families.md)
- [Foundational Relationship Set](./foundational-relationship-set.md)
- ADR-WSF-19 (Semantic Relationship Model)

---

*Status: Baseline. Changes occur only through the ADR/CR process.*
