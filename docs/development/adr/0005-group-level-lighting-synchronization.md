# ADR-0005: Group-Level Emergency Lighting Synchronization

## Status

Accepted

## Date

2026-09-25

## Context

Police vehicles participating in a pursuit or coordinated scene may need synchronized emergency lighting.

Synchronizing every physical light from one vehicle to every other vehicle would generate unnecessary state and network traffic and would tightly couple vehicle implementations.

## Decision

MPRP will synchronize emergency lighting at the group level.

A lighting group stores abstract state such as:

- Group ID
- Lighting state
- Pattern ID
- Synchronization mode
- Phase information
- Traffic Advisor state

Each vehicle retains its own lighting package and renders its own physical light nodes.

Supported synchronization modes may include:

- SYNCED
- STAGGERED
- ALTERNATING
- INDEPENDENT

## Consequences

### Benefits

- Low network overhead
- Vehicle-specific lighting packages remain independent
- More realistic phase offsets
- Easier pursuit-wide synchronization

### Costs

- Client rendering logic is more complex
- Group lifecycle must be managed
- Rejoining/leaving a group requires state transitions

## Alternatives Considered

### Copy physical light states between vehicles

Rejected because it creates excessive coupling and synchronization overhead.

### Synchronize every physical light every tick

Rejected because physical animation is client-side presentation.
