# Assertion

> **A governed statement that attributes a specific Proposition to a specific Agent under specific conditions, with provenance and optional evidence.**

---

## Semantic Identity

```yaml
semantic_id: wsf:Assertion
preferred_name: Assertion
aliases: [Semantic Assertion, Claim]
status: Normative
version: 1.0.0
classification: Tier 1 (Foundational)
parent: wsf:Entity
authority: WSF
```

---

## Definition

An **Assertion** is a governed statement that attributes a specific Proposition to a specific Agent under specific conditions, with provenance and optional evidence.

An Assertion is NOT:
- A Proposition (the proposition is what is asserted);
- A truth claim (assertions may be false);
- A belief (beliefs are mental; assertions are social);
- An unverified statement.

An Assertion IS:
- The act of claiming a proposition;
- Attributed to an agent;
- Made in a context;
- Tracked through lifecycle states;
- Supported by evidence (where applicable);
- Distinct from truth.

---

## Why Assertion Is Foundational

Assertion is foundational because:

1. **Semantic claims are assertions** — every semantic claim is an assertion;
2. **Provenance requires assertions** — provenance tracks assertions;
3. **Evidence supports assertions** — evidence is attached to assertions;
4. **Validation operates on assertions** — assertions can be validated;
5. **Trust is assessed on assertions** — trust is per-assertion;
6. **Conflicts are detected between assertions** — multiple assertions can be compared.

Without Assertion, we cannot attribute, validate, or trust semantic claims.

---

## Assertion Pattern

The basic pattern (per ADR-WSF-12, ADR-WSF-22):

```
Subject ──Relationship──► Object
```

Extended with context:

```
Subject ──Relationship──► Object
   │           │             │
   │           │             └─ Object reference
   │           └─ Relationship reference
   └─ Subject reference

Context: where the assertion applies
Time: when the assertion holds
Evidence: what supports it
Provenance: who, when, how
```

---

## Assertion Structure

```yaml
- assertion:
  # Required
  semantic_id: wsf-assertion:<id>
  subject: <Entity or Concept reference>
  relationship: <Relationship reference>
  object: <Entity or Concept reference>
  
  # Optional qualifiers
  context: <Context reference>
  time:
    valid_from: ISO timestamp
    valid_until: ISO timestamp or open-ended
    asserted_at: ISO timestamp
  conditions:
    - <condition under which the assertion holds>
  evidence:
    - <evidence item>
  
  # Governance
  status: Proposed | Active | Confirmed | Disputed | Rejected | Expired | Superseded | Withdrawn
  version: Semantic version
  authority: Governance authority
  
  # Provenance (required)
  provenance:
    source: <source>
    asserted_by: <agent>
    asserted_at: <timestamp>
    authority: <authority>
    method: <method>
  
  # Trust (optional)
  trust:
    level: High | Medium | Low | Unknown
    basis: How trust was assessed
  
  created_at: ISO timestamp
  last_modified: ISO timestamp
```

---

## Assertion Lifecycle States

Per ADR-WSF-12 and ADR-WSF-22:

```
Proposed → Active → Confirmed | Disputed | Rejected | Expired | Superseded | Withdrawn
```

| State | Meaning | Governance |
|---|---|---|
| **Proposed** | Newly asserted | Awaiting review |
| **Active** | Currently in force | Valid in current context |
| **Confirmed** | Independently verified | Has confirming evidence |
| **Disputed** | Contested | Has contradicting evidence |
| **Rejected** | Determined invalid | Has rejecting evidence |
| **Expired** | Past temporal validity | Validity period ended |
| **Superseded** | Replaced | Newer assertion exists |
| **Withdrawn** | Source retracts | Source withdrew |

---

## Assertion Examples

### Possession Assertion

```yaml
- assertion:
  semantic_id: wsf-assertion:OTCHERE-OrderFulfillment-001
  subject: wsf-ex:OTCHERE-Inc
  relationship: wsf-rel:possesses
  object: wsf-cap:OTCHERE-OrderFulfillment
  context: wsf-ctx:enterprise
  time:
    valid_from: 2026-08-29
    valid_until: open-ended
  evidence:
    - Architecture Assessment 2026
    - 10 years operational records
  provenance:
    source: OTCHERE Architecture Assessment 2026
    asserted_by: Kwesi
    asserted_at: 2026-08-29
    authority: OTCHERE Inc Architecture Team
  trust:
    level: High
    basis: 10 years operational evidence
  status: Active
```

### Role Assertion

