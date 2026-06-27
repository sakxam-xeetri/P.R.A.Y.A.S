| **I2C SDA** | I2C Data | Internal LSM9DS1 (IMU) / Sensors |
| **Tx / D1** | UART Serial Transmit | Master Node GPIO 35 (or ESP-NOW) |

## Data Flow
```
 [ IMU / HTS221 / APDS9960 ] ──(I2C)──> [ Nano 33 BLE ] ──(UART / ESP-NOW)──> [ Master Node ]
```

## Failure Cases & Recovery
*   **Sensor Frozen (I2C Lockup)**: If the IMU fails to update for more than 5 consecutive cycles, the Nano 33 BLE triggers a software reset (`NVIC_SystemReset()`) to re-initialize the I2C bus.
