# Networking Overview

## Principle

MPRP uses server-authoritative, event-driven networking.

## Client → Server

Examples:

- Toggle lighting
- Change lighting mode
- Toggle siren
- Radio transmission
- Change radio channel
- Update unit status
- Accept call
- Request backup
- CAD/MDT interaction

## Server → Client

Examples:

- Lighting state
- Siren state
- Radio transmission
- CAD updates
- Call assignments
- Unit status
- Pursuit updates

## Rules

Do not send unchanged state repeatedly.

Do not send per-light animation frames over the network.

The client should reconstruct visual animation from authoritative state such as mode, pattern, and phase.
