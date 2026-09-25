# Vehicle Definitions

Vehicle definitions describe configurable vehicle content.

Example:

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

The definition should not contain behavior that belongs in the vehicle implementation.

Model nodes may identify physical light locations, while the lighting package determines how those nodes are controlled.
