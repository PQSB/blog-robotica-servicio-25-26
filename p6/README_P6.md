# P6 - Marker Based Visual Loc

**Date:** 29/12/2025

**Author:** Andrés Galea Torrecilla

## Algorithm details:
The goal of this exercise is to estimate the position and orientation (pose) of a robot in a 2D space by detecting and analyzing visual markers, specifically AprilTags.

### APRILTAG DETECTION AND POSE ESTIMATION:



#### APRILTAG DETECTION:






#### POSE ESTIMATION:

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


