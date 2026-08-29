# Space

> **The semantic dimension of spatial location and arrangement — positions, regions, containment, and the relationships between them.**

---

## Semantic Identity

```yaml
semantic_id: wsf:Space
preferred_name: Space
aliases: [Spatial Dimension, Spatial Semantics]
status: Normative
version: 1.0.0
classification: Tier 1 (Foundational)
parent: wsf:Entity
authority: WSF
```

---

## Definition

**Space** is the semantic dimension of spatial location and arrangement — positions, regions, containment, and the relationships between them.

Space is NOT:
- A physical quantity alone;
- A coordinate system alone;
- A property of entities (space is a dimension entities exist within).

Space IS:
- A semantic dimension;
- Composed of positions and regions;
- A dimension along which entities are located;
- Structured by spatial relationships.

---

## Why Space Is Foundational

Space is foundational because:

1. **Entities are located in space** — without space, no location;
2. **Events occur in space** — without space, events are placeless;
3. **Resources occupy space** — without space, no resource allocation;
4. **Systems have spatial extent** — without space, no architecture;
5. **Integration has spatial implications** — without space, no physical integration.

Without Space, the architecture cannot model location, arrangement, or geography.

---

## Space Components

WSF distinguishes:

### 1. Position

A point in space with no extent.

Example: Lat/long coordinates, named location.

### 2. Region

A bounded spatial extent.

Example: A country, a building, a network.

### 3. Path

A route through space.

Example: A delivery route, a network cable.

### 4. Boundary

The edge of a region.

Example: A country border, a firewall.

### 5. Location (general)

A position or region reference.

Example: "OTCHERE Inc is located at 100 OTCHERE Way."

---

## Space vs Spatial Dimension

Space as a concept vs Space as a dimension:

- **Space (concept)**: The semantic concept of spatial location and arrangement.
- **Spatial Dimension**: The application of Space to qualify other semantic artifacts.

Both are needed. The concept provides the foundation; the dimension is the application.

---

## Space Structure

Space carries:

```yaml
- space:
  semantic_id: wsf-space:<id>
  type: Position | Region | Path | Boundary | Location
  
  # For Position
  coordinates:
    latitude: <degrees>
    longitude: <degrees>
    altitude: <meters> (optional)
  
  # For Region
  shape: polygon | rectangle | circle | custom
  coordinates: <list of points>
  area: <square meters>
  
  # For Path
  waypoints: <list of positions>
  distance: <meters>
  
  # Reference system
  coordinate_system: WGS84 | UTM | local | custom
  
  # Address (if applicable)
  address:
    street: <street>
    city: <city>
    region: <region>
    postal_code: <code>
    country: <country>
  
  # Named location (if applicable)
  named_location: <name>
```

---

## Space Relationships

WSF defines the following space relationships:

| Relationship | Definition |
|---|---|
| `contains` | X contains Y (Y inside X) |
| `inside` | X is inside Y (Y contains X) |
| `overlaps` | X and Y share space |
| `adjacent-to` | X is adjacent to Y (touching) |
| `intersects` | X and Y share some space |
| `disjoint-from` | X and Y share no space |
| `near` | X is near Y (close, defined threshold) |
| `far` | X is far from Y (distant) |
| `same-place` | X is at the same location as Y |

---

## Space vs Position vs Location

| Concept | Meaning |
|---|---|
| **Position** | A point (no extent) |
| **Location** | A general spatial reference (point or region) |
| **Space** | The semantic dimension of spatial arrangement |

Position is specific; Location is general; Space is the underlying dimension.

---

## Space in Semantic Assertions

Space qualifies assertions:

```yaml
- assertion:
  ...
  space: wsf-space:OTCHERE-DC-01
  # The assertion applies at this location
```

Or:

```yaml
- assertion:
  ...
  context:
    space: wsf-space:OTCHERE-DC-01
    time: <temporal qualifier>
```

---

## Space in Events

Events occur in space:

```yaml
- event:
  semantic_id: wsf-event:Order-12345-Shipped
  occurred_at: 2026-08-29T14:30:00Z
  location: wsf-space:OTCHERE-Warehouse
  # The event occurred at the OTCHERE Warehouse
```

Events have both temporal and spatial location.

---

## Space in States

States hold in space:

