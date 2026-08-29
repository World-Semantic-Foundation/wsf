# Policy

> **A Policy** is a Rule (or set of Rules) governing Entity behaviour within an Organisation, expressing Goals, Constraints, and Authorities in actionable form.
## Semantic Identity

```yaml
semantic_id: wsf:Policy
preferred_name: Policy
aliases: [Governance Rule, Organisational Directive]
status: Baseline
version: 0.1.0
classification: Tier 3 (Specialisation)
parent: wsf:Rule
defined_by: ADR-WSF-15, ADR-WSF-25
authority: WSF
```

---

## Definition

A **Policy** is an organisational Rule expressing Goals, Constraints, and Authorities as actionable guidelines.

Policies operationalise Governance. Policies translate Goals into Constraints and Authorities into Actions.

A Policy is NOT:
- A formal logical Rule (use Rule);
- A Goal without guidance on implementation (use Goal);
- A Procedure step-by-step (use Process);

---

## Scope and Application

Policies include security policies, privacy policies, operational policies, business policies. Policies MAY have exceptions and waivers.

---

## Differentia

Policies are governance artefacts; Policies guide decisions; Policies MAY be enforced automatically (technical) or manually (procedural); Policies MAY be hierarchical

---

## Canonical Examples

**OTCHERE Data Privacy Policy** : a Policy governing how OTCHERE handles customer data; expresses the Goal (privacy protection) as actionable Constraints (data minimisation, retention limits) and Authorities (DPO authority).

---

## Cross-References

- ADR-WSF-15
- ADR-WSF-25
- wsf:Rule : the parent foundational concept
- `/wsf-examples/` : worked examples

---

*Policy is a Tier 3 specialisation. Status: Baseline.*
