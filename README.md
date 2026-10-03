# rrt-star-ugv-path-planning
Vision-based path planning for a ground robot: OpenCV obstacle detection + RRT* with path smoothing, from a single overhead image.
# Vision-Based Path Planning with RRT*

A complete pipeline that takes a single overhead photo of an arena and
computes a collision-free path for a ground robot (UGV).

![result](images/result.png)

## Features
- Start (green) and goal (red) marker detection in HSV color space
- Obstacle detection with grayscale thresholding, morphology, and connected components
- Free-space map restricted to the region reachable from the start
- Robot-radius-aware safety map using a distance transform
- RRT* planner with goal bias, best-parent selection, and rewiring
- Greedy line-of-sight path smoothing
- Diagnostic plots: free space, safe area, RRT* tree, cost convergence

## How it works
Image -> Marker detection -> Obstacle detection -> Free space
-> Distance transform -> RRT* -> Smoothing -> Waypoints

## Results
| Metric | Value |
|---|---|
| Obstacles detected | [..] |
| Nodes in tree | [..] |
| Planning time | [..] s |
| Raw path length | [..] px |
| Smoothed path length | [..] px |

## Usage
1. Open `notebook.ipynb` in Google Colab
2. Run all cells
3. Upload your arena image when prompted
4. The waypoints (x, y) are printed in pixels

## Parameters
| Name | Value | Meaning |
|---|---|---|
| ROBOT_RADIUS | 14 px | Minimum clearance from obstacles |
| DARK_THRESHOLD | 110 | Gray level below which a pixel is an obstacle |
| max_iter | 4000 | RRT* iterations |
| step | 45 px | Maximum extension per iteration |
| rewire_radius | 90 px | Neighborhood for rewiring |

## Limitations and future work
- Fixed threshold is sensitive to lighting
- Output is in pixels; camera calibration is needed for real units
- Robot is modeled as a circle with no kinematic constraints
- Planned: Otsu/adaptive thresholding, homography calibration,
  Informed RRT*, spline smoothing

## Tech stack
Python, OpenCV, NumPy, Matplotlib
