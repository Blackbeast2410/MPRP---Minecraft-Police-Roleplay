# ADR-0001: Server-Authoritative Gameplay State

## Status

Accepted

## Date

2026-09-25

## Context

MPRP supports multiplayer police roleplay involving officers, dispatchers, supervisors, CAD, pursuits, vehicles, lighting, radio, arrests, evidence, and permissions.

If clients are allowed to directly determine authoritative gameplay state, clients could become inconsistent or manipulate gameplay state.

## Decision

MPRP will use a server-authoritative architecture.

The server owns authoritative gameplay state, including:

- Officer and unit state
- CAD calls and assignments
- Pursuits
- Arrests and citations
- Evidence
- Permissions
- Vehicle gameplay state
- Emergency lighting state
- Siren state
- Radio state

Clients send validated requests to the server.

Clients are responsible primarily for presentation, input, rendering, and audio.

## Consequences

### Benefits

- Consistent multiplayer state
- Easier validation
- Better protection against client-side manipulation
- Clear client/server responsibilities

### Costs

- More networking code
- Client requests must be validated
- Some features require explicit synchronization design

## Alternatives Considered

### Client-authoritative state

Rejected because it is unsuitable for authoritative multiplayer police gameplay.

### Fully synchronized peer-to-peer state

Rejected because it complicates authority, validation, and persistence.
