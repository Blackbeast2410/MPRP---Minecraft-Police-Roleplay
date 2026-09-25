# MPRP Architecture Overview

## Purpose

MPRP is designed as a long-term modular police roleplay framework rather than a collection of independent gameplay scripts.

The architecture separates:

- Domain/gameplay logic
- Minecraft/NeoForge integration
- Client presentation
- Networking
- Persistence
- Data definitions

## Core Principle

The server owns authoritative gameplay state.

The client presents that state through rendering, audio, GUI, and input.

## Major Domains

```text
police
vehicle
lighting
siren
radio
cad
dispatch
callout
ai
pursuit
investigation
equipment
weapons
roles
permissions
network
data
client
platform
```

## Dependency Direction

Gameplay systems should depend on stable domain interfaces where practical.

Minecraft-specific implementation details should not leak unnecessarily into domain logic.

Client-only code must not be loaded from dedicated-server paths.

## Design Goals

1. Server authority
2. Singleplayer compatibility
3. Multiplayer correctness
4. Data-driven content
5. Event-driven networking
6. Focused responsibilities
7. Extensibility
8. Testability
