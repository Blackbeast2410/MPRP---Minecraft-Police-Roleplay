# Vehicle System

## Responsibilities

The vehicle system handles:

- Vehicle state
- Driving
- Passengers
- Equipment
- Radio
- MDT
- Lighting
- Siren
- Inventory

## Separation

Keep these concepts separate:

```text
Vehicle Entity
Vehicle Definition
Vehicle Model
Handling
Equipment
Lighting Package
Siren Package
```

A vehicle definition should describe content and configuration rather than contain all vehicle behavior.

## Data Example

```json
{
  "id": "mprp:lapd_sedan",
  "department": "lapd",
  "class": "PATROL",
  "model": "police_sedan",
  "lighting_package": "lapd_marked",
  "siren_package": "lapd_standard",
  "handling": "patrol_sedan"
}
```

The actual schema may evolve as implementation progresses.
