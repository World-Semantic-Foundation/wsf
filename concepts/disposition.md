# Disposition

> **A tendency, capacity, or potential of an Entity that may manifest under certain conditions — the umbrella concept for Capacity, Ability, Capability, and similar potential-bearing concepts.**

---

## Semantic Identity

```yaml
semantic_id: wsf:Disposition
preferred_name: Disposition
aliases: [Potential, Tendency, Inclination]
status: Normative
version: 1.0.0
classification: Tier 1 (Foundational)
parent: wsf:Concept
authority: WSF
```

---

## Definition

A **Disposition** is a tendency, capacity, or potential of an Entity that may manifest under certain conditions. Disposition is the umbrella concept under which Capacity, Ability, Capability, Function, Role, and similar potential-bearing concepts are organized.

A Disposition is NOT:
- An Event (use Event for occurrences);
- A State (use State for current conditions);
- A guarantee that something will manifest;
- A physical property alone.

A Disposition IS:
- A potential that may manifest;
- Tied to an Entity (as bearer);
- Conditional on circumstances;
- The basis for actions and outcomes.

---

## Why Disposition Is Foundational

Disposition is foundational because:

1. **Potential is distinct from actual** — many semantic concepts describe potential, not just actuality;
2. **Capabilities are dispositions** — every Capability is a Disposition specialized;
3. **Abilities are dispositions** — every Ability is a Disposition;
4. **Roles are dispositions** — Roles are tendencies to act in certain ways;
5. **Functions are dispositions** — Functions are intended purposes;
6. **Action requires disposition** — agents act based on dispositions.

Without Disposition, we conflate potential with actuality and lose important distinctions.

---

## Disposition Categories

WSF distinguishes the following kinds of Disposition:

### 1. Capacity

The "how much" of potential — the extent or magnitude of something an Entity can sustain or accommodate.

Examples:
- Processing Capacity: 100,000 orders/day
- Storage Capacity: 500 TB
- Financial Capacity: $10M
- Organizational Capacity: 200 employees

Capacity answers: "How much can this Entity accommodate, sustain, or process?"

### 2. Ability

The "can do" of potential — the competence or disposition to perform.

Examples:
- Processing Ability: Can process orders
- Architectural Ability: Can design systems
- Operational Ability: Can run operations
- Strategic Ability: Can plan and adapt

Ability answers: "Can this Entity perform this kind of activity?"

### 3. Capability

The grounded combination — a potential that combines Capacity and Ability in context.

Examples:
- Order Fulfillment Capability: Has Capacity for 100,000 orders/day AND Ability to fulfill orders
- Customer Service Capability: Has Service Capacity AND Customer Handling Ability
- Digital Capability: Has Digital Infrastructure Capacity AND Digital Operational Ability

Capability answers: "What can this Entity do, in what context, with what grounded potential?"

### 4. Function

The intended purpose of an Entity.

Examples:
- A system's function: Process orders
- A role's function: Approve requests
- A process's function: Transform inputs to outputs

Function answers: "What is this Entity intended to do?"

### 5. Role

A relational position with associated behavioral expectations.

Examples:
- Enterprise Architect Role: Design and govern enterprise architecture
- Capability Owner Role: Manage a capability's evolution
- Customer Role: Receive services

Role answers: "What is this Entity's expected behavior in this context?"

### 6. Power

The potential to produce effects.

Examples:
- Authoritative Power: Make binding decisions
- Operational Power: Execute operations
- Economic Power: Influence markets

Power answers: "What effects can this Entity potentially produce?"

### 7. Liability

The potential to be affected by something.

Examples:
- Legal Liability: Can be sued
- Operational Liability: Can be affected by disruptions
- Reputational Liability: Can suffer reputation damage

Liability answers: "What can affect this Entity?"

### 8. Vulnerability

The potential to be harmed or fail.

Examples:
- Security Vulnerability: Susceptible to attack
- Operational Vulnerability: Susceptible to disruption
- Financial Vulnerability: Susceptible to loss

Vulnerability answers: "What could harm this Entity?"

---

## Disposition Structure

