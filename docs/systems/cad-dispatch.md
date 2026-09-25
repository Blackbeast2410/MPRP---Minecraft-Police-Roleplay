# CAD and Dispatch

## Core Objects

- Call
- UnitRegistry
- UnitAssignment
- BOLO
- Warrant
- Incident

## Call Lifecycle

```text
CREATED
  ↓
QUEUED
  ↓
DISPATCHED
  ↓
ACKNOWLEDGED
  ↓
EN_ROUTE
  ↓
ON_SCENE
  ↓
INVESTIGATING
  ↓
CLEARED
  ↓
CLOSED
```

## Call Data

A call may contain:

- ID
- Time received
- Source
- Caller
- Location
- Nature
- Priority
- Status
- Assigned units
- Dispatcher
- Notes
- Related persons
- Related vehicles
- Incident

## Assignment

Dispatch must consider unit status and eligibility.

CAD is server authoritative in multiplayer.
