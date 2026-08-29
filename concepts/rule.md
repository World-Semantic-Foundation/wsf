# Rule

> **A Rule** is a normative Constraint on Entity behaviour or State, expressed as a logical condition that MAY be evaluated for compliance.
## Semantic Identity

```yaml
semantic_id: wsf:Rule
preferred_name: Rule
aliases: [Business Rule, Validation Rule, Norm]
status: Baseline
version: 0.1.0
classification: Tier 3 (Specialisation)
parent: wsf:Constraint
defined_by: ADR-WSF-13, ADR-WSF-15
authority: WSF
```

---

## Definition

A **Rule** is a normative Constraint expressed as an evaluable logical condition.

Rules constrain behaviour. Rule evaluation produces compliance status. Rule violations MAY trigger consequences.

A Rule is NOT:
- A general Constraint without logical form (use Constraint);
- A Goal without compliance criteria (use Goal);
- A Procedure that implements Rules (use Process);

---

## Scope and Application

Rules include business rules, validation rules, regulatory rules, technical rules. Rules MAY be composed into Policies.

---

## Differentia

Rules have explicit logical form (when/then); Rules MAY be machine-evaluable; Rules have compliance states (satisfied/violated); Rules MAY carry consequences

---

## Canonical Examples

**Rule: Orders over $10,000 require manager approval** : a Rule with logical form (when order amount > $10,000 then manager approval required); machine-evaluable; consequences for non-compliance (rejection, escalation).

---

## Cross-References

- ADR-WSF-13
- ADR-WSF-15
- wsf:Constraint : the parent foundational concept
- `/wsf-examples/` : worked examples

---

*Rule is a Tier 3 specialisation. Status: Baseline.*
