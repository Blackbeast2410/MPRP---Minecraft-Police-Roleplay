# ADR-0002: Event-Driven Network Synchronization

## Status

Accepted

## Date

2026-09-25

## Context

MPRP contains systems with frequent state changes, especially emergency lighting, sirens, radio, CAD, and pursuits.

Synchronizing complete state every tick would create unnecessary network traffic and make scaling more difficult.

## Decision

MPRP will use event-driven network synchronization.

Network messages should be sent when meaningful authoritative state changes occur.

Examples:

- Lighting mode changes
- Lighting pattern changes
- Siren state changes
- Radio transmissions
- Unit status changes
- Call assignment changes
- Pursuit state changes

Continuous visual animation remains client-side whenever possible.

## Consequences

### Benefits

- Lower network traffic
- Better scalability
- Clear state transitions
- Client-side visual interpolation and animation

### Costs

- State transitions must be designed carefully
- Clients need enough information to reconstruct presentation state
- Reconnection/resynchronization must be handled explicitly

## Alternatives Considered

### Full state synchronization every tick

Rejected due to unnecessary network overhead.

### Per-light synchronization

Rejected because physical light animation is a client presentation concern.
