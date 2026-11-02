# The WSF Identifier Scheme

> **Rules for identifiers, namespaces, and CURIEs: how references to identities are formed and resolved.**

Per ADR-WSF-21 (Namespace and Reference Model) §4-9.

---

## Semantic Identity

```yaml
semantic_id: wsf:IdentifierScheme
preferred_name: WSF Identifier Scheme
status: Baseline
version: 0.1.0
defined_by: ADR-WSF-21 (Namespace and Reference Model)
classification: Foundational
domain: Identity
```

---

## WSF Namespace Hierarchy

```
wsf:              Concept vocabulary (wsf:Entity, wsf:Capability, ...)
wsf-rel:          Relationship vocabulary (wsf-rel:possesses, ...)
wsf-ctx:          Context vocabulary (wsf-ctx:enterprise-architecture, ...)
wsf-assertion:    Individual assertions
wsf-evidence:     Individual evidence items
wsf-id:           Concrete identity representations (identifiers)
wsf-ex:           Canonical example namespace (OTCHERE Inc, Kwesi)
```

Namespaces are governed (ADR-WSF-21 §7): creating a namespace requires governance authority approval; namespaces carry owner, purpose, and version metadata.

---

## Identifier Syntax

Identifiers within WSF namespaces SHALL:

1. Use PascalCase for concept local names (`Capability`, `OrderManagementCapability` is an example local name);
2. Use kebab-case for instance local names (`OTCHERE-Inc`, `Order-Received-Event`);
3. Be stable once assigned (per identity persistence rules);
4. Not embed version (rejected alternative, ADR-WSF-21 §18 E);
5. Not embed location or representation.

---

## CURIEs (Compact URIs)

WSF uses CURIEs per ADR-WSF-21 §6:

```
<prefix>:<local>
wsf:Capability
wsf-rel:possesses
wsf-ex:OTCHERE-Inc
```

The prefix expands to the namespace URI; the local name is the identifier within the namespace. CURIEs are the canonical machine-readable reference form in YAML and Markdown artifacts; full URIs are used in RDF serializations.

---

## Identifier Assignment Rules

1. Identifiers are assigned once and never reused;
2. Superseded identifiers retain their identity with status Superseded and a `supersedes`/`superseded_by` chain;
3. Identifier assignment is recorded with provenance;
4. Federated namespaces follow ADR-WSF-21 §11 (Federated Namespaces): the peer namespace governs its own identifiers; cross-namespace references use the peer prefix.

---

## Reference Resolution

Reference resolution (ADR-WSF-21 §9) proceeds:

1. Expand the CURIE prefix to its namespace;
2. Locate the identifier within the namespace;
3. Return the identity and its current semantic specification;
4. If the identity is Superseded or Retired, return the successor chain.

Unresolvable references are semantic defects and SHALL be surfaced, not silently dropped.

---

## Cross-References

- [Identity Model](./identity-model.md)
- [Identity Lifecycle](./identity-lifecycle.md)
- ADR-WSF-21