```yaml
- state:
  type: Operational
  bearer: OTCHERE DC-01
  valid_from: 2024-01-15T08:00:00Z
  valid_until: open-ended
  located_at: wsf-space:100-OTCHERE-Way
  # The system is operational at this location
```

---

## Spatial Dimensions in Assertions

Multiple spatial dimensions apply:

| Dimension | Meaning |
|---|---|
| **Located-at** | Where something is |
| **Occurred-at** | Where something happened |
| **Recorded-at** | Where something was recorded |
| **Asserted-from** | Where the assertion was made |

These can all differ. An event can occur at one location, be observed elsewhere, and be asserted from a third location.

---

## Space and Containment

Containment is a key spatial relationship:

```
OTCHERE Inc (organization)
   contains OTCHERE DC-01 (data center)
   contains OTCHERE Warehouse
   contains OTCHERE Office-Building
```

Containment has clear semantics for resources, systems, organizations.

---

## Space and Systems

Systems have spatial extent:

```
OTCHERE DC-01 (data center)
   contains [Server Rack A, Server Rack B, ...]
   contains [Network Switch, Storage Array]
```

Systems span physical or virtual space.

---

## Space and Resources

Resources occupy space:

```
OTCHERE DC-01
   occupies 5000 sq ft
   contains 100 server racks
   contains 1 PB storage
```

Resources have spatial extent and location.

---

## Space Validation

Space references SHALL be validated for:

1. **Format validity**: Coordinates in valid format.
2. **Range validity**: Coordinates within representable range.
3. **Coordinate system**: Recognized system.
4. **Address validity**: Address exists.
5. **Containment consistency**: Containment hierarchies are consistent.

---

## Space in Digital Twin Pattern

Space is one of the 8 dimensions of digital twins:

```yaml
- entity_instance: OTCHERE DC-01
  space:
    physical:
      address: 100 OTCHERE Way, Datacenter District
      geographic_coordinates:
        latitude: ...
        longitude: ...
      region: ...
    network:
      ipv4_range: 10.20.0.0/16
      asn: AS65001
```

The digital twin's spatial record includes both physical and network space.

---

## Space vs Topology

Space is geometric; topology is about connectedness:

- **Space**: Where things are located.
- **Topology**: How things are connected.

Both are needed. Topology often overlays spatial relationships.

---

## Space Reference Systems

Space references various systems:

- **WGS84**: Standard geographic coordinates.
- **UTM**: Universal Transverse Mercator.
- **Local coordinates**: Building/floor/room.
- **Network addresses**: IPv4, IPv6 ranges.
- **Logical addresses**: URIs, URLs.

Each has its own conventions.

---

## Space Examples

### Geographic Position

```yaml
- space:
  semantic_id: wsf-space:OTCHERE-DC-01
  type: Position
  coordinates:
    latitude: 37.7749
    longitude: -122.4194
  coordinate_system: WGS84
  named_location: OTCHERE DC-01
  address:
    street: 100 OTCHERE Way
    city: Datacenter District
    region: California
    postal_code: "94101"
    country: USA
```

### Network Region

```yaml
- space:
  semantic_id: wsf-space:OTCHERE-Network-A
  type: Region
  coordinates:
    ipv4_range: 10.20.0.0/16
    ipv6_range: 2001:db8:otchere::/48
  named_location: OTCHERE Inc Internal Network A
```

### Containment Hierarchy

```yaml
- containment:
  parent: wsf-space:OTCHERE-DC-01
  children:
    - wsf-space:OTCHERE-DC-01-Rack-A1
    - wsf-space:OTCHERE-DC-01-Rack-A2
    - wsf-space:OTCHERE-DC-01-Network-Closet
```

---

## Related Concepts

- [Entity](./entity.md) — Entities located in space
- [Event](./event.md) — Events occur in space
- [Time](./time.md) — Time is the temporal dimension (parallel to space)
- [Context](./context.md) — Contexts may have spatial scope

---

## Related ADRs

- ADR-WSF-09 — Foundational Concept Taxonomy
- ADR-WSF-19 — Semantic Relationship Model (spatial relationships)
- ADR-WSF-22 — Assertion and Provenance Model (spatial validity)

---

## Cross-Repository References

- Canonical semantic asset: [wsf/concepts/space.md](https://github.com/World-Semantic-Foundation/wsf/blob/main/concepts/space.md)
