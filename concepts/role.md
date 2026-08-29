# Role

> **A Role** is a contextualised identity that an Entity assumes within a specific context, defining the Entity's expected behaviour, responsibilities, and relationships in that context.
## Semantic Identity

```yaml
semantic_id: wsf:Role
preferred_name: Role
aliases: [Position, Function-as-Identity, Contextual Identity]
status: Baseline
version: 0.1.0
classification: Tier 3 (Specialisation)
parent: wsf:Entity
defined_by: ADR-WSF-08, ADR-WSF-09, ADR-WSF-11
authority: WSF
```

---

## Definition

A **Role** is a contextualised Entity identity that defines expected behaviour and responsibilities within a specific scope.

Roles operationalise Entity identity in specific contexts. A Role carries expectations (what the Entity SHOULD do), rights (what the Entity MAY do), and obligations (what the Entity MUST do).

A Role is NOT:
- An uncontextualised Entity identity (use Entity directly);
- A capability to perform (use Capability);
- A static job title (use Term within a Role);
- A permission or access right (use Authority);

---

## Scope and Application

Roles exist within bounded contexts. A person MAY be an Employee in one organisation and a Customer in another. Role changes are tracked as assertions with provenance.

---

## Differentia

Roles are bound to contexts (e.g., employer, customer, supplier); an Entity MAY hold multiple Roles concurrently across different contexts; Role transitions are governed events

---

## Canonical Examples

**OTCHERE Inc** is an **Employer** (Role); **Kwesi** is an **Employee** (Role) of OTCHERE Inc. The Employer Role carries the expectation to provide compensation; the Employee Role carries the obligation to perform assigned work.

---

## Cross-References

- ADR-WSF-08
- ADR-WSF-09
- ADR-WSF-11
- wsf:Entity : the parent foundational concept
- `/wsf-examples/` : worked examples

---

*Role is a Tier 3 specialisation. Status: Baseline.*
