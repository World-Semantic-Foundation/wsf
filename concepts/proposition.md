# Proposition

> **A semantic content that can be true, false, or indeterminate — the abstract content of an assertion or belief.**

---

## Semantic Identity

```yaml
semantic_id: wsf:Proposition
preferred_name: Proposition
aliases: [Statement, Claim, Content]
status: Normative
version: 1.0.0
classification: Tier 1 (Foundational)
parent: wsf:Concept
authority: WSF
```

---

## Definition

A **Proposition** is a semantic content that can be true, false, or indeterminate — the abstract content that an assertion expresses.

A Proposition is NOT:
- An assertion (use Assertion — propositions are what assertions assert);
- A sentence (sentences express propositions in language);
- A belief (beliefs are mental states about propositions);
- Truth itself (truth is a property of propositions).

A Proposition IS:
- Abstract semantic content;
- Capable of being true or false;
- Expressible in multiple ways (different sentences can express the same proposition);
- Independent of any particular assertion of it.

---

## Why Proposition Is Foundational

Proposition is foundational because:

1. **Assertions are about propositions** — to assert something is to assert a proposition;
2. **Truth applies to propositions** — truth is a property of propositions;
3. **Reasoning operates on propositions** — logical reasoning works on propositions;
4. **Multiple agents can assert the same proposition** — shared content;
5. **Propositions can be true independently of being asserted** — reality is independent of claims.

Without Proposition, the architecture cannot distinguish "what is asserted" from "the act of asserting".

---

## Proposition Examples

| Proposition | True | False | Indeterminate |
|---|---|---|---|
| "OTCHERE Inc possesses Order Fulfillment Capability" | (depends on reality) | (depends on reality) | (if not enough evidence) |
| "Kwesi has Enterprise Architecture Ability" | (depends on reality) | (depends on reality) | (if not enough evidence) |
| "Order #12345 was placed on 2026-08-29" | (depends on reality) | (depends on reality) | (if not enough evidence) |

A proposition's truth value depends on reality, not on whether it is asserted.

---

## Proposition vs Assertion (Critical Distinction)

| Aspect | Proposition | Assertion |
|---|---|---|
| **Nature** | Abstract content | Act of claiming |
| **Example** | "OTCHERE has Order Fulfillment" | Kwesi's claim that OTCHERE has Order Fulfillment |
| **Truth** | Has truth value | May or may not be valid |
| **Multiple instances** | Same proposition can be asserted multiple times | Each assertion is distinct |
| **Language** | Language-independent | Made in a context by an agent |

Propositions are what is asserted. Assertions are the acts of asserting.

```
Proposition: "OTCHERE has Order Fulfillment Capability"
   ↓ (asserted by Kwesi at time T in context C)
Assertion: Kwesi's specific claim, with provenance
```

---

## Proposition vs Statement (Linguistic Distinction)

A statement (sentence) expresses a proposition:

```
Sentence 1: "OTCHERE has Order Fulfillment Capability."
Sentence 2: "OTCHERE possesses the ability to fulfill orders."
Sentence 3: "OTCHERE peut exécuter des commandes."

All three sentences MAY express the same Proposition.
```

Different sentences can express the same proposition in different languages.

---

## Proposition Truth Values

Propositions have truth values:

- **True**: Corresponds to reality.
- **False**: Does not correspond to reality.
- **Indeterminate**: Truth cannot be determined (insufficient evidence).
- **Necessarily true**: True in all possible worlds (e.g., logical truths).
- **Necessarily false**: False in all possible worlds.

Per ADR-WSF-22, truth is distinct from assertion validity.

---

## Proposition Structure

A Proposition MAY carry:

```yaml
- proposition:
  semantic_id: wsf-prop:<id>
  content: <proposition content>
  language_independent: boolean
  truth_value: true | false | indeterminate | necessarily_true | necessarily_false
  modality:
    necessary: boolean
    possible: boolean
  subject: <subject reference>
  predicate: <predicate reference>
  object: <object reference>
  context: <context>
  truth_conditions: <what would make this true>
  expressed_in:
    - language: en
      text: "OTCHERE has Order Fulfillment Capability"
    - language: fr
      text: "OTCHERE a la capacité de traitement des commandes"
```

---

## Propositions in Reasoning

Logical reasoning operates on propositions:

```
Proposition A: "OTCHERE possesses Order Fulfillment Capability"
Proposition B: "Order Fulfillment requires Operations Center"
Proposition C: "If A and B, then OTCHERE has Operations Center"

Reasoning chain:
  A (true)
  B (true)
  C (logical implication)
  ∴ OTCHERE has Operations Center
```

This is the foundation for semantic reasoning.

---

## Propositions in Semantic Assertions

An assertion asserts a proposition:

```yaml
- assertion:
  semantic_id: wsf-assertion:<id>
  asserts_proposition: wsf-prop:<prop-id>
  asserted_by: <agent>
  asserted_at: <timestamp>
  context: <context>
  evidence: <evidence>
  provenance: <provenance>
```

The relationship: Assertion → asserts_proposition → Proposition.

---

## Proposition Lifecycle

Propositions don't have lifecycle states in the same way semantic artifacts do. Instead:

- A proposition exists if its content is expressible;
- A proposition can be true or false independent of any assertion;
- A proposition can be asserted by multiple agents;
- A proposition's truth can change (e.g., if reality changes).

Propositions are timeless in content; their truth is contingent on reality.

---

## Related Concepts

- [Assertion](./assertion.md) — The act of claiming a proposition
- [Concept](./concept.md) — Concepts participate in propositions
- [Entity](./entity.md) — Entities participate in propositions
- [Relationship](./relationship.md) — Relationships form parts of propositions
- [Context](./context.md) — Context affects proposition interpretation

---

## Related ADRs

- ADR-WSF-05 — Semantic Assertion
- ADR-WSF-12 — Semantic Assertion Model
- ADR-WSF-22 — Assertion and Provenance Model

---

## Cross-Repository References

- Canonical semantic asset: [wsf/concepts/proposition.md](https://github.com/World-Semantic-Foundation/wsf/blob/main/concepts/proposition.md)
