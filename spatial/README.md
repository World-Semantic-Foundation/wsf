# WSF Spatial Module

> **Space semantics: Location, Position, Spatial Region; and the critical distinction Position ≠ Location.**

Defined by the Space concept (wsf:Space, Tier 1) and exercised in ADR-WSF-19 (containment relations) and ADR-WSF-22 (space as an assertion qualifier).

---

## Semantic Identity

```yaml
semantic_id: wsf:Space
preferred_name: Spatial Semantics
status: Baseline
version: 0.1.0
defined_by: ADR-WSF-17 (Foundational Semantic Architecture)
classification: Foundational
domain: Space
```

---

## The Three Spatial Primitives

| Primitive | Definition | Example |
|---|---|---|
| **Location** | A named, identified place with governance identity | OTCHERE DC-01's registered site: Accra Campus |
| **Position** | A geometric coordinate within a reference frame | 5.6037° N, 0.1870° W (WGS 84) |
| **Spatial Region** | A bounded area or volume used for containment semantics | the Greater Accra service region |

### Position ≠ Location

> A Location is an identified place; a Position is a coordinate.

The same Location may have many Positions (site entrance, centroid, survey points), and a Position may fall within many Regions. Locations have identity and provenance; Positions are measurements. Spatial relationships (`wsf-rel:contains`, located-in) connect Locations and Regions; Positions support them as evidence.

---

## Spatial Relation Semantics

Spatial containment reuses the Structural Form:

| Relationship | Semantics |
|---|---|
| `wsf-rel:contains` | Location/Region contains an entity or sub-region |
| `wsf-rel:is-contained-in` | Inverse containment |
| located-in (exemplary family) | Entity located in a Location |

Spatial containment is transitive (Region contains Site contains Room) and SHALL be context-qualified where scale matters (geopolitical, physical, logical topologies are distinct containment regimes).

---

## Space in Assertions

Space qualifies assertions analogously to time (per the assertion pattern):

```yaml
- assertion:
    subject: wsf-ex:OTCHERE-DC-01
    relationship: wsf-rel:is-contained-in
    object: wsf-ex:Greater-Accra-Region
    context: wsf-ctx:operations
    space:
      location: wsf-ex:Accra-Campus
      position: { lat: 5.6037, lon: -0.1870, frame: WGS84 }
```

---

## Spatial : Temporal Analogy

| Temporal | Spatial |
|---|---|
| Instant | Position (anchored point) |
| Interval | Spatial Region (bounded span) |
| Duration | Displacement/extent (unanchored length) |
| before/after | within/adjacent-to |
| holds-during | located-in |

The analogy is structural, not semantic: temporal and spatial primitives remain governed by their own constraints and SHALL NOT be conflated in assertions.

---

## Canonical Example

```yaml
- location:
    semantic_id: wsf-ex:Accra-Campus
    preferred_name: OTCHERE Accra Campus
    position: { lat: 5.6037, lon: -0.1870, frame: WGS84 }
    contained_in: wsf-ex:Greater-Accra-Region
    provenance:
      asserted_by: wsf-ex:Kwesi
      asserted_at: 2026-08-29
      source: OTCHERE Inc facilities register
```

---

## Cross-References

- [Space concept](../concepts/space.md)
- ADR-WSF-19 §5.1, ADR-WSF-22 §4
- [Temporal module](../temporal/README.md)

---

*Status: Baseline. Changes occur only through the ADR/CR process.*