A Disposition SHALL carry:

```yaml
disposition:
  semantic_id: wsf-dis:<disposition-id>
  type: Capacity | Ability | Capability | Function | Role | Power | Liability | Vulnerability | Other
  bearer: <Entity that has this disposition>
  context: <Context where the disposition applies>
  grounding:
    # What grounds this disposition?
    evidence: [<evidence items>]
    tests: [<tests that confirm>]
    observation: <observed manifestation>
  manifestation:
    # How can this disposition manifest?
    conditions: [<conditions under which it manifests>]
    forms: [<forms it can take>]
    outcomes: [<potential outcomes>]
  strength:
    # How strong is this disposition?
    level: Strong | Moderate | Weak
    basis: How strength is determined
  temporal:
    exists_since: ISO timestamp
    exists_until: ISO timestamp or open-ended
  provenance:
    source: <source>
    asserted_by: <agent>
    authority: <authority>
```

---

## Disposition vs State (Critical Distinction)

| Aspect | Disposition | State |
|---|---|---|
| **Nature** | Potential | Actual |
| **Manifestation** | May manifest under conditions | Currently holds |
| **Example** | OTCHERE has Order Fulfillment Capability | OTCHERE's Order Processing is Operational |
| **Time** | Persists until realized or lost | Holds during an interval |

A disposition is the potential; a state is the current condition.

```
Disposition: Has Order Fulfillment Capability
   ↓ (when conditions met)
Event: Order #12345 Fulfilled
   ↓ (resulting)
State: Order #12345 is Fulfilled
```

---

## Disposition vs Event (Critical Distinction)

| Aspect | Disposition | Event |
|---|---|---|
| **Nature** | Potential | Occurrence |
| **Time** | Persists | Occurs at point/interval |
| **Example** | Kwesi has Architectural Ability | Kwesi Designed the System on Aug 29 |

A disposition enables events; events are manifestations of dispositions.

---

## Disposition Composition

Dispositions compose to form more specific dispositions:

```
Capacity (how much)
   + Ability (can do)
   = Capability (grounded potential)
```

This composition is central to the Capability model (per ADR-WSF-07).

---

## Disposition Specialization

Dispositions are specialized:

```
wsf:Disposition (parent)
   ↓ specializes
wsf:Capacity (child)
   ↓ specializes
wsf:ProcessingCapacity (grandchild — more specific)
```

Specialization follows Concept specialization rules.

---

## Disposition Manifestation

A disposition MAY manifest under certain conditions:

```yaml
- disposition: OTCHERE has Order Fulfillment Capability
- manifestation_conditions:
  - operational_capacity >= 50,000 orders/day
  - trained_operators >= 25
- manifestation_forms:
  - order_received_event
  - order_fulfilled_event
- potential_outcomes:
  - customer_satisfaction
  - revenue
```

The disposition is potential; manifestation is conditional on circumstances.

---

## Disposition Grounding

Dispositions are grounded in something:

- **Capacity**: Grounded in physical/logical resources.
- **Ability**: Grounded in competence/disposition.
- **Capability**: Grounded in Capacity + Ability + Context.
- **Function**: Grounded in design/intent.
- **Role**: Grounded in social/structural position.

Without grounding, dispositions are mere assertions.

---

## Disposition Strength

Dispositions have varying strengths:

```yaml
- disposition: OTCHERE has Order Fulfillment Capability
- strength:
  level: Strong
  basis: 10 years operational history, 99.5% success rate
```

Strength is determined by evidence, observation, or expert assessment.

---

## Disposition Temporal Validity

Dispositions have temporal validity:

```yaml
- disposition:
  type: Capability
  bearer: OTCHERE Inc
  exists_since: 2014-01-01
  exists_until: open-ended (current)
  historical_periods:
    - period: 2014-2016
      strength: Weak (building capability)
    - period: 2016-2026
      strength: Strong (proven capability)
```

A disposition may grow or weaken over time.

---

## Disposition in Semantic Assertions

