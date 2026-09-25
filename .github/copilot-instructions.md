# MPRP Copilot Instructions

## Project
MPRP is a large-scale Minecraft police roleplay framework
for Minecraft 1.21.1 using NeoForge and Java 21.

## Architecture
- Keep the server authoritative.
- Keep client rendering and audio client-side.
- Avoid unnecessary per-tick network synchronization.
- Prefer event-driven systems.
- Keep gameplay logic separate from rendering.
- Keep content data-driven where practical.

## Development Rules
- Inspect the existing architecture before making changes.
- Do not rewrite unrelated files.
- Do not introduce unnecessary dependencies.
- Preserve singleplayer compatibility.
- Build and test after significant changes.
- Do not silently change public APIs.

## Documentation
Before implementing a major system, consult the relevant
documentation under /docs.