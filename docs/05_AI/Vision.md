# Camera Vision & Face Tracking

## Purpose
This document details the vision tracking capabilities of the ESP32-CAM node, including face tracking and color tracking.

## Face Tracking Pipeline
The ESP32-CAM captures raw frames and uses a local color-thresholding or face-detection algorithm (using the ESP-WHO library) to output target offset coordinates:

```
 [ OV2640 Sensor ] ──> [ Frame Capture ] ──> [ Face Detection (ESP-WHO) ]
                                                       │
                                            Is Target Detected?
                                             ├── Yes ──> [ Calculate Error Angle ] ──> [ Update Neck Servo ]
                                             └── No  ──> [ Center Head ]
```

## Limitations
Due to the processing constraints of the ESP32-CAM, local face detection is limited to **5–8 frames per second** at a resolution of QVGA (320x240). Advanced vision tasks (such as object classification or spatial mapping) are offloaded to the Web Dashboard or a companion processor.