```yaml
- assertion:
  subject: wsf-ex:OTCHERE-Inc
  relationship: wsf-rel:possesses
  object: wsf-dis:OTCHERE-OrderFulfillment-Capability
  context: wsf-ctx:enterprise
  grounding:
    capacity:
      - 100,000 orders/day
    ability:
      - 10 years operational history
    context:
      - enterprise context
  evidence:
    - 10 years operational records
    - Architecture assessment 2026
  provenance:
    source: OTCHERE Architecture Assessment 2026
    asserted_by: OTCHERE Architecture Team
    authority: OTCHERE Inc Board
  trust:
    level: High
    basis: Long operational history
```

---

## Disposition Examples

### Capability Example

```yaml
- disposition:
  type: Capability
  bearer: wsf-ex:OTCHERE-Inc
  name: Order Fulfillment Capability
  grounding:
    capacity:
      - Processing: 100,000 orders/day
    ability:
      - Operational Competence (10 years)
  context: Enterprise
  evidence:
    - Operational metrics
  strength: Strong
```

### Capacity Example

```yaml
- disposition:
  type: Capacity
  bearer: wsf-ex:OTCHERE-DC-01
  name: Storage Capacity
  grounding:
    quantity: 500 TB
    type: SSD + HDD mix
  context: IT Infrastructure
  strength: Static (defined by hardware)
```

### Ability Example

```yaml
- disposition:
  type: Ability
  bearer: wsf-ex:Kwesi
  name: Enterprise Architecture Ability
  grounding:
    competence: 15 years experience
    certifications: [TOGAF, ArchiMate]
  context: Enterprise Architecture
  evidence:
    - Past architecture designs
    - Certification records
  strength: Strong
```

### Role Example

```yaml
- disposition:
  type: Role
  bearer: wsf-ex:Kwesi
  name: Enterprise Architect Role
  context: OTCHERE Inc
  expected_behaviors:
    - Design enterprise architecture
    - Govern architectural decisions
    - Mentor architects
  since: 2020-01-01
```

### Vulnerability Example

```yaml
- disposition:
  type: Vulnerability
  bearer: wsf-ex:OTCHERE-Inc
  name: Single Point of Failure (OTCHERE DC-01)
  context: IT Infrastructure
  grounding:
    risk: 95% of operations depend on DC-01
  mitigation: DC-02 (planned but not operational)
  strength: High vulnerability
```

---

## Disposition Validation

Dispositions SHALL be validated for:

1. **Bearer existence**: The bearer entity exists.
2. **Grounding presence**: Grounding is specified.
3. **Evidence presence**: For normative dispositions, evidence is present.
4. **Strength determinability**: Strength can be assessed.
5. **Temporal validity**: Validity period is specified.
6. **Provenance**: Source, asserted_by, authority recorded.

---

## Disposition in Digital Twin Pattern

Dispositions are central to the Digital Twin pattern:

```yaml
- entity_instance: OTCHERE DC-01
  capabilities:
    - semantic_id: wsf-cap:OTCHERE-DC-01-Compute
      name: Compute
      grounding:
        capacity:
          - CPU Cores: 2048
          - Memory: 8192 GB
    - semantic_id: wsf-cap:OTCHERE-DC-01-Storage
      ...
```

The digital twin captures the entity's dispositions.

---

## Related Concepts

- [Entity](./entity.md) — Bearers of dispositions
- [Capability](./capability.md) — A specialized disposition
- [Role](./role.md) — A relational disposition (forthcoming)
- [Function](./function.md) — An intended-purpose disposition (forthcoming)
- [Capacity](./capacity.md) — The "how much" disposition
- [Ability](./ability.md) — The "can do" disposition
- [State](./state.md) — Actual condition (distinct from disposition)

---

## Related ADRs

- ADR-WSF-07 — Capacity–Ability–Capability (the original distinction)
- ADR-WSF-09 — Foundational Concept Taxonomy
- ADR-WSF-19 — Semantic Relationship Model

---

## Cross-Repository References

- Canonical semantic asset: [wsf/concepts/disposition.md](https://github.com/World-Semantic-Foundation/wsf/blob/main/concepts/disposition.md)
