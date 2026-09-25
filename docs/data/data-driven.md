# Data-Driven Content

MPRP separates content configuration from core Java logic wherever practical.

## Data Domains

- Departments
- Divisions
- Ranks
- Vehicles
- Lighting
- Sirens
- Radio
- Callouts
- Equipment
- Weapons
- Permissions
- Stations

## Goals

Adding content should normally require data files and assets rather than modifying core systems.

Core logic should validate and consume definitions.

Invalid definitions should produce clear errors and safe fallback behavior where appropriate.
