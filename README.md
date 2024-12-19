# ArUco Marker Detection and Pose Estimation

This project implements real-time ArUco marker detection and pose estimation using OpenCV. The system can detect 6x6 ArUco markers through a webcam feed, visualize their corners, and estimate the camera pose relative to the markers.

## Prerequisites

- Python 3.x
- OpenCV (cv2) with ArUco module
- NumPy

## Installation

```bash
pip install opencv-python
pip install numpy
```

## Camera Calibration

Before running the system, you need to have a camera calibration file (`calibrationFileName.xml`) that contains:
- Camera matrix
- Distortion coefficients
- Rotation matrix
- New camera matrix

The calibration file should be in the same directory as the main script.

## Features

- Real-time ArUco marker detection (6x6_250 dictionary)
- Corner detection and visualization
- Camera pose estimation
- 3D axis visualization
- Homography computation
- Perspective warping

## Usage

1. Ensure your webcam is connected and accessible
2. Run the script:
   ```bash
   python aruco_pose_estimation.py
   ```
3. Point your camera at an ArUco marker
4. The system will:
   - Draw blue lines around detected markers
   - Label the corners (1-4)
   - Display the coordinate axes when a marker is detected
   - Show the transformed perspective view

Press 'q' to quit the application.

## Key Components

### Marker Detection
The system uses OpenCV's ArUco module to detect markers in the video feed. It specifically uses the 6x6_250 dictionary, which can generate up to 250 unique markers.

### Pose Estimation
The system performs two types of pose estimation:
1. Using ArUco's built-in pose estimation
2. Custom pose estimation from homography matrix

### Visualization
- Blue lines outline the detected marker
- Corner numbers are displayed at each vertex
- 3D coordinate axes show the marker's orientation
- Perspective-corrected view of the marker area

## Parameters

- `markerLength`: Physical size of the marker (default: 0.25 units)
- `dictionary`: ArUco dictionary type (DICT_6X6_250)
- Camera parameters are loaded from the calibration file

## Notes

- Ensure adequate lighting for reliable marker detection
- The marker should be clearly visible and not too far from the camera
- Camera calibration significantly impacts pose estimation accuracy

## Troubleshooting

1. If markers aren't being detected:
   - Check lighting conditions
   - Ensure marker is within camera view
   - Verify marker is from the correct dictionary

2. If pose estimation is inaccurate:
   - Verify camera calibration file
   - Check marker size parameter
   - Ensure marker is printed at correct physical size
