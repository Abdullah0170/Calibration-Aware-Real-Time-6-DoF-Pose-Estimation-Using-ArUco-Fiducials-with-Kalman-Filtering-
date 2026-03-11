# Calibration-Aware Real-Time 6-DoF Pose Estimation Using ArUco Fiducials with Kalman Filtering Enhancement

This project implements a **real-time 6-DoF pose estimation system** using **ArUco fiducial markers and a monocular camera**. The system integrates **camera calibration, distortion correction, and Kalman filtering** to improve measurement stability and reduce noise in pose estimation.

The framework estimates the **3D position and orientation (roll, pitch, yaw)** of a marker relative to a calibrated camera using the **Perspective-n-Point (PnP) algorithm**.
---
## Features

- Real-time **6-DoF pose estimation**
- **ArUco marker detection** using OpenCV
- **Camera calibration with chessboard pattern**
- **Lens distortion correction**
- **Kalman filter for translation smoothing**
- Distance and orientation error evaluation
- Low-cost monocular vision system
---
## System Overview

The system workflow:

1. Camera calibration using a chessboard pattern
2. Detection of ArUco markers in camera frames
3. Pose estimation using the **PnP algorithm**
4. Conversion of rotation vectors to **Euler angles (Roll, Pitch, Yaw)**
5. Kalman filtering to reduce frame-to-frame noise
6. Distance estimation using the translation vector
---
## Experimental Setup
The system was tested at different distances and angles to evaluate pose estimation accuracy.
**Test distances**
- 56.5 cm
- 75 cm
- 100 cm
- 150 cm
---
**Test angles**
- 0°
- 30°

Results show that **Kalman filtering significantly improves pose stability**, while errors increase with larger distances and viewing angles.
---
## Technologies Used
- Python
- OpenCV
- ArUco Marker Detection
- Kalman Filter
- Perspective-n-Point (PnP)
- Camera Calibration
---
## Applications
- Robotics navigation
- UAV positioning
- Augmented reality tracking
- Vision-based measurement systems
- Autonomous navigation
---
## System Flowchart

```mermaid
flowchart TD
    A([Start]) --> B[Load camera calibration]
    B --> C[Initialize ArUco detector]
    C --> D[Open camera]

    D --> E[Environment calibration]
    E --> F[Capture frames for calibration]
    F --> G[Detect marker and estimate pose]
    G --> H[Compute position noise and reference rotation]

    H --> I[Start main loop]

    I --> J[Capture frame]
    J --> K[Detect ArUco markers]

    K --> L{Marker detected}
    L -- No --> J
    L -- Yes --> M[Estimate pose using PnP]

    M --> N[Apply Kalman filter]
    N --> O[Compute relative rotation]
    O --> P[Convert to roll pitch yaw]
    P --> Q[Compute distance]

    Q --> R[Draw axis and marker]
    R --> S[Display ID position distance orientation]

    S --> T{Press q to exit}
    T -- No --> J
    T -- Yes --> U([End])
