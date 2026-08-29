# Reference

> **A directed, typed association from one concept to another, expressing a navigable semantic relationship that supports both graph traversal and targeted lookup.**

## Semantic Identity

```yaml
semantic_id: wsf:Reference
preferred_name: Reference
aliases: [Link, Pointer, Cross-Reference]
status: Baseline
version: 0.1.0
classification: Tier 2 (Supporting Construct)
parent: wsf:Relationship
defined_by: ADR-WSF-19, ADR-WSF-21
authority: WSF
```

---

## Definition

A **Reference** is a directed, typed association from a source concept to a target concept. References enable navigation across the semantic graph and express structured connections between concepts that are not themselves relationships in the ontological sense.

A Reference is NOT:
- A relationship in the semantic sense (use Relationship for that) ;
- A citation (use Evidence and Provenance for citations) ;
- An assertion about reality (use Assertion for that) ;
- An identifier (use Identifier for unique labels).

---

## Reference vs Relationship

| Aspect | Relationship | Reference |
|---|---|---|
| Nature | Ontological connection | Navigational link |
| Examples | `specializes`, `hasPart` | `see`, `definedIn`, `citedBy` |
| Authority | Semantic governance | Editorial/documentation |
| Required for meaning | Yes (semantic dependency) | No (navigation aid) |
| Affects truth | Yes | No |

---

## Reference Types

### Definition Reference

Points to the formal definition of a concept:

- `definedBy` : reference to the ADR or specification that defines the concept ;
- `documentedIn` : reference to documentation or specification ;
- `specifiedIn` : reference to the schema or shape definition.

### Provenance Reference

Points to attribution and history:

- `assertedBy` : reference to the entity that made the assertion ;
- `derivedFrom` : reference to the source of derivation ;
- `importedFrom` : reference to the external system of origin.

### Cross-Reference

Points to related concepts:

- `seeAlso` : reference to related concepts ;
- `predecessor` : reference to prior version or concept ;
- `successor` : reference to subsequent version or concept.

### Editorial Reference

Points to editorial or organisational metadata:

- `discussedIn` : reference to discussion thread or meeting ;
- `decidedIn` : reference to governance decision record ;
- `reviewedIn` : reference to review record.

---

## Reference Structure

A canonical reference has these components:

| Component | Required | Purpose |
|---|---|---|
| Source | Yes | Concept making the reference |
| Target | Yes | Concept being referenced |
| Type | Yes | Reference type (from controlled vocabulary) |
| Cardinality | Optional | One-to-one, one-to-many constraints |
| Context | Optional | Conditions under which reference applies |
| Provenance | Optional | Attribution metadata |

---

## Reference Cardinality

References support cardinality constraints:

- `1..1` : exactly one target
- `0..1` : zero or one target
- `1..*` : at least one target
- `0..*` : zero or more targets

Cardinality violations produce validation failures.

---

## Reference Directionality

All references are directed:

- Source → Target ;
- Direction encodes meaning (e.g., `assertedBy` differs from `asserts`) ;
- Inverse relationships are explicit (not implied) ;
- Bidirectional references are two distinct references with inverse types.

---

## Reference Context

References MAY carry context:

- Time-bounded references (only valid within a date range) ;
- Conditional references (only valid under specified conditions) ;
- Domain-bounded references (only valid in specified domains).

Context-aware references are evaluated dynamically per ADR-WSF-14 (Semantic Context and Boundary).

---

## Reference Resolution

Resolution paths for references:

### Direct Resolution

Target identifier resolves directly to a concept.

### Indirect Resolution

Reference goes through intermediary:

- Reference chains ;
- Federation hops ;
- Versioned references.

### Unresolved References

References MAY be temporarily unresolved:

- Target concept not yet defined ;
- Federation peer unavailable ;
- Authority under review.

Unresolved references are tracked and reported.

---

## Reference Validation

Validation rules:

- Source and target are valid identifiers ;
- Type is from the controlled vocabulary ;
- Cardinality constraints satisfied ;
- Context constraints satisfied (if specified) ;
- Inverse reference consistency (if both directions exist) ;
- No circular references (for non-recursive reference types).

---

## Reference vs Identifier

| Aspect | Identifier | Reference |
|---|---|---|
| Purpose | Uniquely label a concept | Connect concepts |
| Arity | Unary (one concept) | Binary (source + target) |
| Authority | Owning namespace | Multiple authorities |
| Cardinality | One per concept | Multiple per source |

---

## Canonical Examples

```yaml
# Definition reference
- reference:
    source: wsf:Capability
    type: definedBy
    target: wsf-governance:ADR/ADR-WSF-07

# Provenance reference
- reference:
    source: assertion:12345
    type: assertedBy
    target: wsf-ex:OTCHERE-Inc

# Cross-reference
- reference:
    source: wsf:Entity
    type: seeAlso
    target: wsf:Role
```

---

## Cross-References

- ADR-WSF-19 : Semantic Relationship Model (relationship types)
- ADR-WSF-21 : Namespace and Reference Model (reference schemes)
- wsf:Relationship : the parent construct
- wsf:Identifier : labels concepts referenced

---

*Reference is a Tier 2 supporting construct. Status: Baseline.*