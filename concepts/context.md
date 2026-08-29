# Context

> **A semantic frame that qualifies the applicability, interpretation, and validity of concepts, relationships, and assertions — the situational boundaries of meaning.**

---

## Semantic Identity

```yaml
semantic_id: wsf:Context
preferred_name: Context
aliases: [Semantic Context, Applicability Frame, Situational Boundary]
status: Normative
version: 1.0.0
classification: Tier 1 (Foundational)
parent: wsf:Entity
authority: WSF
```

---

## Definition

A **Context** is a semantic frame that qualifies the applicability, interpretation, and validity of concepts, relationships, and assertions — the situational boundaries of meaning.

A Context is NOT:
- A representation (contexts are semantic, not syntactic);
- A namespace (namespaces are identifiers; contexts are applicability);
- A physical setting alone (contexts can be abstract);
- A state (states are conditions; contexts are frames).

A Context IS:
- A qualification of meaning;
- An applicability boundary;
- An interpretation frame;
- A situational scope.

---

## Why Context Is Foundational

Context is foundational because:

1. **Meaning depends on context** — the same term can mean different things in different contexts;
2. **Assertions have context** — every assertion is made in a context;
3. **Specialization creates contexts** — enterprise context, regulatory context, etc.;
4. **Validation requires context** — assertions may be valid in some contexts but not others;
5. **Integration requires shared contexts** — integration requires understanding contextual applicability.

Without Context, we cannot distinguish "Capability in general" from "Business Capability in enterprise context".

---

## Context Types

WSF distinguishes several kinds of Context:

### 1. Universal Context

Applies to all semantic artifacts in all situations.

Example: The fundamental semantic definitions.

### 2. Domain Context

Applies within a domain (e.g., enterprise, healthcare, finance).

Example: Enterprise Architecture context applies to enterprise modeling.

### 3. Application Context

Applies within a specific application or system.

Example: OTCHERE Inc internal context.

### 4. Temporal Context

Applies within a time period.

Example: Q3 2026 context.

### 5. Regulatory Context

Applies under specific regulations.

Example: GDPR context.

### 6. Cultural Context

Applies within cultural settings.

Example: Western business context.

### 7. Technical Context

Applies within technical constraints.

Example: Mobile context (vs desktop).

---

## Context Dimensions

Context has multiple dimensions:

```yaml
- context:
  semantic_id: wsf-ctx:<id>
  name: <human-readable name>
  
  dimensions:
    time:
      period: <time period>
    space:
      region: <geographic region>
    domain:
      field: <domain>
    application:
      system: <application>
    perspective:
      viewpoint: <viewpoint>
    authority:
      scope: <authority scope>
    language:
      primary: <language>
  
  applicability:
    universal: boolean
    specific_to: [<list of applicable contexts>]
  
  governs: [<concepts/relationships/assertions governed>]
  
  status: Candidate | Investigating | Proposed | Normative
  version: <semantic version>
  authority: <governance authority>
```

---

## Context in Semantic Assertions

Assertions are made in contexts:

```yaml
- assertion:
  ...
  context: wsf-ctx:enterprise-architecture
```

This means: "This assertion applies in the enterprise-architecture context."

An assertion may be valid in one context but not in another.

---

## Context vs Specialization

| Aspect | Context | Specialization |
|---|---|---|
| **Purpose** | Applicability frame | Semantic refinement |
| **Effect** | Limits where meaning applies | Creates more specific meaning |
| **Example** | Enterprise context | Business Capability |
| **Inheritance** | Contexts don't inherit | Specializations inherit |

A concept can be specialized within a context. The specialized meaning applies in that context.

---

## Context Boundaries

Context has explicit boundaries:

```yaml
- context_boundary:
  context: wsf-ctx:enterprise
  applies_to:
    - <concept>
    - <relationship>
    - <assertion>
  does_not_apply_to:
    - <concept>
  boundary_type: domain | temporal | spatial | authority
```

Boundaries are explicit, not implicit.

---

## Context Specialization

Contexts MAY be specialized:

```
wsf-ctx:universal (parent)
   ↓ specializes
wsf-ctx:enterprise (child)
   ↓ specializes
wsf-ctx:enterprise-architecture (grandchild)
   ↓ specializes
wsf-ctx:enterprise-architecture-OTCHERE-Inc
```

Context specialization follows Concept specialization rules.

---

## Context Inheritance

When a context is inherited, all child concepts inherit the context:

