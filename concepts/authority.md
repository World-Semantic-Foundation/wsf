# Authority

> **The recognised right and capability of an entity to make, modify, validate, or retire semantic assertions within a specified domain, under governed rules.**

## Semantic Identity

```yaml
semantic_id: wsf:Authority
preferred_name: Authority
aliases: [Authoritative Body, Governance Authority]
status: Baseline
version: 0.1.0
classification: Tier 2 (Supporting Construct)
parent: wsf:Context
defined_by: ADR-WSF-03, ADR-WSF-15, ADR-WSF-22
authority: WSF
```

---

## Definition

**Authority** is the recognised right and capability of an entity to make, modify, validate, or retire semantic assertions within a specified domain, under governed rules. Authority is the source of weight and trust in the semantic ecosystem per ADR-WSF-03 and ADR-WSF-15.

Authority is NOT:
- Power (authority is governed, not asserted) ;
- Ownership (authority concerns assertions, not concepts as objects) ;
- Permanence (authority can be granted, modified, revoked) ;
- Universal (authority is domain-bounded).

---

## Authority Types

### Foundational Authority

Authority over world-level semantic foundations:

- Establishes foundational concepts ;
- Defines identity schemes ;
- Sets validation rules ;
- Examples: WSF Governance Body.

### Domain Authority

Authority over a semantic domain:

- Defines domain concepts ;
- Validates domain assertions ;
- Maintains domain vocabulary ;
- Examples: Industry consortiums, standards bodies.

### Organisational Authority

Authority within an organisation:

- Defines organisational concepts ;
- Records organisational assertions ;
- Enforces organisational rules ;
- Examples: Enterprise architecture teams.

### Individual Authority

Authority vested in individuals:

- Authority to make specific assertions ;
- Authority to apply policies ;
- Authority to grant access ;
- Examples: System administrators, governance committee members.

### Delegated Authority

Authority granted by another authority:

- Subset of delegating authority's scope ;
- Subject to delegating authority's oversight ;
- Revocable by delegating authority ;
- Examples: Working groups, expert panels.

---

## Authority Scope

Authority has explicit scope:

### Domain Scope

The semantic domain over which the authority applies:

- Concept types covered ;
- Subject matter boundaries ;
- Use case applicability.

### Operational Scope

The actions the authority may take:

- Make assertions ;
- Modify assertions ;
- Validate assertions ;
- Retire assertions ;
- Grant sub-authority.

### Temporal Scope

The time period during which the authority is active:

- Authority grant date ;
- Authority expiry (if bounded) ;
- Renewal conditions.

---

## Authority Structure

A canonical authority record has these components:

| Component | Required | Purpose |
|---|---|---|
| Identifier | Yes | Unique reference for the authority |
| Type | Yes | Authority type (foundational, domain, etc.) |
| Scope | Yes | Domain, operational, temporal scope |
| Holder | Yes | Entity that holds the authority |
| Granting authority | Yes | Who granted the authority (except foundational) |
| Grant date | Yes | When authority was granted |
| Revocation terms | Yes | Conditions under which authority is revoked |
| Contact | Optional | How to reach the authority |

---

## Authority Delegation

Authority can be delegated:

- Delegating authority retains ultimate responsibility ;
- Delegated authority has restricted scope ;
- Delegation recorded with explicit terms ;
- Revocation follows defined procedure.

Delegation chain:

```
Foundational Authority (WSF)
    ↓ delegates
Domain Authority (OpenDEA)
    ↓ delegates
Organisational Authority (OTCHERE Inc)
    ↓ delegates
Individual Authority (Kwesi)
```

---

## Authority and Trust

Authority is the foundation of trust assessment:

- Authoritative source = high trust baseline ;
- Domain expertise = scope-appropriate authority ;
- Authority chain = trust propagation ;
- Authority revocation = trust loss.

Trust flows from authority, not the reverse.

---

## Authority and Provenance

Authority is recorded in provenance:

- Provenance carries authority reference ;
- Authority validates assertion attribution ;
- Authority enables trust assessment ;
- Provenance without authority is incomplete.

Authority in provenance establishes assertion weight.

---

## Authority Lifecycle

Authorities evolve through lifecycle stages:

1. **Proposed** : authority request under review ;
2. **Granted** : authority formally granted with documented scope ;
3. **Active** : authority in use, making assertions ;
4. **Suspended** : authority temporarily inactive (during review, dispute) ;
5. **Renewed** : authority re-granted after expiry ;
6. **Revoked** : authority formally withdrawn ;
7. **Historical** : authority retired, historical record retained.

---

## Authority Conflicts

When two authorities claim the same scope:

1. **Precedence rules** : foundational > domain > organisational > individual ;
2. **Domain specificity** : more specific domain authority wins ;
3. **Temporal precedence** : earlier grant wins (subject to overrides) ;
4. **Federation agreement** : cross-authority conflicts resolved by agreement ;
5. **Governance escalation** : unresolved conflicts escalate to higher authority.

---

## Authority and Namespace

Authority governs namespaces:

- Foundational authority governs foundational namespaces ;
- Domain authority governs domain namespaces ;
- Organisational authority governs organisational namespaces ;
- Individual authority governs personal namespaces (subject to verification).

Namespace registration requires appropriate authority.

---

## Authority and Validation

Authorities validate assertions within their scope:

- WSF Authority validates WSF-level claims ;
- Domain Authority validates domain claims ;
- Organisational Authority validates organisational claims ;
- Cross-authority validation requires federation agreement.

Validation produces validity status (per Validity construct).

---

## Canonical Examples

```yaml
# Foundational authority (WSF)
- authority:
    identifier: wsf-gov:WSF-Governance
    type: foundational
    scope:
      domain: world-level semantic foundations
      operational: full
    holder: WSF Governance Body

# Domain authority (OpenDEA federation)
- authority:
    identifier: opendea-gov:OpenDEA-Semantic-Authority
    type: domain
    scope:
      domain: enterprise architecture semantics
      operational: full
    holder: OpenDEA Governance
    granting_authority: wsf-gov:WSF-Governance
    grant_date: 2026-08-29

# Organisational authority (OTCHERE Inc)
- authority:
    identifier: wsf-ex:OTCHERE-Inc-Authority
    type: organisational
    scope:
      domain: OTCHERE Inc enterprise semantics
      operational: full
    holder: OTCHERE Inc Enterprise Architecture Team
    granting_authority: opendea-gov:OpenDEA-Semantic-Authority
    grant_date: 2026-08-29

# Individual authority (Kwesi)
- authority:
    identifier: wsf-ex:Kwesi-Authority
    type: individual
    scope:
      domain: OTCHERE Inc enterprise assertions
      operational: make_and_modify
    holder: Kwesi (individual)
    granting_authority: wsf-ex:OTCHERE-Inc-Authority
    grant_date: 2026-08-29
```

---

## Cross-References

- ADR-WSF-03 : Semantic Authority (authority categories)
- ADR-WSF-15 : Semantic Authority and Governance
- ADR-WSF-22 : Assertion and Provenance Model (authority in provenance)
- wsf:Context : the parent construct
- wsf:Namespace : governed by authority

---

*Authority is a Tier 2 supporting construct. Status: Baseline.*