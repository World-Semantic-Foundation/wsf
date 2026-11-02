# The Assertion Lifecycle

> **Assertions are governed artifacts: they are proposed, activated, confirmed, disputed, expired, superseded, and withdrawn through explicit states.**

Per ADR-WSF-22 (Assertion and Provenance Model) §6, §17-19.

---

## Semantic Identity

```yaml
semantic_id: wsf:AssertionLifecycle
preferred_name: Assertion Lifecycle
status: Baseline
version: 0.1.0
defined_by: ADR-WSF-22 (Assertion and Provenance Model)
classification: Foundational
domain: Semantics
```

---

## Lifecycle States

```
Proposed → Active → Confirmed | Disputed | Rejected | Expired | Superseded | Withdrawn
```

| State | Meaning | Governance |
|---|---|---|
| **Proposed** | Newly asserted, awaiting review | Source asserted, awaiting confirmation |
| **Active** | Currently in force | Valid in current context |
| **Confirmed** | Independently verified | Has independent confirming evidence |
| **Disputed** | Contested | Has contradicting evidence |
| **Rejected** | Determined invalid | Has rejecting evidence |
| **Expired** | Past temporal validity | Validity period ended |
| **Superseded** | Replaced by newer assertion | Newer assertion exists |
| **Withdrawn** | Source retracts | Source withdrew assertion |

---

## Assertion Conflicts

Two assertions conflict when they make incompatible claims about the same subject-relationship-object in the same context and overlapping time. Conflict resolution (ADR-WSF-22 §17):

1. Mark both assertions Disputed;
2. Compare provenance authority (Semantic Authority Chain);
3. Compare evidence strength (per Evidence reliability/confidence);
4. The stronger assertion is Confirmed; the weaker is Rejected or remains Disputed;
5. The resolution is itself recorded as an assertion with provenance.

---

## Assertion Derivation

Assertions MAY be derived from other assertions:

```yaml
- assertion:
    semantic_id: wsf-assertion:derived-001
    derived_from: [wsf-assertion:source-001, wsf-assertion:source-002]
    derivation_method: "composition of possesses chains"
    provenance:
      method: derivation
```

A derived assertion carries its full derivation chain; removing a source assertion triggers re-evaluation of all derived assertions.

---

## Assertion Withdrawal

The asserting source MAY withdraw an assertion:

```
Active → Withdrawn
```

Withdrawal is recorded with who withdrew, when, and why. Withdrawn assertions are retained (never deleted); consumers of a withdrawn assertion are notified through the change-notification surface (ADR-WSF-24 §7).

---

## Canonical Example

```yaml
- assertion:
    semantic_id: wsf-assertion:DC01-operational-2026
    subject: wsf-ex:OTCHERE-DC-01
    relationship: wsf-rel:holds-during
    object: wsf-ex:FY2026-Interval
    status: Confirmed
    evidence:
      - wsf-evidence:DC01-uptime-report-2026
    provenance:
      asserted_by: wsf-ex:Kwesi
      asserted_at: 2026-03-01
      last_verified_at: 2026-09-01
      last_verified_by: wsf-ex:ExternalAuditor
```

---

## Cross-References

- [Assertion Pattern](./assertion-pattern.md)
- [Machine-Readable Examples](./assertion-examples.yaml)
- [Provenance module](../provenance/README.md)
- ADR-WSF-22
