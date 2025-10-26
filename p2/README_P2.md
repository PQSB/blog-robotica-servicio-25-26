# P2 - Rescue People

**Date:** 26/10/2025

**Author:** Andrés Galea Torrecilla

## Algorithm details:
Program a drone to assist in a search and rescue mission on the high seas.

### Key states:
  - **TAKE_OFF:** Take off the drone and plan the route to follow to search for survivors. If planning has been possible, navigation is configured and the next state begins. On the other hand, if it has not been possible to plan the route, move directly to **LANDING** so as not to navigate without a route.

  - **NAVIGATING_TO_ZONE:** Cheks all the time if the drone has arrived to the searching zone. When the drone arrives, navigation is configured and the next state begins.
  
  - **SEARCHING_SURVIVORS:** The drone follows the pre-planned route, attempting to detect people using the OpenCV Haar cascade detector *haarcascade_frontalface_default.xml*. To improve accuracy (since this detector requires the face to have very little orientation), all possible image rotations are tested in **20-degree** increments. When a new survior is found his the drone stores his coordinates. Once the route has been completed or the drone's battery level is below **22%**, navigation is configured and the next state begins.
  
  - **NAVIGATING_TO_BASE:** Cheks all the time if the drone has arrived to the base. When the drone arrives the next state begins.
  
  - **LANDING:** Land the drone at its current position and display the location of all survivors found in GPS coordinates.

### Planification:
The planning is done with **create_searching_route(origin_location, step_x, step_y, side_length)**. This function generates a zigzag or serpentine pattern within a square area of size **side_length** centred on **origin_location**. Parameters **step_x** and **step_y** determine the number of intermediate points between displacements.

### Navigation:
For navigation, only position control is used via the **HAL.set_cmd_pos(x, y, z, az)** function. The most relevant functions used for navigation are the following:
- **drone_arrived(cur_loc, dst_loc, threshold):** returns whether the drone has reached a position or not by calculating the distance and comparing it with a threshold.

- **calculate_orientation(dst_location):** returns the target angle (in radians) aligned with the movement.

- **move_drone_to(target, height):** configure the navigation parameters (target, height and orientation) and start navigation using *calculate_orientation* and *HAL.set_cmd_pos* functions.

### Survivor detection:

### Battery:

## Difficulties:

  While developing the algorithm I found some difficulties:
  
  - 
  
  - 
  
  - 

  - 

## Execution video:

- **Normal version:**

- **Accelerated version:**












