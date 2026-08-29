# State

> **A condition or configuration of an Entity that persists over time, characterized by a set of properties that hold during an interval.**

---

## Semantic Identity

```yaml
semantic_id: wsf:State
preferred_name: State
aliases: [Condition, Configuration, Status]
status: Normative
version: 1.0.0
classification: Tier 1 (Foundational)
parent: wsf:Entity
authority: WSF
```

---

## Definition

A **State** is a condition or configuration of an Entity that persists over time, characterized by a set of properties that hold during an interval.

A State is NOT:
- An occurrence (use Event);
- A tendency or potential (use Disposition);
- A property alone (a property has a value; state is the configuration).

A State IS:
- A configuration of an Entity;
- Persists over an interval;
- Defined by properties that hold during that interval;
- May be changed by events.

---

## Why State Is Foundational

State is foundational because:

1. **Entities exist in states** : every persistent entity is in some state;
2. **Change is the transition between states** : without states, no change is describable;
3. **Process and workflow are sequences of states** : process = state_1 → state_2 → ... → state_n;
4. **Status reporting is state assertion** : "system is operational" is a state claim;
5. **Closed-loop systems operate on states** : observe state, decide, act, observe new state;
6. **Digital twins capture state** : the "twin" mirrors the entity's state.

Without State, the architecture cannot model persistence or change.

---

## State vs Event (Critical Distinction)

| Aspect | State | Event |
|---|---|---|
| **Nature** | Condition | Occurrence |
| **Time** | Persists | Occurs |
| **Example** | Order is Paid | Payment was received |
| **Change** | Changes when event occurs | Is the change |
| **Identity** | State of which entity | Specific occurrence |

States hold; events occur.

```
Event:  [Placed]→[Paid]→[Shipped]→[Delivered]
            ↓      ↓       ↓         ↓
State:    Pending  Paid    Shipped   Delivered
```

Events cause state transitions. States hold between events.

---

## State vs Property (Critical Distinction)

| Aspect | State | Property |
|---|---|---|
| **Nature** | Configuration of entity | Attribute of entity |
| **Time** | Has temporal validity | May or may not |
| **Example** | Order is Paid (state) | Order has amount (property) |
| **Composition** | Set of property values | Single attribute |

A state is a configuration defined by a coherent set of property values.

---

## State vs Disposition (Critical Distinction)

| Aspect | State | Disposition |
|---|---|---|
| **Nature** | Current condition | Tendency, potential |
| **Time** | Holds now | May manifest under conditions |
| **Example** | Order is Paid | Kwesi has Ability to design |
| **Realization** | Currently true | Possibly true |

A state is what currently holds; a disposition is what may manifest.

---

## State Types

WSF distinguishes several kinds of states:

### 1. Persistent States

Last indefinitely until changed.

Examples:
- Entity existence (continues until destroyed);
- Configuration settings (persist until reset).

### 2. Lifecycle States

Part of an entity's lifecycle progression.

Examples:
- Order: Pending → Paid → Shipped → Delivered
- Customer: Lead → Qualified → Active → Churned
- Document: Draft → Under Review → Approved → Published → Archived

### 3. Operational States

About operational condition.

Examples:
- System: Operational / Degraded / Down / Maintenance
- Network: Connected / Disconnected / Limited
- Service: Running / Stopped / Restarting

### 4. Status States

About current status in a process or workflow.

Examples:
- Task: Open / In Progress / Blocked / Done
- Approval: Pending / Approved / Rejected
- Verification: Unverified / Verified / Expired

### 5. Composite States

States composed of multiple sub-states.

Examples:
- Order Composite State: { Status: Paid, Payment: Confirmed, Inventory: Allocated, Shipping: Pending }
- System Composite State: { Operational: Yes, Capacity: 72%, Security: Compliant }

---

## State Structure

A State SHALL carry:

```yaml
state:
  semantic_id: wsf-ex:<state-instance>
  type: wsf-type:<state-type>
  bearer: <Entity whose state this is>
  holds_during: <time interval>
  properties:
    - property_name: <property>
      value: <value>
  sub_states:
    - <sub-state>
  entered_at: ISO timestamp
  entered_by_event: wsf-ex:<event that caused entry>
  expected_exit_event: wsf-ex:<expected exit event> (optional)
  valid_in_context: <context>
  evidence:
    - <evidence>
  provenance:
    source: <state source>
    asserted_by: <who asserted this state>
    authority: <authority>
```

---

## State Lifecycle

```
1. Initial State (entity creation)
       ↓
2. State persists during interval
       ↓
3. Event occurs (transition trigger)
       ↓
4. State changes (new state entered)
       ↓
5. New state persists
       ↓
... (cycle continues) ...
```

States are entered, persist, and are exited through events.

---

## State Transition

A state transition is the change from one state to another:

```yaml
- transition:
  from_state: wsf-type:OrderPending
  to_state: wsf-type:OrderPaid
  triggered_by_event: wsf-ex:Event-Payment-Received-12345
  occurred_at: 2026-08-29T10:15:00Z
  conditions: [payment confirmed, inventory allocated]
```

Transitions have:
- Source state;
- Target state;
- Trigger event;
- Conditions;
- Timestamp.

