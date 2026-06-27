# Audio & Voice Subsystem

## Purpose
This document details the audio hardware configuration used for voice recording and playback on the AI Node.

## Components
1.  **INMP441 Omnidirectional Microphone**: Digital microphone with a 24-bit I2S interface, providing high SNR (61 dBA) and low power consumption.
2.  **ES8311 Low-Power Mono DAC**: Decodes digital audio streams from the ESP32-S3 over I2S and drives the amplifier.
3.  **NS4150 Mono Audio Power Amplifier**: A 3W class-D amplifier that drives the speaker.
4.  **8-Ohm 3W Speaker**: Compact speaker mounted inside the 3D-printed head.

## Schematic Layout
```
 [ INMP441 Mic ] ─── I2S In ───┐
                               ├──> [ ESP32-S3 AI Node ]
 [ ES8311 DAC  ] ─── I2S Out ──┘
       │ (Differential Analog)
       ▼
 [ NS4150 Amp  ] ─── (3W Output) ───> [ 8-Ohm Speaker ]
```

## Performance Specs
*   **Sample Rate**: 16 kHz (standard for speech recognition).
*   **Bit Depth**: 16-bit.
*   **Audio Delay**: Voice acquisition to transmission buffer delay is < 50 ms.
