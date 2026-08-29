# Evidence

> **A referenceable artifact (observation, document, measurement, or other empirical input) that supports the truth claim underlying an assertion.**

## Semantic Identity

```yaml
semantic_id: wsf:Evidence
preferred_name: Evidence
aliases: [Supporting Evidence, Empirical Input, Observation]
status: Baseline
version: 0.1.0
classification: Tier 2 (Supporting Construct)
parent: wsf:Assertion
defined_by: ADR-WSF-06, ADR-WSF-22
authority: WSF
```

---

## Definition

**Evidence** is a referenceable artifact (observation, document, measurement, or other empirical input) that supports the truth claim underlying an assertion. Evidence grounds assertions in empirical reality and enables trust assessment per ADR-WSF-22.

Evidence is NOT:
- An assertion itself (evidence supports assertions) ;
- A guarantee of truth (evidence may be flawed or misleading) ;
- The source of authority (use Provenance for that) ;
- A citation alone (evidence carries content, not just reference).

---

## Evidence Categories

### Direct Observation

First-hand empirical measurements:

- Sensor readings ;
- Manual observations ;
- Experimental data ;
- Direct measurements.

### Indirect Observation

Derived from direct observation:

- Statistical aggregations ;
- Computed indicators ;
- Inferred values ;
- Aggregated metrics.

### Documentary Evidence

Recorded in documents:

- Contracts ;
- Policies ;
- Specifications ;
- Historical records.

### Testimonial Evidence

Provided by individuals:

- Expert testimony ;
- Witness accounts ;
- Survey responses ;
- Interview data.

### Circumstantial Evidence

Established through context:

- Patterns ;
- Correlations ;
- Absence (evidence of absence) ;
- Default reasoning.

---

## Evidence Structure

A canonical evidence entry has these components:

| Component | Required | Purpose |
|---|---|---|
| Identifier | Yes | Unique evidence reference |
| Type | Yes | Evidence category |
| Content reference | Yes | Where evidence content lives |
| Attribution | Yes | Who/what produced the evidence |
| Time | Yes | When evidence was produced |
| Trust level | Yes | Reliability assessment |
| Validity period | Optional | Time-bounded applicability |

---

## Evidence Trust Assessment

Each piece of evidence carries a trust level:

### High Trust

Direct, primary, verifiable sources:

- Original sensor readings ;
- Authoritative documents ;
- Peer-reviewed publications ;
- First-hand expert testimony.

### Medium Trust

Indirect or interpreted sources:

- Aggregated data ;
- Second-hand reports ;
- Industry analyses ;
- Standard interpretations.

### Low Trust

Limited reliability:

- Anecdotal reports ;
- Outdated sources ;
- Conflicting accounts ;
- Unverified claims.

### Untrusted

Known or suspected unreliability:

- Fabricated sources ;
- Compromised instruments ;
- Confirmed bias ;
- Proven falsification.

---

## Evidence Content

Evidence content varies by type:

### Quantitative

Numerical or structured:

- Numeric measurements with units ;
- Time series ;
- Categorical counts ;
- Statistical distributions.

### Qualitative

Descriptive or narrative:

- Written descriptions ;
- Recorded interviews ;
- Photographic records ;
- Audio/video recordings.

### Reference

Pointer to other evidence:

- Citation to publication ;
- URL to source ;
- Reference to dataset ;
- Link to artefact.

---

## Evidence and Validity

Evidence and validity are related but distinct:

- **Validity** is rule conformance (does the assertion follow the rules) ;
- **Evidence** supports truth claims (is the assertion actually true).

An assertion can be valid but unsupported (no evidence) ; or supported but invalid (evidence present but assertion malformed).

---

## Evidence Chains

Evidence often comes in chains:

- Direct observation → Aggregated data → Indicator → Assertion ;
- Each step MAY carry its own evidence ;
- Chain transparency enables verification.

Evidence chains are recorded in Provenance.

---

## Evidence Authoring

Evidence is authored and registered:

1. **Acquisition** : evidence artifact acquired from source ;
2. **Validation** : evidence format and content validated ;
3. **Trust assessment** : trust level assigned ;
4. **Registration** : evidence registered in evidence catalog ;
5. **Linking** : evidence linked to supporting assertions ;
6. **Maintenance** : evidence maintained per retention policy.

---

## Evidence Retention

Evidence retention follows policy:

- Retention period per evidence type ;
- Storage medium appropriate to evidence ;
- Access controls ;
- Audit trail ;
- Disposal procedures.

---

## Evidence Reuse

Evidence MAY be reused across assertions:

- Same observation supporting multiple claims ;
- Aggregation results supporting several assertions ;
- Documentary evidence cited by multiple parties.

Reuse is tracked to enable impact analysis.

---

## Evidence vs Provenance

| Aspect | Evidence | Provenance |
|---|---|---|
| Purpose | Supports truth claim | Attributes authorship/history |
| Subject | Reality claim | Assertion itself |
| Required for | Trust assessment | Attribution |
| Content | Empirical artifact | Metadata trail |

Both are required for fully-attributed assertions.

---

## Canonical Examples

```yaml
# Direct observation evidence
- evidence:
    identifier: obs-2026-08-29-001
    type: direct_observation
    content: sensor_reading: temperature=22.5C, humidity=45%
    attribution: OTCHERE DC-01 environmental sensor
    time: 2026-08-29T10:30:00Z
    trust: High

# Documentary evidence
- evidence:
    identifier: doc-2026-08-29-001
    type: documentary
    content_reference: documents/contracts/OTCHERE-SUPPLY-001.pdf
    attribution: OTCHERE Inc Legal Department
    time: 2026-08-15
    trust: High

# Aggregated evidence
- evidence:
    identifier: agg-2026-Q3-revenue
    type: indirect_observation
    content: total_revenue: $1,250,000 (Q3 2026)
    attribution: OTCHERE Inc Finance
    time: 2026-09-30
    trust: Medium
```

---

## Cross-References

- ADR-WSF-06 : Evidence and Provenance
- ADR-WSF-22 : Assertion and Provenance Model
- wsf:Assertion : the parent construct that evidence supports
- wsf:Provenance : attribution metadata for the evidence itself
- wsf:Validity : evaluation of conformance to rules

---

*Evidence is a Tier 2 supporting construct. Status: Baseline.*