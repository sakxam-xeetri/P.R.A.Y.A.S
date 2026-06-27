# Sensor Node

## Purpose
The Sensor Node collects environmental and inertial data to help the robot monitor its physical state and navigate safely.

## Hardware Used
*   **MCU**: Arduino Nano 33 BLE Sense (featuring a Nordic nRF52840 Cortex-M4 CPU).
*   **IMU**: LSM9DS1 (9-axis inertial measurement unit).
*   **Ultrasonic Sensors**: 2 × HC-SR04 sensors (front and rear).

## GPIO Mapping
| GPIO Pin | Pin Function | Target Component |
| :--- | :--- | :--- |
| **I2C SCL** | I2C Clock | Internal LSM9DS1 (IMU) |
| **I2C SDA** | I2C Data | Internal LSM9DS1 (IMU) |
| **D2** | Echo Pin | Front HC-SR04 Sensor |
| **D3** | Trigger Pin | Front HC-SR04 Sensor |
| **D4** | Echo Pin | Rear HC-SR04 Sensor |
| **D5** | Trigger Pin | Rear HC-SR04 Sensor |
| **Tx** | UART Serial Transmit | Master Node GPIO 35 (or ESP-NOW) |

## Data Flow
```
 [ IMU / LSM9DS1 ] ──(I2C)──┐
                             ├──> [ Nano 33 BLE ] ──(UART / ESP-NOW)──> [ Master Node ]
 [ HC-SR04 Sonar ] ─(Pulse)──┘
```

## Failure Cases & Recovery
*   **Sensor Frozen (I2C Lockup)**: If the IMU fails to update for more than 5 consecutive cycles, the Nano 33 BLE triggers a software reset (`NVIC_SystemReset()`) to re-initialize the I2C bus.
