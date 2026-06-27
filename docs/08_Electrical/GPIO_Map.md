# Master GPIO Mapping Table

## Purpose
This document provides a single-point-of-truth GPIO mapping table for all microcontroller nodes in PRAYAS V1.

## Complete GPIO Assignments

### 1. Master Coordinator Node (ESP32)
*   **GPIO 16**: UART Rx2 (Connected to AI Node Tx)
*   **GPIO 17**: UART Tx2 (Connected to AI Node Rx)
*   **GPIO 21**: I2C SDA (OLED Display / Status Display)
*   **GPIO 22**: I2C SCL (OLED Display / Status Display)

### 2. Motor Controller Node (ESP32)
*   **GPIO 12**: Left Motor PWM Forward (L_PWM)
*   **GPIO 13**: Left Motor PWM Reverse (R_PWM)
*   **GPIO 14**: Left Driver Enable (L_EN / R_EN)
*   **GPIO 25**: Right Motor PWM Forward (L_PWM)
*   **GPIO 26**: Right Motor PWM Reverse (R_PWM)
*   **GPIO 27**: Right Driver Enable (L_EN / R_EN)
*   **GPIO 34**: Echo Pin (Front HC-SR04 Sonar)
*   **GPIO 35**: Trigger Pin (Front HC-SR04 Sonar)

### 3. Servo Controller Node (ESP32)
*   **GPIO 21**: I2C SDA (Connected to PCA9685 SDA)
*   **GPIO 22**: I2C SCL (Connected to PCA9685 SCL)
*   **GPIO 19**: Hardware Output Enable (OE) (PCA9685 - active LOW)

### 4. AI Voice Node (ESP32-S3)
*   **GPIO 1**: I2S SDOUT (ES8311 DAC)
*   **GPIO 2**: I2S BCLK (ES8311 & INMP441)
*   **GPIO 3**: I2S WS / LRCK (ES8311 & INMP441)
*   **GPIO 4**: I2S SDIN (INMP441 Mic)
*   **GPIO 18**: UART Tx (Connected to Master GPIO 16)
*   **GPIO 19**: UART Rx (Connected to Master GPIO 17)