---

## State in Semantic Assertions

```yaml
- assertion:
  subject: wsf-ex:Order-12345
  relationship: wsf-rel:has-state
  object: wsf-type:Paid
  context: wsf-ctx:OrderProcessing
  validity:
    since: 2026-08-29T10:15:00Z
    until: 2026-08-29T14:30:00Z
  evidence:
    - Order record
    - State log
  provenance:
    source: OTCHERE Order Service
    asserted_by: OTCHERE Order Service
    authority: OTCHERE Inc Operations
```

This asserts that Order #12345 was in the Paid state from 10:15 to 14:30.

---

## State Pattern in Digital Twin

The digital twin pattern (per CR-WSF-17 Rev.1 §16) explicitly captures state:

```yaml
- entity_instance: OTCHERE DC-01
  state:
    current: Operational
    since: 2024-01-15
    power_state: Online
    capacity_utilization: 0.72
    temperature_status: Normal
```

The twin's state mirrors the entity's actual state.

---

## State Pattern in Simulation

The simulation pattern (per CR-WSF-17 Rev.1 §17) is state-transition based:

```yaml
- simulation:
  initial_state:
    order: Pending
  trace:
    - event: PaymentReceived
      new_state: Paid
    - event: ItemsShipped
      new_state: Fulfilled
  final_state:
    order: Fulfilled
```

States evolve through the simulation; transitions are caused by events.

---

## State Validity

States have temporal validity:

```yaml
- state_validity:
  state: wsf-type:Paid
  bearer: wsf-ex:Order-12345
  valid_from: 2026-08-29T10:15:00Z
  valid_until: 2026-08-29T14:30:00Z
  current: false (no longer current)
```

This enables:
- Historical state reconstruction;
- Current state determination;
- Future state prediction;
- Temporal reasoning.

---

## State Properties

A state is defined by a coherent set of properties:

```yaml
- state_properties:
  - capacity_utilization: 0.72
  - power_state: Online
  - temperature_status: Normal
  - security_status: Compliant
  - backup_status: Current
```

The set of property values defines the state. Changing any property may or may not change the state (depends on whether the state definition treats the property as part of its definition).

---

## State vs Status (Subtle Distinction)

- **State**: A coherent configuration with defined meaning.
- **Status**: A label indicating condition.

```yaml
- status: Operational  # A label
- state:                # A coherent configuration
    power_state: Online
    capacity_utilization: 0.72
    temperature_status: Normal
    ...
```

Status is often a simplification of state. States have richer semantics.

---

## State Examples

### Order State

```yaml
- state:
  type: wsf-type:OrderPaid
  bearer: wsf-ex:Order-12345
  properties:
    payment_status: Confirmed
    payment_method: Credit Card
    amount_paid: 99.99
    payment_date: 2026-08-29T10:15:00Z
  holds_during:
    from: 2026-08-29T10:15:00Z
    to: 2026-08-29T14:30:00Z
```

### System State

```yaml
- state:
  type: wsf-type:SystemOperational
  bearer: wsf-ex:OTCHERE-DC-01
  properties:
    power_state: Online
    capacity_utilization: 0.72
    temperature_status: Normal
    active_services: [CRM, ERP, DB]
  holds_during:
    from: 2024-01-15T08:00:00Z
    to: open-ended (current)
```

### Lifecycle State

```yaml
- state:
  type: wsf-type:CustomerActive
  bearer: wsf-ex:Kwesi
  properties:
    customer_since: 2020-03-15
    engagement_level: High
    lifetime_value: High
  holds_during:
    from: 2020-03-15T00:00:00Z
    to: open-ended (current)
```

---

## State Validation

States SHALL be validated for:

1. **Bearer existence**: The bearer entity exists.
2. **Property consistency**: Properties are consistent with state type.
3. **Temporal validity**: Holds_during is valid.
4. **Predecessor state**: A valid predecessor state existed.
5. **Trigger event**: The transition was triggered by a valid event.
6. **Evidence presence**: At least one evidence item.
7. **Provenance presence**: Source, asserted_by, authority recorded.

---

## State Composition (Composite States)

States may be composed of sub-states:

```yaml
- composite_state:
  type: wsf-type:OrderPaidAndBeingShipped
  bearer: wsf-ex:Order-12345
  sub_states:
    - payment_state: Paid
    - shipping_state: Pending
    - inventory_state: Allocated
  properties:
    - ...
```

Composite states combine sub-states into a unified condition.

---

## Related Concepts

- [Entity](./entity.md) : Things that have states
- [Event](./event.md) : Things that change states
- [Disposition](./disposition.md) : Tendencies that may produce states
- [Capability](./capability.md) : Dispositions affecting possible states
- [Time](./time.md) : States hold in time

---

## Related ADRs

- ADR-WSF-09 : Foundational Concept Taxonomy
- ADR-WSF-12 : Semantic Assertion Model (state assertions)
- ADR-WSF-19 : Semantic Relationship Model (state relationships)

---

## Cross-Repository References

- Canonical semantic asset: [wsf/concepts/state.md](https://github.com/World-Semantic-Foundation/wsf/blob/main/concepts/state.md)
