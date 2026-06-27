# Microcontrollers & Co-processors

## Purpose
This document provides a comparative analysis of the microcontrollers used in PRAYAS V1, explaining the selection rationale and hardware capabilities.

## Hardware Used
The platform distributes processing across multiple microcontrollers to handle specific real-time tasks:

*   **ESP32-WROOM-32E (Master, Motor, Servo, Power Nodes)**: Chosen for its dual-core Xtensa 32-bit LX6 processor (240 MHz, 520 KB SRAM, 4MB Flash), built-in Wi-Fi and Bluetooth, and ESP-NOW support.
*   **ESP32-S3-WROOM-1 (AI Node)**: Integrates vector instructions for accelerating neural network calculations (voice wake word, simple wake gesture processing), along with 8MB Octal SPI PSRAM.
*   **ESP32-CAM (Camera Node)**: OV2640 camera interface with built-in micro-SD slot, providing a cost-effective, low-power video server.
*   **Arduino Nano 33 BLE Sense (Sensor Node)**: Features a 64 MHz ARM Cortex-M4 (nRF52840) with low power consumption and onboard sensors (IMU, microphone, gesture/light/color sensors).

## Comparative Specifications Table
| Parameter | ESP32-WROOM-32E | ESP32-S3-WROOM-1 | ESP32-CAM | Nano 33 BLE Sense |
| :--- | :--- | :--- | :--- | :--- |
| **Core Architecture** | Tensilica Xtensa LX6 | Tensilica Xtensa LX7 | Tensilica Xtensa LX6 | ARM Cortex-M4F |
| **Core Speed** | 240 MHz (Dual) | 240 MHz (Dual) | 240 MHz (Dual) | 64 MHz (Single) |
| **SRAM** | 520 KB | 512 KB internal + 8MB | 520 KB internal + 4MB | 256 KB |
| **Flash** | 4 MB | 8 MB | 4 MB | 1 MB |
| **WiFi** | 802.11 b/g/n (150 Mbps)| 802.11 b/g/n (150 Mbps)| 802.11 b/g/n | None |
| **Bluetooth** | BLE v4.2 BR/EDR | BLE v5.0 / Mesh | BLE v4.2 BR/EDR | BLE v5.0 |
| **Primary Task** | Real-time Motor/Servos| AI & Speech Engine | Video Stream | IMU & Environment |

## Limitations
*   **Shared Radio**: On the ESP32-WROOM-32E, Wi-Fi and Bluetooth share the same 2.4 GHz antenna. Enabling both simultaneously can cause packet drops.
*   **ESP32-CAM RAM**: The ESP32-CAM module lacks extensive heat dissipation, so streaming at high resolutions (e.g. UXGA) can lead to thermal throttling and frame rate drops.
