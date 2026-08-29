# Identity

> **The semantic property by which an Entity or Concept is distinguishable as the same Entity or Concept across contexts, time, and representations.**

---

## Semantic Identity

```yaml
semantic_id: wsf:Identity
preferred_name: Identity
aliases: [Semantic Identity, Distinguishability]
status: Normative
version: 1.0.0
classification: Tier 1 (Foundational)
parent: wsf:Disposition
authority: WSF
```

---

## Definition

**Identity** is the semantic property that allows an Entity or Concept to be recognized as the same Entity or Concept across different contexts, times, representations, and assertions.

Identity is NOT:
- A name (names can change);
- A label (labels can be ambiguous);
- A representation (representations can be transformed);
- A location (locations can change);
- A version (versions evolve while identity persists).

Identity IS:
- The persistent "this-ness" that distinguishes X from not-X;
- Surviving representation changes;
- Surviving context changes (where appropriate);
- Surviving version evolution (per ADR-WSF-16);
- Surviving naming/labeling changes.

---

## Two Distinct Notions of "Identity"

WSF recognizes that "Identity" can mean different things. This ADR governs the broader semantic concept of Identity. Concept Identity (governed by ADR-WSF-18) is the application of Identity to semantic concepts specifically.

| Notion | Scope | Governed By |
|---|---|---|
| **Identity** (this concept) | All semantic artifacts | This ADR (proposed) |
| **Concept Identity** | Concepts specifically | ADR-WSF-18 |

---

## Why Identity Is Foundational

Identity is foundational because:

1. **Reference requires distinguishability** — to say "OTCHERE Inc", one must be able to distinguish it.
2. **Assertions require stable subjects** — "OTCHERE possesses Capability X" requires stable identity of OTCHERE.
3. **Evolution requires persistence** — concepts evolve while maintaining identity (per ADR-WSF-16).
4. **Integration requires resolution** — cross-system references resolve to identities.
5. **Provenance requires attribution** — provenance links assertions to their origin (requires identity).

Without Identity, semantic claims become unanchored.

---

## Identity Dimensions

WSF distinguishes the following identity dimensions:

### 1. Identity by Meaning

The core identity for Concepts — a Concept is identified by what it means.

Example: `wsf:Capability` is identified as "the concept of grounded potential".

### 2. Identity by Stable Reference

The core identity for Entities — an Entity is identified by a stable reference (e.g., a persistent identifier).

Example: `OTCHERE Inc` is identified by registration, name, or assigned ID.

### 3. Identity by Role

An Entity may have a different identity in different roles.

Example: Kwesi the Person vs Kwesi the Enterprise Architect.

### 4. Identity by Context

An Entity may be the same across contexts but identified differently.

Example: The same person in OTCHERE and in OpenDEA.

### 5. Identity by Time

Identity may persist through time but be qualified by temporal validity.

Example: "OTCHERE Inc" exists since incorporation, but its legal form changes.

---

## Identity vs Naming (Critical Distinction)

| Aspect | Identity | Name |
|---|---|---|
| **Nature** | Semantic property | Label |
| **Stability** | Stable (per ADR-WSF-16) | Mutable |
| **Uniqueness** | Unique by construction | May collide |
| **Resolution** | Resolves to the entity/concept | May be ambiguous |
| **Persistence** | Persists through evolution | Changes freely |
| **Machine handling** | Resolvable | Lookup table required |

A name is a way to refer to an identity; identity is what the name refers to.

---

## Identity Resolution

Identity SHALL be resolvable:

```
Reference → Identity Resolution Service → Entity/Concept
```

Resolution methods:

1. **Direct lookup**: Known identity → entity/concept
2. **Name resolution**: Name → identity (with disambiguation)
3. **Alias resolution**: Alias → identity
4. **Cross-namespace mapping**: External identity → WSF identity
5. **Version-aware lookup**: Identity + version → specification

---

## Identity Persistence Through Change

