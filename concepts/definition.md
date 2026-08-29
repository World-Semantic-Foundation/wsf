# Definition

> **A formal, normative specification of a concept's meaning, expressed as a structured prose statement that establishes necessary and sufficient conditions for concept application.**

## Semantic Identity

```yaml
semantic_id: wsf:Definition
preferred_name: Definition
aliases: [Formal Definition, Definitional Statement]
status: Baseline
version: 0.1.0
classification: Tier 2 (Supporting Construct)
parent: wsf:Identity
defined_by: ADR-WSF-11, ADR-WSF-20
authority: WSF
```

---

## Definition

A **Definition** is a formal, normative specification of a concept's meaning. Definitions express necessary and sufficient conditions for applying a concept, enabling consistent interpretation across contexts and time. Definitions follow the structure established in ADR-WSF-20 (Concept Definition Model).

A Definition is NOT:
- A loose description (definitions are normative) ;
- An example (use examples separately) ;
- A usage note (use editorial annotations) ;
- A definition in one natural language only (definitions support multilingual formalisation).

---

## Definition Structure

A canonical WSF definition follows a structured form per ADR-WSF-20:

| Component | Required | Purpose |
|---|---|---|
| Super-type statement | Yes | Genus (broader category) |
| Differential characteristics | Yes | Distinguishing features |
| Scope notes | Optional | Boundaries of applicability |
| Examples | Optional | Illustrative instances |
| Counter-examples | Optional | What is NOT this concept |
| Citations | Optional | Authoritative sources |

---

## Definition Quality Criteria

A definition meets these criteria:

### 1 : Appropriate genus

The super-type statement correctly places the concept in its category.

### 2 : Essential differentia

The differential characteristics distinguish the concept from sibling concepts.

### 3 : Necessary conditions

Every stated condition is required for the concept to apply.

### 4 : Sufficient conditions

The stated conditions together suffice for the concept to apply.

### 5 : Non-circularity

The definition does not reference the concept being defined.

### 6 : Positive intelligibility

The definition states what the concept is, not merely what it is not.

### 7 : Clarity

The definition is expressed in unambiguous language.

---

## Definition Types

### Intensional Definition

Defines through properties (what the concept is):

- Lists essential characteristics ;
- More compact than extensional ;
- Allows inference about unobserved instances.

### Extensional Definition

Defines through enumeration (what instances are included):

- Lists all known instances ;
- More concrete but less portable ;
- Useful for closed sets.

### Operational Definition

Defines through measurement or test:

- Specifies how to determine applicability ;
- Useful for empirical concepts ;
- May require instrumentation.

### Ostensive Definition

Defines through demonstration:

- Shows rather than tells ;
- Useful for prototypes ;
- Less portable across contexts.

WSF prefers intensional definitions, supplemented with extensional examples.

---

## Definition Versioning

Definitions evolve under governance:

- **Patch version** : typo corrections, minor wording improvements ;
- **Minor version** : added scope notes, additional examples ;
- **Major version** : substantive changes to necessary/sufficient conditions.

Version changes are recorded with:

- The change rationale ;
- The authority approving the change ;
- Migration guidance for dependent concepts.

---

## Definition Multilingualism

Definitions support multilingual formalisation:

- Each language version is a full definition, not a translation ;
- Concepts identified by `semantic_id`, not by language ;
- Cross-language alignment verified by concept identity ;
- Translations reviewed by domain experts.

---

## Definition Authoring Workflow

Definitions are authored under governance:

1. **Drafting** : author drafts definition following structure ;
2. **Quality review** : governance checks definition against quality criteria ;
3. **Linguistic review** : language expert reviews for clarity ;
4. **Community review** : stakeholders review for accuracy ;
5. **Approval** : governance approves the definition ;
6. **Publication** : definition becomes normative ;
7. **Evolution** : changes follow versioning protocol.

---

## Definition vs Term vs Description

| Aspect | Definition | Term | Description |
|---|---|---|---|
| Purpose | Formal meaning | Human label | Narrative overview |
| Form | Structured prose | Word/phrase | Free prose |
| Normative | Yes | Yes | No |
| Required | Yes | Yes | Optional |
| Length | Variable (typically 50-200 words) | Short (1-3 words) | Variable |

---

## Definition Examples

### Foundational Concept Example

```yaml
- concept:
    semantic_id: wsf:Entity
    definition:
      super_type: A category of concepts representing individual things
      differentia: |
        that exist or may exist as discrete, identifiable particulars
        and are the bearers of properties, participants in events,
        and occupants of roles.
      scope_notes: |
        Includes both physical and non-physical entities.
        Excludes universals, properties, and relations themselves.
      examples:
        - A specific person (Kwesi)
        - A specific organisation (OTCHERE Inc)
        - A specific system (OTCHERE DC-01)
```

### Specialised Concept Example

```yaml
- concept:
    semantic_id: wsf:Capability
    definition:
      super_type: A specialised form of Disposition
      differentia: |
        that represents an attributable, contextualised potential
        of an Entity to accomplish a defined kind of effect or outcome,
        grounded in relevant Capacity and Ability within a defined context.
      scope_notes: |
        Capability is grounded in Disposition.
        A Capability MAY exist without being exercised.
      counter_examples:
        - Current performance (use Performance or Measurement)
        - Process (use Process for structured activity)
```

---

## Cross-References

- ADR-WSF-11 : Semantic Concept Specification
- ADR-WSF-20 : Concept Definition Model (16-section structure)
- wsf:Identity : the parent construct
- wsf:Term : human-readable label of the concept
- wsf:Assertion : claims that use definitions for meaning

---

*Definition is a Tier 2 supporting construct. Status: Baseline.*