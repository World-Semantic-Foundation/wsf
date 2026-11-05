# The Assertion Pattern

> **The normative structure of a WSF semantic assertion.**

Per ADR-WSF-22 (Assertion and Provenance Model) §4-5, §7, §10-13.

---

## Semantic Identity

```yaml
semantic_id: wsf:AssertionPattern
preferred_name: Semantic Assertion Pattern
status: Baseline
version: 0.1.0
defined_by: ADR-WSF-22 (Assertion and Provenance Model)
classification: Foundational
domain: Semantics
```

---

## Full Structure

```yaml
- assertion:
  # Core (required)
  semantic_id: wsf-assertion:<assertion-id>      # Unique identifier
  subject: <Entity or Concept reference>
  relationship: <Relationship reference>
  object: <Entity or Concept reference>

  # Optional Qualifiers
  context: <Context reference>
  time: <Time specification>
  conditions: <Conditions under which assertion holds>
  evidence: <Evidence references>
  provenance: <Provenance metadata>
  trust: <Trust assessment>

  # Governance
  status: Proposed | Active | Confirmed | Disputed | Rejected | Expired | Superseded | Withdrawn
  version: Semantic version
  authority: Governance authority
  created_at: ISO timestamp
  last_modified_at: ISO timestamp
```

---

## Required vs Optional

### Required (MUST be present for a valid assertion)

1. **Semantic Identity**: Stable identifier.
2. **Subject**: What the assertion is about.
3. **Relationship**: How subject relates to object; drawn from the governed vocabulary (ADR-WSF-19).
4. **Object**: What the subject relates to.
5. **Provenance**: Who asserted it and when.

An assertion without provenance is invalid (rejected alternative A, ADR-WSF-22 §22).

### Optional (MAY be present)

1. **Context**: The applicable context.
2. **Time**: Temporal validity.
3. **Conditions**: Under what conditions the assertion holds.
4. **Evidence**: Supporting evidence.
5. **Trust**: Trust assessment.

---

## Truth vs Validity (Critical Distinction)

An assertion is NOT truth:

- **Assertion**: A semantic claim, valid per its structure.
- **Truth**: Whether the claim corresponds to reality.

| | Valid | Invalid |
|---|---|---|
| **True** | Valid AND True | n/a (truth of an invalid claim is meaningless) |
| **False** | Valid AND False | Invalid |

This distinction is essential for semantic governance: validation checks structure and governance, never correspondence to reality.

---

## Context in Assertions

Assertions are made in contexts; context qualifies applicability and interpretation:

```yaml
context: wsf-ctx:enterprise-architecture
```

The same subject-relationship-object triple MAY hold in one context and not another. Context applicability follows ADR-WSF-14 (Semantic Context and Boundary).

---

## Time in Assertions

Temporal qualification constrains when the assertion holds:

```yaml
time:
  valid_from: 2026-01-01
  valid_to: null            # open-ended
  temporal_qualifier: holds-during
```

Temporal Validity is distinct from lifecycle: an assertion can be Active (lifecycle) and temporally expired (validity), or vice versa.

---

## Conditions on Assertions

Assertions MAY be conditioned:

```yaml
conditions:
  - "Pricing terms unchanged"
  - "Service tier: Enterprise"
```

A conditioned assertion holds only when its conditions are satisfied. Conditions are part of the semantic contract of the assertion.

---

## Multi-Party Assertions

Assertions MAY involve multiple parties with different epistemic stances:

```yaml
- assertion:
    subject: wsf-ex:OTCHERE-Inc
    relationship: wsf-rel:provides
    object: wsf-ex:DataHostingService
    asserted_by: wsf-ex:Kwesi
    confirmed_by: [wsf-ex:ExternalAuditor]
    disputed_by: []
```

---

## Validation Levels

Assertions are validated at three levels (ADR-WSF-22 §15-16):

1. **Structural validation**: required components present, well-formed references.
2. **Semantic validation**: relationship domain/range match, context applicability, condition coherence.
3. **Provenance validation**: provenance complete, authority chain intact, evidence resolvable.

---

## Cross-References

- [Assertion Lifecycle](./assertion-lifecycle.md)
- [Machine-Readable Examples](./assertion-examples.yaml)
- [Relationships module](../relationships/README.md)
- ADR-WSF-22
