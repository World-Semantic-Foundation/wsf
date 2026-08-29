# Identifier

> **A stable, persistent, machine-readable label that uniquely references a single concept across all representations, contexts, and time.**

## Semantic Identity

```yaml
semantic_id: wsf:Identifier
preferred_name: Identifier
aliases: [IRI, URI, CURIE, ID]
status: Baseline
version: 0.1.0
classification: Tier 2 (Supporting Construct)
parent: wsf:Identity
defined_by: ADR-WSF-18, ADR-WSF-21
authority: WSF
```

---

## Definition

An **Identifier** is a stable, persistent, machine-readable label that uniquely references a single concept in the semantic graph. Identifiers follow the conventions established in ADR-WSF-21 (Namespace and Reference Model) and persist across representation changes per ADR-WSF-18 (Concept Identity).

An Identifier is NOT:
- A natural language name (use Term for that) ;
- A version marker (versions are tracked separately) ;
- A display label (use preferred_name or alias for display) ;
- A temporary handle or session reference.

---

## Identifier Forms

WSF supports four identifier forms:

### IRI (Internationalized Resource Identifier)

The canonical machine-readable form:

- Full URI with optional international characters ;
- Used in JSON-LD `@id`, Turtle subject URIs, RDF/XML resource references ;
- Format: `<scheme>:<hierarchical-part>[:<query>][#<fragment>]`.

### CURIE (Compact URI)

The shorthand machine-readable form:

- Prefix-suffix structure: `prefix:suffix` ;
- Prefix resolves to a namespace URI (per Namespace construct) ;
- Format: `[prefix]:[suffix]` where prefix is registered.

### Bare Identifier

The local-only form:

- A simple local name without namespace prefix ;
- Used within a single namespace context ;
- Resolves to full IRI within that context only.

### Content-Addressed Identifier

The cryptographic form:

- Hash of canonical representation (SHA-256 or stronger) ;
- Provides tamper-evidence and deduplication ;
- Format: `urn:sha256:<hash>`.

---

## Identifier Structure

A canonical WSF identifier has three components:

| Component | Required | Purpose |
|---|---|---|
| Scheme | Yes | Protocol or context (`wsf:`, `wsf-rel:`, `urn:`, `http:`) |
| Namespace | Yes | Authoritative source organisation |
| Local name | Yes | Unique name within namespace |
| Version marker | Optional | Distinguishes versions of the same concept |
| Fragment | Optional | Sub-concept reference |

---

## Identifier Schemes

### `wsf:` Scheme

Authoritative WSF foundational concepts:

- `wsf:Entity`, `wsf:Capability`, `wsf:Disposition` ;
- Managed by WSF governance ;
- Stable across all representations.

### `wsf-rel:` Scheme

Authoritative WSF relationship types:

- `wsf-rel:hasPart`, `wsf-rel:specializes`, `wsf-rel:asserts` ;
- Namespaced to distinguish from concept identifiers ;
- Managed by WSF governance.

### `wsf-cap:` Scheme

Authoritative WSF foundational capabilities:

- `wsf-cap:OrderFulfillment`, `wsf-cap:CustomerManagement` ;
- Reserved for Capability-type concepts ;
- Managed by WSF governance.

### `wsf-ctx:` Scheme

Authoritative WSF context markers:

- `wsf-ctx:enterprise`, `wsf-ctx:technical`, `wsf-ctx:operational` ;
- Distinguishes contextual application of concepts.

### `wsf-ex:` Scheme

Example identifiers:

- `wsf-ex:OTCHERE-Inc`, `wsf-ex:Kwesi`, `wsf-ex:OTCHERE-DC-01` ;
- Reserved for canonical examples ;
- Never used in production data.

---

## Identifier Lifecycle

Identifiers evolve under governance:

1. **Request** : requestor proposes identifier ;
2. **Validation** : governance validates uniqueness and conformance ;
3. **Registration** : identifier registered in authoritative registry ;
4. **Activation** : identifier becomes referenceable ;
5. **Use** : consumers reference the identifier ;
6. **Versioning** : identifier MAY carry version marker ;
7. **Retirement** : identifier deprecated, never re-used ;
8. **Archive** : identifier remains resolvable for historical references.

---

## Identifier Stability Rules

### Rule 1 : Never Re-Use

A retired identifier SHALL NOT be re-used for a different concept. This prevents reference ambiguity in historical data.

### Rule 2 : Persistent Resolution

An identifier SHALL remain resolvable for at least as long as any reference to it exists.

### Rule 3 : Stable Through Evolution

A concept may evolve (new attributes, new relationships, refined definition) while retaining its identifier.

### Rule 4 : Version Explicit

When a concept undergoes breaking change, the new version SHALL declare a new identifier (e.g., `wsf:Capability:v2`).

### Rule 5 : Namespace Authority

Each identifier belongs to exactly one namespace authority. Cross-namespace use requires explicit federation agreement.

---

## Identifier Conflicts

When two authorities propose the same identifier:

1. **Priority** : earlier registration wins ;
2. **Negotiation** : conflicting authorities negotiate distinction ;
3. **Disambiguation** : if needed, suffixes or prefixes distinguish ;
4. **Documentation** : conflict resolution recorded in governance.

---

## Identifier Validation

Validation rules:

- Conforms to URI/CURIE syntax ;
- Registered namespace prefix (or full IRI scheme) ;
- Local name contains only permitted characters ;
- Total length within reasonable bounds (≤ 200 characters) ;
- No collisions with existing identifiers ;
- Authority is recognised.

---

## Canonical Examples

```yaml
# Foundational concept identifier
- identifier: wsf:Capability
  type: concept
  authority: WSF

# Relationship identifier
- identifier: wsf-rel:hasPart
  type: relationship
  authority: WSF

# Specialised capability
- identifier: wsf-cap:OrderFulfillment
  type: capability
  authority: WSF
  parent: wsf:Capability

# Example identifier
- identifier: wsf-ex:OTCHERE-Inc
  type: example_entity
  authority: WSF
  domain: examples
```

---

## Cross-References

- ADR-WSF-18 : Concept Identity (identifier stability rules)
- ADR-WSF-21 : Namespace and Reference Model (identifier schemes)
- wsf:Identity : the parent concept that Identifier supports
- wsf:Namespace : the organisational unit of identifier registration

---

*Identifier is a Tier 2 supporting construct. Status: Baseline.*