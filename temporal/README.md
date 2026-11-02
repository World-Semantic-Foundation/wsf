# WSF Temporal Module

> **Time semantics: Instant, Interval, Duration; and the critical distinctions Precedence ≠ Causality and Temporal Validity ≠ Lifecycle.**

Defined by the Time concept (wsf:Time, Tier 1) and exercised in ADR-WSF-19 (Temporal relationships) and ADR-WSF-22 (time in assertions).

---

## Semantic Identity

```yaml
semantic_id: wsf:Time
preferred_name: Temporal Semantics
status: Baseline
version: 0.1.0
defined_by: ADR-WSF-17 (Foundational Semantic Architecture); ADR-WSF-19 §5.3; ADR-WSF-22 §11
classification: Foundational
domain: Time
```

---

## The Three Temporal Primitives

| Primitive | Definition | Serialization |
|---|---|---|
| **Instant** | A point in time | ISO 8601 timestamp (`2026-08-29T10:00:00Z`) |
| **Interval** | A bounded span between two instants | `{ valid_from, valid_to }` |
| **Duration** | A length of time, unanchored | ISO 8601 duration (`P7Y`, `PT24H`) |

Instants and intervals are anchored to the timeline; durations are not. An interval plus a duration determines a derived interval; a duration alone does not determine when anything holds.

---

## Temporal Relationship Semantics

The Temporal Form of relation (ADR-WSF-19 §5.3):

| Relationship | Semantics |
|---|---|
| `wsf-rel:before` | A occurs before B (transitive, asymmetric) |
| `wsf-rel:after` | A occurs after B (inverse of before) |
| `wsf-rel:during` | Event occurs within an interval |
| `wsf-rel:holds-during` | State holds within an interval |

### Precedence ≠ Causality

> A before B does not imply A caused B.

Temporal relations carry no causal commitment. Causal relations (`causes`, `triggers`) imply precedence but not the converse. Night follows day; night does not cause day.

---

## Temporal Validity ≠ Lifecycle

Two independent clocks govern every assertion:

1. **Temporal validity**: the interval during which the assertion holds in the world (`time: { valid_from, valid_to }`).
2. **Lifecycle**: the governance state of the assertion as an artifact (Proposed, Active, Confirmed, ...).

| | Lifecycle Active | Lifecycle Withdrawn |
|---|---|---|
| **Temporally valid** | Holds now | No longer asserted; historical reference |
| **Temporally expired** | Past claim, retained | n/a |

An assertion can be Active (lifecycle) and Expired (validity): the claim's window has passed but the artifact remains governed. It can also be Withdrawn while still inside its validity window: the source retracted it.

---

## Time in Assertions

Per ADR-WSF-22 §11:

```yaml
time:
  valid_from: 2026-01-01
  valid_to: null
  temporal_qualifier: wsf-rel:holds-during
```

States MUST be temporally qualified (per the Entity concept: an entity's state MUST be qualified temporally).

---

## Canonical Example

```yaml
- assertion:
    semantic_id: wsf-assertion:DC01-operational-2026
    subject: wsf-ex:OTCHERE-DC-01
    relationship: wsf-rel:holds-during
    object: wsf-ex:FY2026-Maintenance-Interval
    time:
      valid_from: 2026-01-01
      valid_to: 2026-12-31
    status: Active

- interval:
    semantic_id: wsf-ex:FY2026-Maintenance-Interval
    begins: 2026-01-01T00:00:00Z
    ends: 2026-12-31T23:59:59Z
    duration: P365D
```

---

## Cross-References

- [Time concept](../concepts/time.md), [Event concept](../concepts/event.md), [State concept](../concepts/state.md)
- ADR-WSF-19 §5.3, ADR-WSF-22 §11
- [Assertions module](../assertions/README.md)

---

*Status: Baseline. Changes occur only through the ADR/CR process.*
