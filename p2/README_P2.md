# P2 - Rescue People

**Date:** 26/10/2025

**Author:** Andrés Galea Torrecilla

## Algorithm details:
Program a drone to assist in a search and rescue mission on the high seas.

### Key states:
  - **TAKE_OFF:** Take off the drone and plan the route to follow to search for survivors. If planning has been possible, navigation is configured and the next stage begins. On the other hand, if it has not been possible to plan the route, move directly to **LANDING** so as not to navigate without a route.

  - **NAVIGATING_TO_ZONE:** Cheks all the time if the drone has arrived to the searching zone. When the drone arrives, navigation is configured and the next stage begins.
  
  - **SEARCHING_SURVIVORS:** The drone follows the pre-planned route, attempting to detect people using the OpenCV Haar cascade detector *haarcascade_frontalface_default.xml*. To improve accuracy (since this detector requires the face to have very little orientation), all possible image rotations are tested in **20-degree** increments. Once the route has been completed or the drone's battery level is below **22%**, navigation is configured and the next stage begins.
  
  - **NAVIGATING_TO_BASE:**
  
  - **LANDING:**

### Planification:

### Navigation:

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





