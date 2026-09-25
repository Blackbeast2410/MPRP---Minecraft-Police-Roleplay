# ADR-0007: Configurable Police Organization

## Status

Accepted

## Date

2026-09-25

## Context

MPRP initially uses an LAPD-style organizational model as a reference, including bureaus, divisions, stations, watches, beats, ranks, and units.

The project may later support CHP, LASD, fictional departments, or custom departments.

## Decision

The organizational model will be configurable rather than hardcoded around one real-world department.

The architecture will support concepts such as:

- Department
- Bureau
- Division
- Station
- Watch
- Beat
- Rank
- Assignment
- Unit

Department-specific terminology and structure should be represented through data where practical.

## Consequences

### Benefits

- Supports multiple departments
- Reduces hardcoded assumptions
- Allows custom/f fictional organizations
- Makes content expansion easier

### Costs

- More general data models
- Some department-specific behavior requires configuration or extension points

## Alternatives Considered

### Hardcode LAPD structure

Rejected because it would make future department support unnecessarily difficult.
