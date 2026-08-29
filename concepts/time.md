# Time

> **The semantic dimension of temporal location and sequence — instants, intervals, durations, and the relationships between them.**

---

## Semantic Identity

```yaml
semantic_id: wsf:Time
preferred_name: Time
aliases: [Temporal Dimension, Temporal Semantics]
status: Normative
version: 1.0.0
classification: Tier 1 (Foundational)
parent: wsf:Entity
authority: WSF
```

---

## Definition

**Time** is the semantic dimension of temporal location and sequence — instants, intervals, durations, and the relationships between them.

Time is NOT:
- A physical quantity alone (time has semantic structure beyond measurement);
- A linear axis alone (time has semantic structure);
- A property of entities (time is a dimension entities exist within).

Time IS:
- A semantic dimension;
- Composed of instants and intervals;
- A dimension along which events occur and states hold;
- Structured by temporal relationships.

---

## Why Time Is Foundational

Time is foundational because:

1. **Events occur in time** — without time, no events;
2. **States hold over time** — without time, no persistence;
3. **Causality operates in time** — causes precede effects;
4. **Assertions have temporal validity** — assertions may be time-bounded;
5. **History requires time** — without time, no record;
6. **Process and workflow happen over time** — without time, no sequence.

Without Time, the architecture cannot model change, persistence, or history.

---

## Time Components

WSF distinguishes:

### 1. Instant

A point in time with no duration.

Example: 2026-08-29T10:15:00Z

### 2. Interval

A bounded temporal region.

Example: 2026-08-29T09:00:00Z to 2026-08-29T17:00:00Z

### 3. Duration

An amount of time, independent of specific start/end.

Example: PT8H (8 hours)

### 4. Date

A calendar date without time-of-day.

Example: 2026-08-29

### 5. Time of Day

Time of day without date.

Example: 10:15:00 UTC

---

## Time vs Temporal Dimension

Time as a concept vs Time as a dimension:

- **Time (concept)**: The semantic concept of temporal location and sequence.
- **Temporal Dimension**: The application of Time to qualify other semantic artifacts.

Both are needed. The concept provides the foundation; the dimension is the application.

---

## Time Structure

Time carries:

```yaml
- time:
  semantic_id: wsf-time:<id>
  type: Instant | Interval | Duration | Date | TimeOfDay
  
  # For Instant
  instant_value: ISO timestamp
  
  # For Interval
  start: ISO timestamp
  end: ISO timestamp or open-ended
  
  # For Duration
  duration: ISO duration
  duration_unit: seconds | minutes | hours | days | weeks | months | years
  
  # Timezone
  timezone: UTC | region | offset
  
  # Calendar
  calendar: Gregorian | Hijri | Hebrew | ...
  
  # Properties
  precision: <level of precision>
  granularity: <smallest distinguishable unit>
  
  # Reference
  reference_frame: <relative-to reference>
```

---

## Time Relationships

WSF defines the following time relationships:

| Relationship | Definition |
|---|---|
| `before` | X is before Y (X ends before Y starts) |
| `after` | X is after Y (Y is before X) |
| `during` | X occurs during Y (X within Y) |
| `contains` | Y contains X (X within Y) |
| `overlaps` | X and Y share time |
| `meets` | X ends when Y begins |
| `starts` | X starts at the same time as Y |
| `ends` | X ends at the same time as Y |
| `equals` | X is the same time as Y |

