# WSF Provenance Module

> **The four epistemic qualifiers for assertions: Evidence, Provenance, Authority, Trust.**

Defined by ADR-WSF-22 (Assertion and Provenance Model) §8-9, §12 and the Tier 2 concepts Evidence, Provenance, Authority (plus Validity as the assessment frame).

---

## Semantic Identity

```yaml
semantic_id: wsf:Provenance
preferred_name: Epistemic Qualification
status: Baseline
version: 0.1.0
defined_by: ADR-WSF-22 (Assertion and Provenance Model)
classification: Foundational
domain: Epistemology
```

---

## The Four Epistemic Qualifiers

| Qualifier | Question answered | Concept |
|---|---|---|
| **Provenance** | Where did this claim come from, and who made it? | wsf:Provenance |
| **Evidence** | What supports the claim? | wsf:Evidence |
| **Authority** | What gives the claim its weight? | wsf:Authority |
| **Trust** | How much should consumers rely on the claim? | trust assessment (per assertion) |

Every assertion MUST carry provenance; it MAY carry evidence and trust. Authority is carried by the provenance authority chain.

---

## Provenance Structure

Per ADR-WSF-22 §8, every assertion SHALL carry:

```yaml
- provenance:
  source: <Source of the assertion>          # Where did this come from?
  asserted_by: <Agent that asserted it>      # Who made this claim?
  asserted_at: <ISO timestamp>               # When was it asserted?
  authority: <Authority for the assertion>   # What gives it weight?
  method: <Method used to assert>            # How was it derived?
  derivation: <Derivation chain if derived>   # If derived, from what?
  references: <External references>          # Supporting references
  last_verified_at: <ISO timestamp>         # Last verification
  last_verified_by: <Agent>                   # Who verified last
```

The Semantic Authority Chain governs authority conflicts: authorities inherit from the World Semantic Authority; higher authorities resolve lower-authority conflicts (per the identity resolution rules of ADR-WSF-18 §8 and the Universal-Concepts authority chain).

---

## Evidence Structure

Per ADR-WSF-22 §9:

```yaml
- evidence:
  - evidence_id: wsf-evidence:<id>
    type: Observation | Measurement | Document | Record | TestResult | ExternalSource
    description: What the evidence shows
    source: Where the evidence came from
    collected_by: Who collected it
    collected_at: When it was collected
    reliability: High | Medium | Low
    confidence: 0.0-1.0
```

Evidence strength combines reliability and confidence. In assertion conflicts (ADR-WSF-22 §17), stronger evidence prevails where authority is equal.

---

## Trust Assessment

Per ADR-WSF-22 §12, a trust assessment MAY accompany an assertion:

```yaml
- trust:
  score: 0.0-1.0
  basis:
    - authority-standing
    - evidence-strength
    - verification-recency
  assessed_by: <Agent or authority>
  assessed_at: <ISO timestamp>
```

Trust is assessed, never implied. Implicit trust is a rejected alternative (ADR-WSF-22 §22 E).

---

## The Qualifiers in Assertion Lifecycle

| Lifecycle event | Epistemic role |
|---|---|
| Proposed | Provenance present; evidence optional |
| Active | Context-valid; provenance intact |
| Confirmed | Independent evidence present; verification recorded |
| Disputed | Contradicting evidence recorded |
| Rejected | Rejecting evidence outranks supporting |
| Expired | Temporal validity ended (validity, not trust) |

---

## Canonical Example

```yaml
- assertion:
    semantic_id: wsf-assertion:OTCHERE-possesses-OMC-001
    subject: wsf-ex:OTCHERE-Inc
    relationship: wsf-rel:possesses
    object: wsf-ex:OrderManagementCapability
    evidence:
      - evidence_id: wsf-evidence:capability-model-2026
        type: Document
        source: OTCHERE Inc capability model
        collected_by: wsf-ex:Kwesi
        collected_at: 2026-08-29
        reliability: High
        confidence: 0.9
    provenance:
      source: OTCHERE Inc Architecture Team
      asserted_by: wsf-ex:Kwesi
      asserted_at: 2026-08-29
      authority: wsf-ex:OTCHERE-Architecture-Board
    trust:
      score: 0.9
      basis: [authority-standing, evidence-strength]
    status: Confirmed
```

---

## Cross-References

- [Evidence concept](../concepts/evidence.md), [Provenance concept](../concepts/provenance.md), [Authority concept](../concepts/authority.md), [Validity concept](../concepts/validity.md)
- ADR-WSF-22 §8-9, §12, §17
- [Assertions module](../assertions/README.md)

---

*Status: Baseline. Changes occur only through the ADR/CR process.*
