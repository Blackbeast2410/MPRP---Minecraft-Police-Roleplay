# Unit System

## Purpose

The unit system represents patrol and specialized operational units.

## Unit State

Supported states:

- OFF_DUTY
- AVAILABLE
- EN_ROUTE
- ON_SCENE
- BUSY
- TRANSPORTING
- AT_HOSPITAL
- AT_STATION
- OUT_OF_SERVICE

## Assignment Rules

A dispatcher should normally assign only eligible units.

BUSY units must not receive new calls unless an explicit supervisor override exists.

## Unit Composition

A unit may contain:

- One officer
- Two officers
- Specialized personnel

The unit identity is separate from the player identity.

## Server Authority

Unit status is authoritative on the server and synchronized to authorized clients.
