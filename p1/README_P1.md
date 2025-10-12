# P1 - Localized Vacuum Cleaner

**Date:** 12/10/2025

**Author:** Andrés Galea Torrecilla

## Algorithm details:
The goal is to program BSA algorithm for a localized vaccum cleaner so that it cleans as much of the map as possible.

### 0. Map Obstacles Dilatation:
Once the array map is obtained, and before performing any other operations, the obstacles are dilated using OpenCV's dilate function with a *(9,9) kernel* and *2 iterations* (values determined after extensive testing) in order to ensure safer navigation.

### 1. Map Registration:
The objective of this phase is to optain an ecuation that allows coordiates transformation from:

- gazebo &rArr; pixel map
- pixel map &rArr; gazebo

To calculate the *gazebo &rArr; pixel map* transformation:
- Get 11 coordinates from gazebo and their corresponding coordinates in the pixel map.

- For every gazebo point and its corresponding pixel point create the equations with these points and add them to A and B matrices.

- Use **np.linalg.lstsq(A,B)** to solve this system using the least squares method and get best transformation that approximates all those points as closely as possible.

To calculate the *pixel map &rArr; gazebo* transformation assemble the resulting parameters into a matrix and invert it using **np.linalg.inv(t)**.

At the end of the phase, he transformation parameters for both directions (gazebo &rArr; pixel map and pixel map &rArr; gazebo) are available, and can be used with the following equations (note: *gazebo &rArr; pixel map* pixel coordinates must be rounded):

- x' = a·x + b·y + e

- y' = c·x + d·y + f

### 2. Navigation Grid Creation

### 3. BSA Coverage Algorithm Route Planning

### 4. Route Reactive Piloting

### Obtained results:

## Difficulties:

While developing the algorithm I found some difficulties:
- Finding the best ecuation so that the error between the current and the estimate location is low enough.

- Making the obstacles big enough so that the robot avoids them the best way possible, but without losing too much ground to clear.

## Execution video:






