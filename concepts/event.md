# Event

> **An occurrence in time — something that happens, occurs, or takes place at a specific point or interval.**

---

## Semantic Identity

```yaml
semantic_id: wsf:Event
preferred_name: Event
aliases: [Occurrence, Happening]
status: Normative
version: 1.0.0
classification: Tier 1 (Foundational)
parent: wsf:Entity
authority: WSF
```

---

## Definition

An **Event** is an occurrence in time — something that happens, occurs, or takes place at a specific point or interval. Events are the foundation for representing change, action, and happening in semantic systems.

An Event is NOT:
- A persistent entity (use Entity for things that persist);
- A tendency or potential (use Disposition);
- A state of affairs (use State);
- An activity type (use Activity — but events are specific occurrences).

An Event IS:
- Located in time;
- Specific (this particular occurrence);
- Distinguished from other events by identity;
- May change state or produce outcomes;
- May have participants (Agents, Entities).

---

## Why Event Is Foundational

Event is foundational because:

1. **Change requires events** — something happens at a time;
2. **History requires events** — past occurrences are events;
3. **Causality involves events** — causes produce effects (which are events);
4. **Actions are events** — agent actions are specific occurrences;
5. **Processes are sequences of events** — structured change;
6. **Provenance refers to events** — assertions are made at events (asserted-at).

Without Event, the architecture cannot model change, history, or occurrence.

---

## Event Types

WSF distinguishes several kinds of events:

### 1. Atomic Events

Occurrences at a point in time.

Examples:
- A specific payment is received
- A specific order is placed
- A specific message is sent

### 2. Composite Events

Events composed of multiple atomic events.

Examples:
- Order fulfillment (composed of payment, picking, shipping, delivery)
- Customer onboarding (composed of registration, verification, activation)

### 3. Instantaneous Events

Occur at a specific instant with no duration.

Examples:
- Click of a button
- Sending a message
- Recording a measurement

### 4. Interval Events

Occur over a duration.

Examples:
- A workflow execution
- A manufacturing process
- A training session

### 5. Internal Events

Occur within an entity.

Examples:
- System state change
- Heartbeat
- Decision made

### 6. External Events

Occur in the world outside entities.

Examples:
- Natural disaster
- Market change
- Customer action

### 7. Agent Events

Performed by an agent.

Examples:
- Order placed by Kwesi
- Payment made by OTCHERE Inc
- Decision made by Architecture Team

---

## Event Structure

An Event SHALL carry:

```yaml
event:
  semantic_id: wsf-ex:<event-instance>
  type: wsf-type:<event-type>
  occurred_at: ISO timestamp
  duration: ISO duration (optional, for interval events)
  participants:
    agents: [<Entities that performed or were involved>]
    entities: [<Entities affected>]
  location: <spatial location>
  context: <context of occurrence>
  changes:
    - state_change: <state changed>
      from: <previous state>
      to: <new state>
  produces:
    - <outcome produced>
  causes:
    - <cause events>
  triggered_by:
    - <triggering events>
  evidence:
    - <evidence of occurrence>
  provenance:
    source: <where the event was recorded>
    asserted_by: <who recorded it>
    authority: <authority for the record>
```

---

## Event vs State (Critical Distinction)

| Aspect | Event | State |
|---|---|---|
| **Nature** | Occurrence | Condition |
| **Time** | Specific instant or interval | Persists over time |
| **Example** | Order #12345 was placed | Order #12345 is in Paid state |
| **Change** | Happens, then is past | Exists until changed |
| **Identity** | Each event has unique identity | States can recur |

**The crucial distinction**: A state can hold for an interval; an event occurs at a point or during an interval.

```
Event:  [Placed]→[Paid]→[Shipped]→[Delivered]
            ↓      ↓       ↓         ↓
State:    Pending  Paid    Shipped   Delivered
```

Events cause state changes. States hold between events.

---

## Event vs Activity (Critical Distinction)

| Aspect | Event | Activity |
|---|---|---|
| **Nature** | Occurrence | Type of occurrence |
| **Time** | Specific | Generic |
| **Example** | Order #12345 was shipped (Aug 29) | Shipping an order (activity type) |
| **Identity** | This specific occurrence | The activity as a concept |

Events are specific occurrences. Activities are types of occurrences. An Activity is specialized through instances that are Events.

---

## Event Patterns

### Event Causation

```
Event A ──causes──► Event B
```

Events cause other events. Causal relationships form chains.

### Event Sequence

```
Event A ──before──► Event B ──before──► Event C
```

Events occur in sequences. Sequences can be linear or branching.

### Event Composition

```
Event X = Event A + Event B + Event C
```

Composite events are made of simpler events.

### Event Participation

```
Event ──has-participant──► Agent
```

Events have participants (agents, entities, systems).

---

## Event in Semantic Assertions

```yaml
- assertion:
  subject: wsf-ex:Order-12345
  relationship: wsf-rel:occurred-at
  object: wsf-time:2026-08-29T10:15:00Z
  context: <context>

- assertion:
  subject: wsf-ex:Order-12345
  relationship: wsf-rel:has-event
  object: wsf-ex:Event-Payment-Received-12345
  context: <context>

- event:
  semantic_id: wsf-ex:Event-Payment-Received-12345
  type: wsf-type:PaymentReceived
  occurred_at: 2026-08-29T10:15:00Z
  participants:
    entities: [wsf-ex:Order-12345, wsf-ex:OTCHERE-Inc]
  changes:
    - state_change: Order-12345 status
      from: Pending
      to: Paid
  evidence:
    - Payment gateway log
  provenance:
    source: OTCHERE Payment Gateway
    asserted_by: OTCHERE Payment Gateway
    authority: OTCHERE Inc IT
```