| Change Type | Identity Behavior |
|---|---|
| Name change | Identity persists |
| Alias added | Identity persists |
| Alias removed | Identity persists |
| Representation change | Identity persists |
| Context change (compatible) | Identity persists |
| Scope change (compatible) | Identity persists |
| Semantic clarification | Identity persists |
| Semantic correction (intended meaning restored) | Identity persists |
| Semantic extension | Identity persists |
| Semantic breaking change | New identity; old deprecated |
| Identity-changing transformation | New identity |

---

## Identity and Specialization

When a concept is specialized:

```
wsf:Capability (parent identity)
   ↓ specializes
wsf:BusinessCapability (child identity — new)
```

- The parent retains its identity;
- The child receives its own identity;
- The child's identity MUST reference the parent's identity through a `specializes` relationship.

This ensures:
- Parent-child relationships are traceable;
- Specialization cannot be silent;
- Each concept has a unique identity.

---

## Identity and Time

Identity may be qualified by time:

```yaml
- entity: OTCHERE Inc
  identity: wsf-id:OTCHERE-Inc-stable-id
  temporal:
    exists_since: 2014-01-01
    exists_until: open-ended
  forms:
    - form: Corporation
      valid_from: 2014-01-01
      valid_until: present
```

The identity persists; the temporal validity may change.

---

## Identity and Provenance

Identity includes provenance attribution:

```yaml
- identity: wsf-id:OTCHERE-Inc-stable-id
  provenance:
    assigned_by: WSF
    asserted_by: OTCHERE Inc Architecture Team
    authority: OTCHERE Inc Board
    created_at: 2026-08-29
```

This enables tracking of who established the identity.

---

## Identity and Trust

Identity may carry trust assessments:

```yaml
- identity: wsf-id:unknown-entity-12345
  trust:
    level: Provisional
    basis: External claim, no independent verification
```

Trust distinguishes:
- Authoritatively identified entities (high trust);
- Provisionally identified entities (lower trust);
- Disputed identities (needs resolution);
- Unknown identities (requires investigation).

---

## Identity Metadata Schema

Every Identity SHALL carry:

```yaml
identity:
  semantic_id: wsf:<id>              # The stable identity
  type: Concept | Entity | Relationship | Assertion | Context | etc.
  preferred_name: Human-readable name
  aliases: [Alternative names]
  status: Candidate | Investigating | Proposed | Normative | Deprecated | Retired
  version: Semantic Version
  authority: Governance authority
  parent: Parent identity (if specialized)
  context_applicability: List of applicable contexts
  temporal_validity:
    exists_since: ISO timestamp
    exists_until: ISO timestamp or open-ended
  created: ISO timestamp
  last_modified: ISO timestamp
  superseded_by: New identity (if deprecated)
  provenance:
    source: Where the identity originated
    asserted_by: Who established it
    authority: Governance authority
```

---

## Identity in Semantic Assertions

Identity is essential for assertions:

```yaml
- assertion:
  subject:
    identity: wsf-id:OTCHERE-Inc-stable-id   # Identity of subject
  relationship:
    identity: wsf-rel:possesses             # Identity of relationship
  object:
    identity: wsf-cap:OTCHERE-OrderFulfillment  # Identity of object
  context:
    identity: wsf-ctx:enterprise            # Identity of context
```

Without identity, assertions cannot be unambiguously made.

---

## Related Concepts

- [Entity](./entity.md) — The concrete things that have identity
- [Concept](./concept.md) — The abstract ideas that have identity
- [Capability](./capability.md) — A concept with identity
- [Disposition](./disposition.md) — Identity of tendencies/potentials

---

## Related ADRs

- ADR-WSF-18 — Concept Identity (the application of Identity to concepts)
- ADR-WSF-10 — Semantic Identity & Naming
- ADR-WSF-16 — Semantic Evolution & Versioning
- ADR-WSF-21 — Namespace and Reference Model (forthcoming)

---

## Cross-Repository References

- Canonical semantic asset: [wsf/concepts/identity.md](https://github.com/World-Semantic-Foundation/wsf/blob/main/concepts/identity.md)
- ADR-WSF-18: [wsf-governance/ADR/ADR-WSF-18-Concept-Identity.md](https://github.com/World-Semantic-Foundation/wsf-governance/blob/main/ADR/ADR-WSF-18-Concept-Identity.md)
