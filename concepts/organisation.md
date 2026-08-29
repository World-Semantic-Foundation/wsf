# Organisation

> **An Organisation** is an Entity composed of multiple Actors pursuing shared Goals through coordinated Activities, with defined Roles, Authorities, and Processes.
## Semantic Identity

```yaml
semantic_id: wsf:Organisation
preferred_name: Organisation
aliases: [Enterprise, Institution, Agency]
status: Baseline
version: 0.1.0
classification: Tier 3 (Specialisation)
parent: wsf:Entity
defined_by: ADR-WSF-08, ADR-WSF-15
authority: WSF
```

---

## Definition

A **Organisation** is a structured Entity of Actors with shared Goals, Roles, and Authorities.

Organisations coordinate Actors toward Goals. Organisations define Roles for Members. Organisations establish Policies governing behaviour.

A Organisation is NOT:
- An individual Actor (use Actor or Entity);
- An informal group without shared structure (use Entity);
- A System without social structure (use System);

---

## Scope and Application

Organisations include enterprises, government agencies, NGOs, informal collectives. Organisation Boundaries MAY be legal, functional, or social.

---

## Differentia

Organisations have Members (Actors); Organisations have Governance (Rules, Policies); Organisations have Purposes (Goals); Organisations have Boundaries (membership, scope)

---

## Canonical Examples

**OTCHERE Inc** : an Organisation (enterprise) composed of Actors (employees, contractors), with defined Roles (Employer, Employee), Authorities (Capability Governance), and Goals (Order Fulfillment Excellence).

---

## Cross-References

- ADR-WSF-08
- ADR-WSF-15
- wsf:Entity : the parent foundational concept
- `/wsf-examples/` : worked examples

---

*Organisation is a Tier 3 specialisation. Status: Baseline.*
