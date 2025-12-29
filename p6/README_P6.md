# P6 - Marker Based Visual Loc

**Date:** 29/12/2025

**Author:** Andrés Galea Torrecilla

## Algorithm details:
The goal of this exercise is to estimate the position and orientation (pose) of a robot in a 2D space by detecting and analyzing visual markers, specifically AprilTags.

### APRILTAG DETECTION AND POSE ESTIMATION:
To detect AprilTags and estimate the robot pose the following procedure is used:
1)  Detect all AprilTags present in the camera image.
2)  Filter detected apriltags to keep the closest one.
3)  Highlight the selected tag in the image for visualization.
4)  Use **cv2.solvePnP** together with the known 3D coordinates of the tag corners to compute the robot pose (x, y, yaw).

-  In case there are no apriltag in the image, the robot pose estimation is updated using odometry increments.
-  Pose estimation can only start after the robot has seen at least one tag, since an initial absolute reference is required.

#### APRILTAG DETECTION:
For apriltag the following functions are used:
- **detect_apriltags:** returns all the apriltags detected in the image.
- **filter_closest_apriltag:** returns the closes apriltag to the robot (the biggest one in the image).

#### POSE ESTIMATION:
When the robot detects an AprilTag in the image, the **calculate_robot_pose** function calculates the estimated pose of the robot. The function requires wtag, pix_corners, K, dcoefs, tag_corners
The function requires the following parameters:
- tag location in the world reference system.
- tag corners coordinates in pixel coordinates.
- K.
- distortion coefficients.
- tag corners coordinates in the tag reference system.

To do this, the method is formulated as a sequence of coordinate‑frame transformations. The goal is to get:

**robot2world = tag2world · camera2tag · robot2camera**

- ***robot2camera:***
  
  Calculated as the inverse of the camera2robot matrix obtained from the SDF. It is used to move from the robot reference frame to the camera reference frame. This transformation is fixed and depends only on how the camera is mounted on the robot.

- ***camera2tag:***
  
  Calculated as the inverse of the tag2camera matrix obtained from **cv2.solvePnP**. It is used to move from the camera reference frame to the tag reference frame. Since the tag coordinate system used by solvePnP does not match the tag coordinate system defined in the world, an additional rotation is applied to align both frames.

- ***tag2world:***
  
  Constructed from the known position and orientation of the tag in the world reference frame. It is used to move from the tag reference frame to the world reference frame and only depends on how the tag is placed in the environment.

### NAVIGATION:
For navigation, a **bump & go** exploration algorithm has been implemented using laser information and a state machine.

To extract the most relevant laser information for making movement decisions the laser data is divided into three key sectors:

- **Front sector:** to detect obstacles in the direction of travel.
- **Right sector and Left sector:** to decide which way to turn when an obstacle is detected.

The state machine used consists of two main states:

  - **FORWARD:** The robot moves in a straight line as long as the front sector is clear. When an obstacle is detected it moves to **TURN** state.

  - **TURN:** When the laser detects an obstacle in front, the robot stops moving forward and turns for a random amount of time (between 0.5 s and 1.2 s). The direction of the turn is decided by comparing the lateral distances, so that the robot tends to turn toward the clearer side. Once the turn is complete, it returns to the **FORWARD** state.

## Difficulties:

  While developing the algorithm I found some difficulties:
  
  - 
  
  -  
  
  - 

## Execution video:
- **Normal version:** 

