# Term

> **A human-readable, language-bound linguistic label that designates a concept in natural language use, distinct from the concept's identifier and definition.**

## Semantic Identity

```yaml
semantic_id: wsf:Term
preferred_name: Term
aliases: [Linguistic Label, Designation, Designator]
status: Baseline
version: 0.1.0
classification: Tier 2 (Supporting Construct)
parent: wsf:Identity
defined_by: ADR-WSF-10, ADR-WSF-18
authority: WSF
```

---

## Definition

A **Term** is a human-readable, language-bound linguistic label that designates a concept in natural language use. Terms are distinct from identifiers (machine-readable labels) and definitions (formal specifications of meaning) ; they are the linguistic surface through which concepts are communicated to humans.

A Term is NOT:
- An identifier (use Identifier for machine labels) ;
- A definition (use Definition for formal meaning) ;
- A universal label (terms are language-bound) ;
- An alias for multiple concepts (terms should be unambiguous within a language).

---

## Term vs Identifier vs Definition

| Aspect | Term | Identifier | Definition |
|---|---|---|---|
| Purpose | Human communication | Machine reference | Formal meaning |
| Form | Natural language | URI/CURIE | Prose specification |
| Uniqueness | Per language | Globally unique | Globally unique |
| Change rate | High | Low (stable) | Medium |
| Audience | Humans | Machines | Humans + machines |

---

## Term Components

A canonical term entry has these components:

| Component | Required | Purpose |
|---|---|---|
| Concept identifier | Yes | The concept this term designates |
| Text | Yes | The linguistic form |
| Language | Yes | ISO 639 language code |
| Part of speech | Optional | noun, verb, adjective, etc. |
| Usage scope | Optional | Where this term is preferred |
| Status | Yes | preferred, admitted, deprecated |

---

## Term Status

Terms carry lifecycle status:

### Preferred Term

The recommended term for a concept in a given context:

- Used by default in documentation ;
- Recommended in user-facing interfaces ;
- Subject to governance review.

### Admitted Term

Alternative term accepted as equivalent:

- Recognised but not preferred ;
- May appear in legacy content ;
- Useful for translation or regional variation.

### Deprecated Term

Historical term that should be replaced:

- Documented for backward compatibility ;
- New content SHOULD avoid ;
- Migration path to preferred term.

---

## Term Multilingualism

WSF supports multilingual terms:

- Each term associated with a language tag (BCP 47) ;
- Translations preserve concept identity, not term text ;
- Term alignment maintained across translations ;
- Cross-language search via concept identifier.

Example:

```yaml
# English term
- term:
    concept: wsf:Capability
    text: Capability
    language: en
    status: preferred

# French term
- term:
    concept: wsf:Capability
    text: Capacité
    language: fr
    status: preferred

# German term
- term:
    concept: wsf:Capability
    text: Fähigkeit
    language: de
    status: preferred
```

---

## Term Disambiguation

Terms SHOULD be unambiguous within a language:

- One concept per term (preferred) ;
- If a term is overloaded, context disambiguates ;
- Homonyms documented as separate concepts ;
- Polysemy handled through context.

---

## Term Alignment Across Vocabularies

Terms align across vocabularies through:

- Explicit `alignedWith` relationships ;
- Shared concept definitions ;
- Cross-vocabulary mappings ;
- Federation agreements.

Alignment enables translation and concept portability.

---

## Term Authoring Workflow

Terms are authored under governance:

1. **Proposal** : requestor proposes term for a concept ;
2. **Validation** : governance validates uniqueness within language ;
3. **Linguistic review** : language expert reviews appropriateness ;
4. **Approval** : governance approves with status (preferred, admitted) ;
5. **Publication** : term registered in concept record ;
6. **Use** : term appears in documentation and interfaces ;
7. **Review** : periodic review for currency ;
8. **Deprecation** : when appropriate, term marked deprecated.

---

## Term Relationships

Terms relate to concepts and to each other:

### Term-Concept Relationship

- One concept has multiple terms (multilingual) ;
- One term in one language designates one concept ;
- Term variant relationships (abbreviation, expansion).

### Term-Term Relationships

- Synonymy : equivalent terms across regional dialects ;
- Antonymy : opposite terms (rare in technical vocabularies) ;
- Hypernymy/hyponymy : general/specific terms.

---

## Term vs Display Label

A display label is a UI-rendering convenience:

- May differ from preferred term ;
- May include emojis, formatting, abbreviations ;
- Not governed as strictly as terms.

Terms are authoritative linguistic labels ; display labels are presentation choices.

---

## Term in Canonical Examples

```yaml
# Concept with multilingual terms
- concept:
    semantic_id: wsf:Capability
    terms:
      - text: Capability
        language: en
        status: preferred
      - text: Capacité
        language: fr
        status: preferred
      - text: Capacidad
        language: es
        status: preferred
      - text: 能力
        language: zh
        status: preferred

# Alias (alternative designation)
- concept:
    semantic_id: wsf:Disposition
    terms:
      - text: Disposition
        language: en
        status: preferred
      - text: Potential
        language: en
        status: admitted
      - text: Tendency
        language: en
        status: admitted
```

---

## Cross-References

- ADR-WSF-10 : Semantic Identity and Naming
- ADR-WSF-18 : Concept Identity
- wsf:Identity : the parent construct
- wsf:Definition : the formal meaning that terms designate

---

*Term is a Tier 2 supporting construct. Status: Baseline.*