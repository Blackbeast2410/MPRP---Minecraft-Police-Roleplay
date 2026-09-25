# ADR-0004: Shared Singleplayer and Multiplayer Architecture

## Status

Accepted

## Date

2026-09-25

## Context

MPRP must work in singleplayer while also supporting multiplayer with real human dispatchers, officers, supervisors, and command roles.

The two environments have different requirements, but duplicating the entire gameplay architecture would create maintenance problems.

## Decision

MPRP will use shared gameplay interfaces with environment-specific implementations where required.

For example:

```text
DispatchService
├── LocalDispatchService
└── NetworkDispatchService
```

Singleplayer will not require simulated human network participants.

Multiplayer will use real server/network services.

## Consequences

### Benefits

- Shared gameplay logic
- Less duplicated code
- Clear separation of local and network behavior
- Better long-term maintainability

### Costs

- Interfaces require careful design
- Some features need separate implementations
- Environment-specific behavior must be tested

## Alternatives Considered

### Separate singleplayer and multiplayer codebases

Rejected because it would create substantial duplication.

### Force singleplayer to emulate multiplayer

Rejected because singleplayer does not require fake human dispatch/network participants.
