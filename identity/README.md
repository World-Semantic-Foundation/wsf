# WSF Identity Module

> **The identity foundations of WSF: the distinctions between Identity, Identifier, Name, Reference, and Representation, and the model of identity persistence through evolution.**

Defined by ADR-WSF-18 (Concept Identity) and ADR-WSF-21 (Namespace and Reference Model). Identity is the stable, persistent identity of a concept or entity; references, names, and representations are ways to refer to it, and SHALL NOT be conflated with the identity itself.

---

## Module Structure

```
identity/
├── README.md              (this file)
├── identity-model.md      The Concept Identity Model (ADR-WSF-18 §4)
├── identifier-scheme.md   The identifier scheme and CURIE rules (ADR-WSF-21 §5-6)
└── identity-lifecycle.md  Identity lifecycle and persistence through evolution
```

---

## The 5 Distinctions (Investigation 6)

| Distinction | What it is | Example |
|---|---|---|
| **Identity** | The stable, persistent identity of a concept or entity | the identity of OTCHERE Inc through time |
| **Identifier** | A concrete representation of identity within a scheme | `wsf-ex:OTCHERE-Inc` |
| **Name** | A human-readable label referring to the identity | "OTCHERE Inc" |
| **Reference** | An act of referring to the identity in discourse or data | the link in an assertion |
| **Representation** | A serialization of the identity's specification | the Turtle/OpenAPI/JSON rendering of `wsf:Capability` |

Identity is primary; the other four are derivatives. Rejected alternatives (ADR-WSF-18 §17): identity by name, by location, by version, by representation, by context, or implicitly.

---

## Governing Principle

> **Identity persists through compatible evolution and is replaced only on semantic breaking change.**

---

## Assets

- [Identity Model](./identity-model.md) : the four-component model
- [Identifier Scheme](./identifier-scheme.md) : syntax, namespaces, CURIEs, assignment rules
- [Identity Lifecycle](./identity-lifecycle.md) : states, persistence, collision resolution

---

## Cross-References

- ADR-WSF-18: Concept Identity
- ADR-WSF-21: Namespace and Reference Model
- [Identity concept](../concepts/identity.md), [Identifier concept](../concepts/identifier.md), [Reference concept](../concepts/reference.md), [Namespace concept](../concepts/namespace.md)

---

*Status: Baseline. Changes occur only through the ADR/CR process.*
