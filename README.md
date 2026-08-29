# WSF Canonical Semantic Foundation

> **The authoritative home for WSF's foundational semantic assets.**

This repository (`wsf/`) contains the canonical semantic definitions, relationships, identity, assertions, context, temporal, spatial, and provenance foundations that constitute the World Semantic Foundation.

---

## Repository Structure

```
wsf/
├── README.md (this file)
├── concepts/         ← Tier 1 (12) + Tier 2 (9) + Tier 3 (16+) concept definitions
├── relationships/    ← 4 Forms of Relation + specialized relationships
├── identity/         ← Identity/Reference/Representation distinctions
├── assertions/       ← Semantic Assertion Model
├── context/          ← Context as semantic qualification
├── temporal/         ← Time semantics (Instant/Interval/Duration)
├── spatial/          ← Space semantics (Location/Position/Region)
└── provenance/       ← Evidence/Provenance/Authority/Trust
```

---

## What Lives Here

### `concepts/` ; Foundational Concept Definitions

The 12 Tier 1 foundational concepts and 9 Tier 2 supporting constructs. Each concept has:
- Unique Semantic Identity (URI)
- Preferred Name
- Definition
- Classification (per ADR-WSF-09)
- Relationships to other concepts
- Constraints
- Scope and Context considerations
- Canonical examples (OTCHERE/Kwesi)

### `relationships/` ; Foundational Relationships

The 4 Forms of Relation (Structural / Temporal / Causal / Dispositional) plus the 10 relationship families (Identity, Possession, Participation, Realization, Enablement, Provision, Constraint, Measurement, Causality, Context).

### `identity/` ; Identity/Reference/Representation

Distinguishes Identity, Identifier, Name, Reference, Representation. Implements the 5 distinctions from Investigation 6.

### `assertions/` ; Semantic Assertion Model

The Subject + Relationship + Object + Context + Time + Space + Condition + Evidence + Provenance + Trust pattern. See ADR-WSF-12.

### `context/` ; Context as Semantic Qualification

Context qualifies meaning, applicability, interpretation ; not a generic metadata container.

### `temporal/` ; Time Semantics

Instant, Interval, Duration. Precedence ≠ Causality. Temporal Validity ≠ Lifecycle.

### `spatial/` ; Space Semantics

Location, Position, Spatial Region. Position ≠ Location.

### `provenance/` ; Evidence, Provenance, Authority, Trust

The 4 epistemic qualifiers for assertions.

---

## Conventions

### Naming

- **Files**: `kebab-case.md` for documents, `snake_case.yaml` for machine-readable
- **Concepts**: PascalCase for the canonical name, lowercase for files
- **Examples**: Always OTCHERE Inc (or OTCHERE) and Kwesi : never ACME

### Frontmatter

Every concept file includes:

```yaml
---
semantic_id: <URI>
preferred_name: <Canonical Name>
status: Candidate | Investigating | Proposed | Normative | Deprecated | Retired
version: <semver>
defined_by: <ADR-WSF-XX>
classification: <Foundational | Supporting | Derived>
domain: <14 Foundational Domains>
last_reviewed: <YYYY-MM-DD>
---
```

### Canonical Examples

All examples use:

- **Enterprise**: OTCHERE Inc
- **Individual**: Kwesi
- **System**: OTCHERE DC-01 (data center example)

---

## Current Status

This repository is being established per CR-WSF-17 Rev.1. Initial concept definitions are being authored under subsequent ADRs (ADR-WSF-18 through ADR-WSF-22).

**Initial 12 Tier 1 Foundational Concepts** (all status: Proposed):
1. Entity
2. Concept
3. Relationship
4. Event
5. State
6. Disposition
7. Proposition
8. Assertion
9. Identity
10. Context
11. Time
12. Space

**Initial 9 Tier 2 Supporting Constructs**:
1. Identifier
2. Reference
3. Namespace
4. Term
5. Definition
6. Validity
7. Evidence
8. Provenance
9. Authority

---

## How to Contribute

1. Read the [12 Foundational Principles](../../wsf-docs/conceptual/FOUNDATIONAL-PRINCIPLES.md)
2. Read the [Investigation Record](../../wsf-governance/RESEARCH/INVESTIGATION-RECORD.md)
3. Read relevant ADRs in `wsf-governance/ADR/`
4. Propose new concepts/relationships via the [ADR Template](../../wsf-governance/templates/ADR-TEMPLATE.md)
5. Use canonical examples (OTCHERE/Kwesi)

---

## Related Repositories

- [wsf-spec/](../wsf-spec/) : Normative specifications
- [wsf-governance/](../wsf-governance/) : ADRs, CRs, governance
- [wsf-examples/](../wsf-examples/) : Reference applications
- [wsf-software/](../wsf-software/) : Semantic Engine implementation
- [wsf-docs/](../wsf-docs/) : Conceptual documentation
- [wsf-connectors/](../wsf-connectors/) : Integration adapters
- [wsf-visuals/](../wsf-visuals/) : Visual semantic assets

---

*This is the canonical semantic foundation of WSF. Changes occur only through the ADR/CR process.*