```
wsf-ctx:enterprise
   ├── wsf-concept:BusinessCapability (inherits enterprise context)
   ├── wsf-concept:EnterpriseSystem (inherits enterprise context)
   └── wsf-concept:EnterpriseProcess (inherits enterprise context)
```

Children inherit their parent's context.

---

## Context-Specific Definitions

Concepts MAY have context-specific definitions:

```yaml
- concept_definition:
  semantic_id: wsf-concept:Capability
  universal_definition: <general definition>
  
  context_specific_definitions:
    wsf-ctx:enterprise: "Capability in enterprise context — bounded by enterprise value"
    wsf-ctx:technical: "Capability in technical context — bounded by technical feasibility"
    wsf-ctx:operational: "Capability in operational context — bounded by operational capacity"
```

The universal definition is preserved; contexts add specificity.

---

## Context vs Perspective

A context is the frame; a perspective is the viewpoint within the frame.

```
Context: Enterprise Architecture
   ├── Perspective: Business View
   ├── Perspective: Application View
   └── Perspective: Technology View
```

Both are needed; they serve different purposes.

---

## Context vs Namespace

| Aspect | Context | Namespace |
|---|---|---|
| **Purpose** | Applicability | Identifier organization |
| **Effect** | Limits where meaning applies | Organizes identifiers |
| **Example** | Enterprise context | wsf: namespace |
| **Independent of** | Identifiers | Applicability |

Namespaces organize identifiers; contexts organize applicability.

---

## Context Identity

Context has its own identity (per ADR-WSF-18):

```yaml
context:
  semantic_id: wsf-ctx:enterprise-architecture
  version: 1.0.0
```

This persists through compatible evolution.

---

## Context Lifecycle

Contexts follow the lifecycle:

```
Candidate → Investigating → Proposed → Normative → Deprecated → Retired
```

A context MAY be deprecated when no longer relevant.

---

## Context Examples

### Enterprise Context

```yaml
- context:
  semantic_id: wsf-ctx:enterprise
  name: Enterprise Context
  description: The context of enterprise operations and architecture
  dimensions:
    domain: enterprise
    perspective: business + technical
  governs:
    - wsf-concept:BusinessCapability
    - wsf-concept:EnterpriseSystem
    - wsf-concept:EnterpriseProcess
```

### OTCHERE Inc Internal Context

```yaml
- context:
  semantic_id: wsf-ctx:OTCHERE-Inc
  name: OTCHERE Inc Internal Context
  description: The internal context of OTCHERE Inc's operations
  dimensions:
    domain: enterprise
    application: OTCHERE Inc
  parent_context: wsf-ctx:enterprise
  governs:
    - wsf-cap:OTCHERE-OrderFulfillment
    - wsf-cap:OTCHERE-CustomerService
```

### Regulatory Context

```yaml
- context:
  semantic_id: wsf-ctx:GDPR
  name: GDPR Regulatory Context
  description: The context of EU GDPR regulatory requirements
  dimensions:
    domain: regulatory
    space: EU
  governs:
    - Personal data handling
    - Data subject rights
    - Cross-border data transfer
```

---

## Context in WSF Architecture

Context operates across the entire WSF semantic stack:

```
World Reality
   ↓ (universal context)
WSF Foundational Semantics
   ↓ (WSF context)
Semantic Architecture
   ↓ (semantic architecture context)
Ontology Architecture
   ↓ (ontology context)
Enterprise Semantics
   ↓ (enterprise context)
OpenDEA
   ↓ (OpenDEA context)
Architecture Instance
```

Each level has its own context; meanings are preserved across them.

---

## Context Validation

Contexts SHALL be validated for:

1. **Identity validity**: Has a stable semantic identity.
2. **Dimension completeness**: Relevant dimensions are specified.
3. **Boundary explicitness**: Boundaries are explicit.
4. **Applicability definition**: Where the context applies is defined.
5. **Specialization consistency**: Children are consistent with parent.

---

## Related Concepts

- [Entity](./entity.md) — Things in contexts
- [Concept](./concept.md) — Concepts in contexts
- [Capability](./capability.md) — Capabilities specialized in contexts
- [Assertion](./assertion.md) — Assertions made in contexts

---

## Related ADRs

- ADR-WSF-14 — Semantic Context & Boundary
- ADR-WSF-09 — Foundational Concept Taxonomy
- ADR-WSF-12 — Semantic Assertion Model

---

## Cross-Repository References

- Canonical semantic asset: [wsf/concepts/context.md](https://github.com/World-Semantic-Foundation/wsf/blob/main/concepts/context.md)
