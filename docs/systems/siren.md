# Siren System

## Purpose

Manage emergency vehicle audio independently from lighting.

## Supported Tones

- Wail
- Yelp
- Phaser
- Horn

## Architecture

The server synchronizes necessary siren state.

The client handles audio playback.

Lighting and siren state must not be hard-coupled.

A vehicle may use emergency lighting without siren, or siren without changing the lighting state.
