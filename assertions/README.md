# WSF Assertions Module

> **The Semantic Assertion Model: the Subject + Relationship + Object core pattern, its required and optional qualifiers, lifecycle, validation, and conflict handling.**

Defined by ADR-WSF-22 (Assertion and Provenance Model). An assertion is a semantic claim; it is not truth. Assertions carry provenance, may carry evidence, context, time, conditions, and trust assessments, and move through a governed lifecycle.

---

## Module Structure

```
assertions/
├── README.md                   (this file)
├── assertion-pattern.md        The assertion structure and required/optional components
├── assertion-lifecycle.md     The 8 lifecycle states, conflicts, derivation, withdrawal
└── assertion-examples.yaml    Machine-readable canonical examples (OTCHERE/Kwesi)
```

---

## Governing Principle

> **An assertion is a valid semantic claim; truth is whether the claim corresponds to reality. An assertion can be valid and false.**

---

## The Assertion Pattern

```
Subject ──Relationship──► Object
   qualified by: Context, Time, Conditions, Evidence, Provenance, Trust
```

Required (MUST): semantic identity, subject, relationship, object, provenance.
Optional (MAY): context, time, conditions, evidence, trust.

See the [Assertion Pattern](./assertion-pattern.md) for the full structure.

---

## Canonical Example

```yaml
- assertion:
    semantic_id: wsf-assertion:OTCHERE-possesses-OMC-001
    subject: wsf-ex:OTCHERE-Inc
    relationship: wsf-rel:possesses
    object: wsf-ex:OrderManagementCapability
    context: wsf-ctx:enterprise-architecture
    time: { valid_from: 2026-01-01 }
    evidence: [wsf-evidence:capability-model-2026]
    provenance:
      asserted_by: wsf-ex:Kwesi
      asserted_at: 2026-08-29
    status: Active
```

---

## Assets

- [Assertion Pattern](./assertion-pattern.md)
- [Assertion Lifecycle](./assertion-lifecycle.md)
- [Machine-Readable Examples](./assertion-examples.yaml)

---

## Cross-References

- ADR-WSF-22: Assertion and Provenance Model
- [Assertion concept](../concepts/assertion.md), [Proposition concept](../concepts/proposition.md)
- [Relationships module](../relationships/README.md), [Provenance module](../provenance/README.md)

---

*Status: Baseline. Changes occur only through the ADR/CR process.*
