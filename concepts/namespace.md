# Namespace

> **A governed administrative scope that groups related identifiers under a common authority, enabling prefix-based shorthand (CURIE) and federation across independent semantic ecosystems.**

## Semantic Identity

```yaml
semantic_id: wsf:Namespace
preferred_name: Namespace
aliases: [Prefix Scope, Identifier Domain]
status: Baseline
version: 0.1.0
classification: Tier 2 (Supporting Construct)
parent: wsf:Context
defined_by: ADR-WSF-21
authority: WSF
```

---

## Definition

A **Namespace** is a governed administrative scope that groups related identifiers under a common authority. Namespaces enable prefix-based shorthand (CURIE notation), support federation of independent semantic ecosystems, and prevent identifier collisions across organisational boundaries.

A Namespace is NOT:
- A physical storage boundary (namespaces are administrative, not technical) ;
- A security boundary (access control is independent of namespace) ;
- An ownership claim over concepts (only over identifiers).

---

## Namespace Structure

A canonical namespace has these components:

| Component | Required | Purpose |
|---|---|---|
| Prefix | Yes | Short identifier prefix (e.g., `wsf`) |
| IRI | Yes | Full IRI of namespace root (e.g., `https://world-semantic-foundation.org/ns/`) |
| Authority | Yes | Organisation responsible for namespace |
| Description | Optional | Human-readable description |
| Version | Optional | Namespace version |
| Registration date | Yes | When namespace was registered |
| Status | Yes | Lifecycle status (active, deprecated, retired) |

---

## Namespace Categories

### Authoritative Namespaces

Governed namespaces for foundational content:

- `wsf:` : WSF foundational concepts (managed by WSF governance) ;
- `wsf-rel:` : WSF relationship types (managed by WSF governance) ;
- `wsf-cap:` : WSF foundational capabilities (managed by WSF governance).

### Specialised Namespaces

Namespaces for specific domains or specialisations:

- `wsf-ctx:` : WSF context markers ;
- `wsf-ex:` : WSF canonical examples ;
- `wsf-gov:` : WSF governance artifacts.

### Federated Namespaces

Namespaces from peer organisations:

- `opendea:` : OpenDEA enterprise semantics (federated) ;
- `tmforum:` : TM Forum ontology (federated) ;
- `schema:` : Schema.org vocabulary (federated).

### Community Namespaces

Namespaces registered by independent parties:

- `org:` : Organisation-claimed namespaces ;
- `user:` : Individual-claimed namespaces (subject to verification).

---

## Namespace Registration

Namespaces are registered through governance:

1. **Proposal** : requestor submits namespace proposal with justification ;
2. **Conflict check** : governance checks for prefix collisions ;
3. **Authority validation** : governance validates the requesting authority ;
4. **Approval** : governance approves or rejects with rationale ;
5. **Publication** : approved namespace published in registry ;
6. **Activation** : namespace becomes available for identifier registration.

---

## Namespace Lifecycle

Namespaces evolve under governance:

1. **Proposed** : under governance review ;
2. **Active** : accepting identifier registrations ;
3. **Deprecated** : no new identifiers accepted, existing identifiers maintained ;
4. **Retired** : no maintenance, identifiers frozen ;
5. **Reclaimed** : namespace withdrawn and cannot be re-used.

---

## Namespace Federation

Federation enables cross-namespace interoperability:

### Federation Agreement

Two namespaces federate when:

- Both authorities agree to honour each other's identifiers ;
- Identifier resolution protocols are agreed ;
- Conflict resolution procedures are documented ;
- Versioning policies are compatible.

### Federation Discovery

Federated namespaces are discoverable through:

- Registry publication ;
- Peer-to-peer gossip ;
- Authority-curated federation directories.

### Federation Resolution

Cross-namespace references resolve via:

- Direct IRI expansion if known ;
- Registry lookup if namespace registered ;
- Federation peer request if federated ;
- Unresolved state if not findable.

---

## Namespace Ownership

Namespaces carry ownership semantics:

- Authority of record ;
- Contact information ;
- Update responsibility ;
- Discontinuation authority.

Ownership is irrevocable within the namespace's active lifecycle.

---

## Namespace Versioning

Namespaces MAY version:

- **Major version** : breaking changes to identifier schemes ;
- **Minor version** : additive identifier introductions ;
- **Patch version** : documentation and metadata changes.

Versioning affects:

- Identifier registration policy ;
- Resolution behaviour ;
- Federation compatibility.

---

## Namespace vs Vocabulary

A namespace provides identifier administration. A vocabulary provides concept definitions. They are related but distinct:

| Aspect | Namespace | Vocabulary |
|---|---|---|
| Purpose | Identifier administration | Concept cataloguing |
| Content | Identifiers + metadata | Concept definitions |
| Operation | Register, resolve | Define, classify |
| Granularity | Identifier-level | Concept-level |

A vocabulary may use one or more namespaces. A namespace may contain identifiers from multiple vocabularies.

---

## Canonical Examples

```yaml
# Authoritative WSF namespace
- namespace:
    prefix: wsf
    iri: https://world-semantic-foundation.org/ns/
    authority: WSF Governance
    status: Active
    registered: 2026-08-29

# Specialised WSF namespace
- namespace:
    prefix: wsf-rel
    iri: https://world-semantic-foundation.org/rel/
    authority: WSF Governance
    status: Active
    registered: 2026-08-29
    parent: wsf

# Federated namespace
- namespace:
    prefix: opendea
    iri: https://opendea.org/ns/
    authority: OpenDEA Governance
    status: Active
    federation: wsf
```

---

## Cross-References

- ADR-WSF-21 : Namespace and Reference Model (namespace governance)
- wsf:Identifier : uses namespaces for prefix-based shorthand
- wsf:Context : the parent construct
- wsf:Authority : governance body responsible for namespaces

---

*Namespace is a Tier 2 supporting construct. Status: Baseline.*