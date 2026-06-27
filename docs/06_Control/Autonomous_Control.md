# Autonomous Locomotion & Pathing

## Purpose
This document details the autonomous locomotion, path planning, and obstacle avoidance systems of PRAYAS V1.

## Obstacle Avoidance Flowchart
Locomotion tasks default to a safety-monitored behavior:

```mermaid
flowchart TD
    Start([Start Pathing]) --> ReadSensors[Read Ultrasonic Sonars]
    ReadSensors --> CheckDist{Is Obstacle < 20cm?}
    
    CheckDist -- Yes --> StopBase[Halt Motors]
    StopBase --> BackUp[Reverse 10cm]
    BackUp --> SpinBase[Rotate 45 degrees left]
    SpinBase --> ReadSensors
    
    CheckDist -- No --> DriveForward[Drive toward target coordinates]
    DriveForward --> ReadSensors
```

## Odometry & Path Tracking
*   **Open-Loop Target Pathing**: In V1, the robot estimates its position using wheel rotation duration and velocity profiles.
*   **Odometry Limitations**: Without wheel encoders, slippage on smooth floors can cause positioning errors (drift) of up to 15% over a 5-meter drive.
