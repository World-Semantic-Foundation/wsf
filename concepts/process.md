# Process

> **A Process** is a structured, repeatable, ordered sequence of Activities that transforms inputs into outputs according to defined rules, governed by an owning Entity.
## Semantic Identity

```yaml
semantic_id: wsf:Process
preferred_name: Process
aliases: [Workflow, Procedure, Pipeline]
status: Baseline
version: 0.1.0
classification: Tier 3 (Specialisation)
parent: wsf:Event
defined_by: ADR-WSF-08, ADR-WSF-12
authority: WSF
```

---

## Definition

A **Process** is a structured sequence of Events (Activities) that produces defined Outcomes through governed transformation.

Processes are governed by Process owners who define inputs, outputs, rules, and performance expectations. Process instances generate Events that are recorded in time.

A Process is NOT:
- A single Activity (use Activity);
- An Outcome (use Outcome);
- A Capability to perform work (use Capability);
- A random sequence of Events;

---

## Scope and Application

Processes are abstract templates. Instantiations are Events. Processes MAY have sub-processes; sub-processes MAY recursively decompose.

---

## Differentia

Processes have defined inputs, outputs, owners, and rules; they MAY be instantiated multiple times; each instantiation is an Event that occurs in time

---

## Canonical Examples

**OTCHERE Order Fulfillment Process** : a Process with stages (Order Received, Payment Confirmed, Inventory Allocated, Order Shipped, Delivery Confirmed). Each stage is an Activity. Each execution is an Event.

---

## Cross-References

- ADR-WSF-08
- ADR-WSF-12
- wsf:Event : the parent foundational concept
- `/wsf-examples/` : worked examples

---

*Process is a Tier 3 specialisation. Status: Baseline.*
