# AI & Voice Node

## Purpose
The AI Node processes voice interaction, handles conversational flows via the Xiaozhi framework, and interfaces with cloud LLM systems using the Model Context Protocol (MCP).

## Hardware Used
*   **MCU**: ESP32-S3-WROOM-1 (with 8MB PSRAM).
*   **DAC/Codec**: ES8311 I2S Audio Codec.
*   **Microphone**: INMP441 I2S digital omnidirectional microphone.
*   **Speaker**: 3W 8-Ohm Speaker.

## GPIO Mapping
| GPIO Pin | Pin Function | Target Component |
| :--- | :--- | :--- |
| **GPIO 1** | I2S Serial Data Out (SDOUT) | ES8311 DAC SDIN |
| **GPIO 2** | I2S Serial Clock (BCLK) | ES8311 / INMP441 BCLK |
| **GPIO 3** | I2S Word Select (LRCK) | ES8311 / INMP441 WS |
| **GPIO 4** | I2S Serial Data In (SDIN) | INMP441 SD Out |
| **GPIO 18**| UART Tx (To Master Rx2) | Master Node GPIO 16 |
| **GPIO 19**| UART Rx (To Master Tx2) | Master Node GPIO 17 |

## Speech Pipeline Block Diagram
```
  [ INMP441 Mic ] ──(I2S Digital)──> [ ESP32-S3 Node ]
                                            │
                                    (VAD & Wake Word)
                                            │ (Wi-Fi TCP)
                                            ▼
                                   [ Cloud TTS / LLM ]
                                            │ (Wi-Fi TCP)
                                            ▼
  [ ES8311 Codec ] <──(I2S Digital)── [ ESP32-S3 Node ]
          │
  [ 3W Speaker ]
```

## Failure Cases & Recovery
*   **High Speech Latency**: If the cloud response takes longer than 2.0 seconds, the AI Node plays a local audio response (e.g. "Processing command...") to update the user.
