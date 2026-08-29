# Actor

> **An Actor** is an Entity that performs Activities, makes Assertions, or bears Responsibilities, typically within an Organisation or System.
## Semantic Identity

```yaml
semantic_id: wsf:Actor
preferred_name: Actor
aliases: [Agent, Participant, Performer]
status: Baseline
version: 0.1.0
classification: Tier 3 (Specialisation)
parent: wsf:Entity
defined_by: ADR-WSF-08, ADR-WSF-15
authority: WSF
```

---

## Definition

A **Actor** is an Entity that performs Activities or makes Assertions within a context.

Actors perform Activities, make Assertions, bear Responsibilities. Actor identification is critical for Provenance and Authority attribution.

A Actor is NOT:
- An Entity that does not act (use Entity);
- A Role held by an Actor (use Role);
- An Activity performed by an Actor (use Activity);

---

## Scope and Application

Actors include individuals (Kwesi), organisations (OTCHERE Inc), and computational agents (software bots). Actors MAY have multiple Roles.

---

## Differentia

Actors have agency (ability to act); Actors MAY be human, organisational, or computational (agents); Actors have Roles; Actors bear Responsibilities

---

## Canonical Examples

**Kwesi** is an Actor (individual) at OTCHERE Inc, holding Roles (Employee, Enterprise Architect), performing Activities (designing capability model), bearing Responsibilities (architecture governance).

---

## Cross-References

- ADR-WSF-08
- ADR-WSF-15
- wsf:Entity : the parent foundational concept
- `/wsf-examples/` : worked examples

---

*Actor is a Tier 3 specialisation. Status: Baseline.*