```yaml
- assertion:
  semantic_id: wsf-assertion:Kwesi-EnterpriseArchitect-001
  subject: wsf-ex:Kwesi
  relationship: wsf-rel:assumes-role
  object: wsf-role:EnterpriseArchitect
  context: wsf-ctx:OTCHERE-Inc
  time:
    valid_from: 2020-01-01
    valid_until: open-ended
  evidence:
    - HR records
    - Architecture team membership
  provenance:
    source: OTCHERE HR Department
    asserted_by: OTCHERE HR Department
    asserted_at: 2026-08-29
    authority: OTCHERE Inc HR
  trust:
    level: High
  status: Active
```

### Event Assertion

```yaml
- assertion:
  semantic_id: wsf-assertion:Order12345-Payment-001
  subject: wsf-ex:Order-12345
  relationship: wsf-rel:has-event
  object: wsf-event:Payment-Received-12345
  context: wsf-ctx:OrderProcessing
  time:
    occurred_at: 2026-08-29T10:15:00Z
  evidence:
    - Payment gateway log
    - Bank statement
  provenance:
    source: OTCHERE Payment Gateway
    asserted_by: OTCHERE Payment Gateway
    asserted_at: 2026-08-29T10:16:00Z
    authority: OTCHERE Inc Finance
  trust:
    level: High
  status: Active
```

---

## Assertion vs Proposition (Critical Distinction)

| Aspect | Assertion | Proposition |
|---|---|---|
| **Nature** | Act of claiming | Content of claim |
| **Example** | Kwesi's claim about OTCHERE | "OTCHERE has Order Fulfillment" |
| **Truth** | Distinct from truth | Has truth value |
| **Identity** | Each assertion unique | Same proposition can be asserted multiple times |
| **Attribution** | Attributed to agent | Not attributed |

Proposition is the content; Assertion is the act of attributing it.

---

## Assertion Validation

Assertions SHALL be validated for:

1. **Structural validation**: Required fields present.
2. **Identity validation**: All references resolve.
3. **Domain/Range validation**: Subject/object types match relationship.
4. **Context validation**: Context exists and is applicable.
5. **Temporal validation**: Time values are valid.
6. **Evidence validation**: At least one evidence item (for Normative).
7. **Provenance validation**: Source, asserted_by, authority recorded.

---

## Multi-Party Assertions

Multiple agents may assert the same proposition:

```yaml
- multi_party_assertion:
  proposition: wsf-prop:OTCHERE-Has-OrderFulfillment
  assertions:
    - asserted_by: Kwesi
      asserted_at: 2026-08-29
      trust: High
    - asserted_by: OTCHERE Inc Board
      asserted_at: 2026-08-30
      trust: High
  consensus: Agreement (both assert the same proposition)
```

Disagreement may also be tracked:

```yaml
- multi_party_assertion:
  proposition: wsf-prop:OTCHERE-Has-Capability-X
  assertions:
    - asserted_by: Kwesi
      assertion_value: true
    - asserted_by: External Auditor
      assertion_value: false
  consensus: Disagreement
```

---

## Assertion Conflicts

When two assertions conflict:

```
Assertion A: OTCHERE possesses X (asserted by Kwesi)
Assertion B: OTCHERE does NOT possess X (asserted by External Auditor)
   ↓
Conflict detected
   ↓
Resolution paths:
  - Different contexts (no conflict)
  - Different times (no conflict)
  - Different definitions (resolve definition)
  - Genuine disagreement (mark disputed)
  - Error (correct or withdraw)
```

---

## Assertion Derivation

Assertions MAY be derived from other assertions:

```yaml
- assertion_X:
  derived_from:
    - assertion_A
    - assertion_B
  derived_using:
    rule: <derivation rule>
  derivation_method: <method used>
```

Derivation chains preserve provenance.

---

## Assertion Withdrawal

Assertions MAY be withdrawn:

```yaml
- assertion_withdrawal:
  assertion: wsf-assertion:<id>
  withdrawn_by: <agent>
  withdrawn_at: <timestamp>
  reason: <reason>
  superseding_assertion: <new assertion if any>
```

Withdrawn assertions are preserved for history.

---

## Related Concepts

- [Proposition](./proposition.md) — What is asserted
- [Concept](./concept.md) — Concepts participate in assertions
- [Entity](./entity.md) — Things that participate in assertions
- [Relationship](./relationship.md) — How things connect in assertions
- [Context](./context.md) — Where assertions apply

---

## Related ADRs

- ADR-WSF-05 — Semantic Assertion
- ADR-WSF-06 — Evidence & Provenance
- ADR-WSF-12 — Semantic Assertion Model
- ADR-WSF-22 — Assertion and Provenance Model

---

## Cross-Repository References

- Canonical semantic asset: [wsf/concepts/assertion.md](https://github.com/World-Semantic-Foundation/wsf/blob/main/concepts/assertion.md)