These are the standard temporal relationships (per Allen's interval algebra).

---

## Time in Semantic Assertions

Time qualifies assertions:

```yaml
- assertion:
  ...
  time:
    valid_from: 2026-08-29
    valid_until: 2026-12-31
    asserted_at: 2026-08-29T10:00:00Z
```

This means: "The assertion is valid from Aug 29 to Dec 31, 2026, and was asserted on Aug 29."

---

## Time in Events

Events occur at instants or during intervals:

```yaml
- event:
  semantic_id: wsf-event:Order-12345-Placed
  occurred_at: 2026-08-29T09:00:00Z   # Instant
  duration: PT0S                         # Instantaneous
```

Or for interval events:

```yaml
- event:
  semantic_id: wsf-event:Shipment-Process
  started_at: 2026-08-29T14:00:00Z
  ended_at: 2026-08-29T14:30:00Z
  duration: PT30M
```

---

## Time in States

States hold over intervals:

```yaml
- state:
  type: Paid
  bearer: Order-12345
  valid_from: 2026-08-29T10:15:00Z
  valid_until: 2026-08-29T14:30:00Z
```

The state held from 10:15 to 14:30 on Aug 29.

---

## Temporal Dimensions in Assertions

Per the Temporal investigation, multiple temporal dimensions apply:

| Dimension | Meaning |
|---|---|
| **Occurred-at** | When something happened |
| **Observed-at** | When something was observed |
| **Recorded-at** | When something was recorded |
| **Asserted-at** | When something was asserted |
| **Valid-from** | When something became valid |
| **Valid-until** | When something stopped being valid |

These can all differ. An event can occur before being observed before being recorded before being asserted.

---

## Time and Causality

Causality operates in time:

```
Cause Event A ──at── 2026-08-29T09:00:00Z
   ↓ causes
Effect Event B ──at── 2026-08-29T09:05:00Z
```

Causes MUST precede effects in time.

```
Sequence (precedence): A before B (no causal claim)
Causality: A causes B (A precedes B AND A is causally responsible)
```

The distinction between sequence and causality is important.

---

## Time Reference Systems

Time references various systems:

- **UTC**: Coordinated Universal Time.
- **Local time**: With timezone offset.
- **Calendar date**: Date without time.
- **Fiscal year**: Business year.
- **Academic year**: Academic calendar.
- **Custom calendars**: Hijri, Hebrew, etc.

Each has its own conventions.

---

## Time Validation

Time references SHALL be validated for:

1. **Format validity**: ISO 8601 or other standard format.
2. **Calendar validity**: Date exists in calendar.
3. **Range validity**: Within representable range.
4. **Timezone validity**: Timezone is recognized.
5. **Consistency**: Times are internally consistent.

---

## Time in Digital Twin Pattern

Time is one of the 8 dimensions of digital twins:

```yaml
- entity_instance: OTCHERE DC-01
  time:
    created: 2024-01-15T08:00:00Z
    operational_since: 2024-01-15T08:00:00Z
    last_maintenance: 2026-06-15T06:00:00Z
    planned_retirement: null
```

The digital twin's temporal record is essential.

---

## Time in Simulation

Time is the driver of simulation:

```yaml
- simulation:
  simulation_id: SIM-2026-08-29-001
  duration: PT24H
  trace:
    - timestamp: 2026-08-29T09:00:00Z
      event: OrderPlaced
    - timestamp: 2026-08-29T10:15:00Z
      event: PaymentReceived
    ...
```

Events occur at specific simulated times.

---

## Time vs Sequence vs Causality

Three distinct concepts:

- **Sequence (precedence)**: A before B (temporal order).
- **Causality**: A causes B (causal relationship).
- **Coincidence**: A and B at the same time (temporal overlap).

A before B does NOT imply A causes B.

---

## Related Concepts

- [Event](./event.md) — Events occur in time
- [State](./state.md) — States hold over time
- [Assertion](./assertion.md) — Assertions have temporal validity
- [Space](./space.md) — Space is the spatial dimension (parallel to time)

---

## Related ADRs

- ADR-WSF-09 — Foundational Concept Taxonomy
- ADR-WSF-19 — Semantic Relationship Model (temporal relationships)
- ADR-WSF-22 — Assertion and Provenance Model (temporal validity)

---

## Cross-Repository References

- Canonical semantic asset: [wsf/concepts/time.md](https://github.com/World-Semantic-Foundation/wsf/blob/main/concepts/time.md)
