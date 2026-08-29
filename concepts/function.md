# Function

> **A Function** is a purposeful kind of Activity enabled by Capability, representing a defined category of work that an Entity performs.
## Semantic Identity

```yaml
semantic_id: wsf:Function
preferred_name: Function
aliases: [Operation Type, Activity Type]
status: Baseline
version: 0.1.0
classification: Tier 3 (Specialisation)
parent: wsf:Disposition
defined_by: ADR-WSF-07, ADR-WSF-08
authority: WSF
```

---

## Definition

A **Function** is a purposeful kind of Activity that a Capability enables an Entity to perform.

Functions categorise work. A Capability enables one or more Functions. An Activity is an actual occurrence of a Function.

A Function is NOT:
- The actual execution of work (use Activity);
- The ability to perform work (use Capability);
- A Process that orchestrates Functions (use Process);
- A Role that assigns Functions (use Role);

---

## Scope and Application

Functions describe the kind of activity, not the activity itself. An Entity MAY have Functions defined within its capability portfolio.

---

## Differentia

Functions are categorisations of work; Capabilities enable Functions; Activities are actual executions of Functions; Functions MAY be enabled by multiple Capabilities

---

## Canonical Examples

**OTCHERE Inc possesses Order Fulfillment Function** : enabled by Order Fulfillment Capability; instances are individual order Activities.

---

## Cross-References

- ADR-WSF-07
- ADR-WSF-08
- wsf:Disposition : the parent foundational concept
- `/wsf-examples/` : worked examples

---

*Function is a Tier 3 specialisation. Status: Baseline.*
