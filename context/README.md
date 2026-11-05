# WSF Context Module

> **Context as semantic qualification: context qualifies meaning, applicability, and interpretation; it is not a generic metadata container.**

Defined by ADR-WSF-14 (Semantic Context and Boundary, aliased into the foundational architecture per ADR-WSF-17) and exercised throughout ADR-WSF-19 (relationship context applicability) and ADR-WSF-22 (context in assertions).

---

## Semantic Identity

```yaml
semantic_id: wsf:Context
preferred_name: Context as Semantic Qualification
status: Baseline
version: 0.1.0
defined_by: ADR-WSF-14 (Semantic Context and Boundary)
classification: Foundational
domain: Semantics
```

---

## Governing Principle

> **Context qualifies meaning; it does not decorate it.**

The same subject-relationship-object triple MAY hold in one context and fail in another. Context is therefore a first-class qualifier in assertions and a validation dimension in relationships (ADR-WSF-19 §10, §13.5).

---

## Context Is NOT

- A generic metadata bag;
- A configuration store;
- An environment variable;
- A free-form tag set.

Context entries in WSF are governed vocabulary items in the `wsf-ctx:` namespace, with definitions and applicability rules.

---

## Context Applicability Model

```yaml
- context:
    semantic_id: wsf-ctx:enterprise-architecture
    preferred_name: Enterprise Architecture Context
    definition: The context of enterprise architecture practice
    applies_to:
      - wsf:Capability
      - wsf-rel:possesses
      - wsf-rel:governs
    not_applicable_in:
      - informal-context
    authority: WSF
```

Relationships declare their context applicability (ADR-WSF-19 §10):

```
wsf-rel:governs
   applies-in:
     - enterprise-context
     - regulatory-context
   not-applicable-in:
     - informal-context
```

---

## Initial Context Set

| Context | Qualifies |
|---|---|
| `wsf-ctx:enterprise-architecture` | Enterprise architecture concepts, structural and dispositional relationships |
| `wsf-ctx:operations` | Operational events, causal relationships, service states |
| `wsf-ctx:regulatory` | Policies, obligations, normative relationships |
| `wsf-ctx:organisational` | Roles, participation, governance |
| `wsf-ctx:informal` | Conversational, non-normative discourse (explicitly excluded from normative relationship applicability) |

---

## Context in Assertions

Assertions carry at most one primary context (ADR-WSF-22 §10):

```yaml
- assertion:
    subject: wsf-ex:OTCHERE-Inc
    relationship: wsf-rel:possesses
    object: wsf-ex:OrderManagementCapability
    context: wsf-ctx:enterprise-architecture
```

**Validation rule**: a relationship declared not-applicable-in a context MUST NOT be asserted in that context.

---

## Canonical Example

```yaml
# Holds in enterprise architecture context
- assertion:
    subject: wsf-ex:Kwesi
    relationship: wsf-rel:assumes-role
    object: wsf-ex:Enterprise-Architect-Role
    context: wsf-ctx:organisational

# Does NOT hold in regulatory context: the role is organisational, not regulatory
```

---

## Cross-References

- [Context concept](../concepts/context.md)
- ADR-WSF-14, ADR-WSF-19 §10, ADR-WSF-22 §10
- [Assertions module](../assertions/README.md)

---

*Status: Baseline. New contexts require governance approval.*
