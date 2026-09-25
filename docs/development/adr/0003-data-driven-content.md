# ADR-0003: Data-Driven Content

## Status

Accepted

## Date

2026-09-25

## Context

MPRP is intended to support multiple departments, vehicles, lighting packages, sirens, callouts, stations, equipment, and permissions.

Hardcoding each content variant into Java would make expansion increasingly expensive.

## Decision

MPRP will separate content definitions from core gameplay logic where practical.

Data-driven domains include:

- Departments
- Divisions
- Ranks
- Vehicles
- Lighting packages
- Siren packages
- Radio configuration
- Callouts
- Equipment
- Weapons
- Permissions
- Stations

Java systems provide behavior and validation.

Data files provide configuration and content definitions.

## Consequences

### Benefits

- Easier content expansion
- Less duplicated Java code
- Better mod extensibility
- Easier configuration changes

### Costs

- Schema validation is required
- Invalid data needs useful diagnostics
- Data formats become part of the project's compatibility surface

## Alternatives Considered

### Hardcode every department and vehicle

Rejected because it does not scale.

### Put all behavior in data

Rejected because complex behavior belongs in maintainable code.
