# Validity

> **The state of an assertion, representation, or semantic construct conforming to its governing rules at a point in time ; a time-bounded, evaluable property distinct from truth.**

## Semantic Identity

```yaml
semantic_id: wsf:Validity
preferred_name: Validity
aliases: [Valid State, Conformance Status]
status: Baseline
version: 0.1.0
classification: Tier 2 (Supporting Construct)
parent: wsf:State
defined_by: ADR-WSF-13, ADR-WSF-22
authority: WSF
```

---

## Definition

**Validity** is the state of an assertion, representation, or semantic construct conforming to its governing rules at a point in time. Validity is a time-bounded, evaluable property; it can change as rules change or as the construct evolves. Validity is distinct from truth per ADR-WSF-22.

Validity is NOT:
- Truth (an assertion can be valid but false, or invalid but true) ;
- Permanence (validity has a temporal scope) ;
- Correctness in all senses (validity is rule-specific) ;
- Currency (a valid construct may be outdated).

---

## Validity vs Truth

The distinction is critical:

- **Truth** : correspondence to reality (does the assertion match what is) ;
- **Validity** : conformance to rules (does the assertion follow the specified form and constraints) ;

A WSF assertion can be:

| Validity | Truth | Status |
|---|---|---|
| Valid | True | Currently accepted claim |
| Valid | False | Erroneous claim requiring investigation |
| Invalid | True | True claim with structural defect |
| Invalid | False | Defective erroneous claim |

Validity is necessary but not sufficient for acceptance; truth verification is separate.

---

## Validity Scope

Validity applies to:

- Assertions (per ADR-WSF-12) ;
- Representations (per ADR-WSF-23) ;
- Concept definitions (per ADR-WSF-20) ;
- Relationships (per ADR-WSF-19) ;
- Identifiers (per ADR-WSF-18).

---

## Validity Levels

Validity can be assessed at multiple levels:

### Syntactic Validity

- Encoding parses per format specification ;
- No malformed structure ;
- Required fields present.

### Structural Validity

- Conforms to concept definition ;
- Required relationships present ;
- Cardinality constraints satisfied ;
- Type assertions correct.

### Semantic Validity

- Conforms to SHACL/ShEx shapes (per ADR-WSF-23) ;
- Inheritance rules respected (per ADR-WSF-04) ;
- Cross-references resolvable ;
- Constraint constraints satisfied.

### Contextual Validity

- Valid in the asserted context (per ADR-WSF-14) ;
- Authority appropriate for context ;
- Time-bounded validity respected.

---

## Validity States

Validity is a state that can change:

### Valid

The construct currently conforms to all applicable rules.

### Invalid

The construct currently fails one or more applicable rules:

- Validation errors recorded ;
- Reason for invalidity documented ;
- Remediation path identified.

### Indeterminate

Validity cannot be determined at this time:

- Required information missing ;
- Validation tools unavailable ;
- Conflict between rules under resolution.

### Void

The construct has no validity status:

- Deprecated and superseded ;
- Explicitly withdrawn ;
- Outside applicable scope.

---

## Validity Evaluation

Validity is evaluated through:

### Automated Validation

- SHACL validators ;
- ShEx validators ;
- Custom validators ;
- Continuous validation in pipelines.

### Manual Validation

- Domain expert review ;
- Peer review ;
- Editorial review.

### Periodic Revalidation

- Time-triggered re-evaluation ;
- Rule change triggers re-evaluation ;
- Reference change triggers re-evaluation.

---

## Validity Time-Bounding

Validity has temporal scope:

### Valid From

The earliest time the construct became valid.

### Valid Until

The latest time the construct remains valid (if bounded).

### Re-evaluation Period

How often validity is re-checked.

### Validity Expiry

When validity lapses if not renewed.

Time-bounding enables confidence in long-lived constructs.

---

## Validity Evidence

Validity claims require evidence:

- Validation report (from automated validator) ;
- Review record (from manual review) ;
- Test case coverage (from test suite) ;
- Audit trail (from system activity).

Evidence links validity claims to validation actions.

---

## Validity Reporting

Validity status is reported through:

- Concept metadata (`status` field) ;
- Assertion metadata (`validity` field) ;
- API responses (with validity info) ;
- Dashboards (with validity trends).

---

## Validity vs Lifecycle Status

Validity is distinct from lifecycle status:

| Aspect | Validity | Lifecycle Status |
|---|---|---|
| Purpose | Rule conformance | Stage in lifecycle |
| Evaluated by | Validation engine | Governance process |
| Affects | Trust in construct | Use of construct |
| Example | Invalid (fails rule) | Deprecated (withdrawn) |

A construct can be valid but deprecated, or invalid but active.

---

## Canonical Examples

```yaml
# Valid assertion
- assertion:
    subject: wsf-ex:OTCHERE-Inc
    predicate: wsf-rel:possesses
    object: wsf:Capability
    validity: Valid
    evidence: validation-report-12345

# Invalid assertion (with reason)
- assertion:
    subject: wsf-ex:UnknownEntity
    predicate: wsf-rel:possesses
    object: wsf:Capability
    validity: Invalid
    invalidity_reason: subject_identifier_not_registered

# Time-bounded validity
- assertion:
    subject: wsf-ex:OTCHERE-Inc
    predicate: wsf-rel:registeredIn
    object: jurisdiction:US-DE
    validity: Valid
    valid_from: 2026-01-01
    valid_until: 2026-12-31
```

---

## Cross-References

- ADR-WSF-13 : Semantic Constraints and Validation
- ADR-WSF-22 : Assertion and Provenance Model (truth vs validity distinction)
- wsf:State : the parent construct
- wsf:Evidence : supports validity claims

---

*Validity is a Tier 2 supporting construct. Status: Baseline.*