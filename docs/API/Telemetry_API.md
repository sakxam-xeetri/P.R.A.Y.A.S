# Telemetry API Reference

## Purpose
This document details the telemetry packet structure used to transmit system status data.

## Telemetry Fields Schema
The telemetry data published to `prayas/telemetry/state` includes the following fields:

| Field Name | Type | Unit | Description |
| :--- | :--- | :---: | :--- |
| `timestamp` | Integer | ms | Time elapsed since Master Node boot. |
| `battery.voltage` | Float | V | Battery voltage read from the analog sensor (range $9.0	ext{V}$ to $12.6	ext{V}$). |
| `battery.current` | Float | A | Current draw read from the ACS712 sensor. |
| `sensors.ultrasonic_front`| Float | cm | Distance read from the front ultrasonic sensor. |
| `sensors.ultrasonic_rear` | Float | cm | Distance read from the rear ultrasonic sensor. |
| `system_state` | String | - | Current state (e.g. `STATE_IDLE`, `STATE_MOVING`, `STATE_FAULT`). |