---

## Event Time

Events are located in time:

```yaml
event_time:
  occurred_at: <instant>
  # OR
  occurred_during: <interval>
  recorded_at: <instant>
  observed_at: <instant>
```

Per the Temporal investigation, events have:
- **Occurrence time**: When the event actually happened.
- **Recording time**: When the event was recorded.
- **Observation time**: When the event was observed.

These can differ (event happened before being recorded, or before being observed).

---

## Event Identity

Each event has its own identity, distinguishing it from other events:

```yaml
event:
  semantic_id: wsf-ex:Event-2026-08-29-001
  # Specific identifier for this specific occurrence
```

Even if two events have the same type (e.g., "Payment Received"), they have distinct identities if they are different occurrences.

---

## Event Lifecycle

Events follow the lifecycle:

```
Occurrence → Recording → Observation → Assertion → Validation → Historical Record
```

Each stage may have its own timestamp and provenance.

---

## Event Sources

Events may originate from:

- **System events**: Generated by systems (e.g., application logs).
- **Agent actions**: Performed by agents.
- **Observations**: Recorded by observation.
- **Inferences**: Derived from other events.
- **External sources**: Reported by external systems.

Each source has its own provenance requirements.

---

## Event Examples

### Order Placed

```yaml
event:
  semantic_id: wsf-ex:Order-12345-Placed
  type: wsf-type:OrderPlaced
  occurred_at: 2026-08-29T09:00:00Z
  duration: PT0S (instantaneous)
  participants:
    agents: [wsf-ex:Kwesi]
    entities: [wsf-ex:Order-12345]
  context: wsf-ctx:OTCHERE-CustomerPortal
  changes:
    - state_change: Order-12345 status
      from: null
      to: Pending
  produces:
    - wsf-ex:Order-12345 (new entity)
  evidence:
    - Order placement log
    - Customer portal session
  provenance:
    source: OTCHERE Order Service
    asserted_by: OTCHERE Order Service
    authority: OTCHERE Inc
```

### Payment Received

```yaml
event:
  semantic_id: wsf-ex:Payment-12345-Received
  type: wsf-type:PaymentReceived
  occurred_at: 2026-08-29T10:15:00Z
  duration: PT0S
  participants:
    entities: [wsf-ex:Order-12345, wsf-ex:OTCHERE-Inc, wsf-ex:PaymentGateway]
  context: wsf-ctx:OTCHERE-PaymentProcessing
  changes:
    - state_change: Order-12345 status
      from: Pending
      to: Paid
    - state_change: OTCHERE-Inc balance
      from: <previous>
      to: <new>
  evidence:
    - Payment gateway log
    - Bank statement
  provenance:
    source: OTCHERE Payment Gateway
    asserted_by: OTCHERE Payment Gateway
    authority: OTCHERE Inc Finance
```

### Order Shipped

```yaml
event:
  semantic_id: wsf-ex:Order-12345-Shipped
  type: wsf-type:ItemsShipped
  occurred_at: 2026-08-29T14:30:00Z
  duration: PT15M (loading time)
  participants:
    entities: [wsf-ex:Order-12345, wsf-ex:OTCHERE-Warehouse]
  context: wsf-ctx:OTCHERE-Warehouse
  changes:
    - state_change: Order-12345 status
      from: Paid
      to: Shipped
  produces:
    - wsf-ex:Shipment-TRK-2026-08-29-001
  evidence:
    - Warehouse fulfillment log
    - Shipping confirmation
    - Tracking number assignment
  provenance:
    source: OTCHERE Warehouse System
    asserted_by: OTCHERE Warehouse System
    authority: OTCHERE Inc Operations
```

---

## Event Validation

Events SHALL be validated for:

1. **Time validity**: Occurred_at is consistent with related events.
2. **Participant existence**: All referenced participants exist.
3. **Causal consistency**: Causes occurred before effects.
4. **State change validity**: State transitions are valid.
5. **Evidence presence**: At least one evidence item.
6. **Provenance presence**: Source, asserted_by, authority recorded.

---

## Event in Digital Twin Pattern

Events are central to the Digital Twin pattern (per CR-WSF-17 Rev.1 §16):

```
Entity Instance (OTCHERE DC-01)
   ├── Identity
   ├── State (current)
   ├── Events (history)
   ├── Relationships
   ├── Capabilities
   ├── Context
   ├── Time
   └── Space
```

The event history provides the operational record of the digital twin.

---

## Event in Simulation Pattern

Events drive simulation (per CR-WSF-17 Rev.1 §17):

```
Initial State → Event/Action → Transition → Resulting State → Next Event
```

Each transition is an event; each state is between events.

---

## Related Concepts

- [Entity](./entity.md) — Things that participate in events
- [State](./state.md) — Conditions held between events
- [Disposition](./disposition.md) — Tendencies that manifest in events
- [Capability](./capability.md) — Dispositions realized through events
- [Time](./time.md) — Events occur in time
- [Space](./space.md) — Events occur in space

---

## Related ADRs

- ADR-WSF-09 — Foundational Concept Taxonomy
- ADR-WSF-12 — Semantic Assertion Model (events in assertions)
- ADR-WSF-16 — Semantic Evolution & Versioning (event records)
- ADR-WSF-19 — Semantic Relationship Model (event relationships)

---

## Cross-Repository References

- Canonical semantic asset: [wsf/concepts/event.md](https://github.com/World-Semantic-Foundation/wsf/blob/main/concepts/event.md)
