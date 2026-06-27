# Motorized Base Construction

## Purpose
This document details the mechanical design, motor mounts, and dynamics of the motorized base.

## Chassis Components
*   **Base Deck Plate**: 12mm birch plywood deck.
*   **Motors**: 4 × Johnson 12V 200RPM geared motors.
*   **Motor Brackets**: 4 L-shaped heavy steel brackets bolted to the underside of the plywood deck using M4 machine screws.
*   **Wheels**: 4 × 100mm rubber-tread wheels. The two left wheels and the two right wheels are coupled, providing a stable 4x4 differential drive base.

## Turning Mechanics
The motorized base uses a differential drive configuration to turn:
```
     Left Motors Forward (▲)       Left Motors Reverse (▼)
     Right Motors Reverse (▼)      Right Motors Forward (▲)
          ┌─────────┐                   ┌─────────┐
          │   ▲   ▲ │                   │   ▼   ▲ │
          │         │                   │         │
          │   ▼   ▼ │                   │   ▲   ▼ │
          └─────────┘                   └─────────┘
         Spin Right                     Spin Left
```
