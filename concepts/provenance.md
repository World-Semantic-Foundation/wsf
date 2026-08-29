# Provenance

> **The complete, traceable record of how an assertion came to be: who created it, when, under what authority, with what evidence, and through what derivation chain.**

## Semantic Identity

```yaml
semantic_id: wsf:Provenance
preferred_name: Provenance
aliases: [Attribution Metadata, Audit Trail, Source Chain]
status: Baseline
version: 0.1.0
classification: Tier 2 (Supporting Construct)
parent: wsf:Assertion
defined_by: ADR-WSF-06, ADR-WSF-22
authority: WSF
```

---

## Definition

**Provenance** is the complete, traceable record of how an assertion came to be. Provenance captures who created the assertion, when, under what authority, with what evidence, and through what derivation chain. Provenance enables accountability, trust assessment, and reproducibility per ADR-WSF-22.

Provenance is NOT:
- An assertion itself (provenance attributes assertions) ;
- Evidence (provenance carries metadata, evidence carries empirical content) ;
- A guarantee of correctness (provenance enables verification, not verification itself) ;
- Optional (provenance is mandatory for governance-grade assertions).

---

## Provenance Components

A canonical provenance record has these components:

| Component | Required | Purpose |
|---|---|---|
| Asserted by | Yes | Authority or agent that created the assertion |
| Asserted at | Yes | When the assertion was created |
| Asserted from | Yes | Source location or system |
| Authority | Yes | Authoritative basis for the assertion |
| Method | Optional | How the assertion was derived |
| Evidence references | Yes | Links to supporting evidence |
| Version | Optional | Assertion version |
| Signature | Optional | Cryptographic signature for integrity |

---

## Provenance Chain

Provenance MAY form a chain:

- Each assertion has direct provenance ;
- Assertions derived from other assertions carry their source's provenance ;
- Chains enable tracing back to original observations ;
- Chain depth typically 1-3 levels, occasionally more.

Chain representation:

```
Observation (T0) → Derived data (T1) → Aggregation (T2) → Assertion (T3)
   ↓                   ↓                    ↓                ↓
[provenance A]    [provenance B]        [provenance C]   [provenance D]
   ↓                   ↓                    ↓                ↓
       derives from →     derives from →     derives from →
```

---

## Provenance and Authority

Provenance records the authority basis:

- **Authority level** : foundational, organisational, individual ;
- **Authority scope** : domain of authority ;
- **Authority reference** : identifier of the authority ;
- **Authority validation** : how authority was verified.

Authority determines the assertion's weight in trust assessment.

---

## Provenance and Time

Provenance records multiple time markers:

- **Asserted at** : when the assertion was made ;
- **Valid from** : when the assertion became effective ;
- **Valid until** : when the assertion ceases to be effective (if bounded) ;
- **Observed at** : when the underlying reality was observed (for empirical claims) ;
- **Recorded at** : when the provenance itself was recorded.

Time markers enable temporal reasoning.

---

## Provenance Authoring

Provenance is authored when an assertion is created:

1. **Capturing** : provenance fields captured at assertion creation ;
2. **Validation** : provenance validity verified (authority known, time valid) ;
3. **Signing** : cryptographic signature applied (if enabled) ;
4. **Recording** : provenance stored immutably ;
5. **Linking** : provenance linked to evidence ;
6. **Maintenance** : provenance maintained through assertion lifecycle.

---

## Provenance Immutability

Provenance records are immutable:

- Once recorded, provenance cannot be altered ;
- Corrections create new provenance records ;
- History preserved through audit trail ;
- Tamper-detection through cryptographic signing.

Immutability ensures provenance remains trustworthy.

---

## Provenance vs Evidence

| Aspect | Provenance | Evidence |
|---|---|---|
| Purpose | Attributes assertion | Supports truth claim |
| Content | Metadata | Empirical artifact |
| Example | "Asserted by OTCHERE Inc on 2026-08-29" | Temperature sensor reading |
| Type | Audit information | Empirical content |

Both are required for fully-attributed assertions.

---

## Provenance and Trust

Provenance enables trust assessment:

- Authoritativeness of assertor ;
- Reliability of method ;
- Recency of observation ;
- Chain of derivation ;
- Cryptographic integrity.

Trust flows from provenance to assertion.

---

## Provenance in Canonical Examples

```yaml
# OTCHERE Inc assertion provenance
- assertion:
    subject: wsf-ex:OTCHERE-Inc
    predicate: wsf-rel:possesses
    object: wsf-cap:OrderFulfillment
    provenance:
      asserted_by:
        identifier: wsf-ex:OTCHERE-Inc
        type: organisation
      asserted_at: 2026-08-29T10:30:00Z
      authority: OTCHERE Inc Capability Governance
      method: formal_declaration
      evidence_references:
        - evidence:doc-2026-08-29-capability-declaration
      signature: ed25519:abc123...

# Derived assertion with chain
- assertion:
    subject: wsf-ex:OTCHERE-Inc
    predicate: wsf-rel:hasAnnualRevenue
    object: 1250000
    provenance:
      asserted_by:
        identifier: wsf-ex:OTCHERE-Inc-Finance
        type: department
      asserted_at: 2026-09-30T16:00:00Z
      authority: OTCHERE Inc Financial Reporting
      method: aggregated_from_transactions
      derived_from:
        - assertion:tx-2026-Q3-001
        - assertion:tx-2026-Q3-002
      evidence_references:
        - evidence:agg-2026-Q3-revenue
```

---

## Provenance Privacy

Provenance respects privacy:

- Personally identifiable information in provenance is access-controlled ;
- Aggregated provenance available without individual details ;
- Pseudonymisation for shared provenance ;
- Confidentiality boundaries enforced.

---

## Cross-References

- ADR-WSF-06 : Evidence and Provenance
- ADR-WSF-22 : Assertion and Provenance Model (provenance structure)
- wsf:Assertion : the parent construct that provenance attributes
- wsf:Evidence : empirical support referenced from provenance
- wsf:Authority : authority basis recorded in provenance

---

*Provenance is a Tier 2 supporting construct. Status: Baseline.*