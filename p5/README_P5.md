# P5 - Laser Mapping

**Date:** 11/12/2025

**Author:** Andrés Galea Torrecilla

## Algorithm details:
Implement a navigation algorithm that allows a robot to autonomously explore a warehouse environment while generating an accurate map of the area using LIDAR sensor data.

### Key states:
  - **INIT_MAP:** Mapping begins by updating the map for the first time and moves on to **PLAN** state. This state is only executed once.
  
  - **PLAN:** The following procedure is followed:
    - The current **grid_map** is overwritten with a new one that takes into account the changes made to the map.
    - The **frontier** points of the new grid_map are obtained.
    - The robot's position is calculated in **grid_map** coordinates.
    - Using BFS, the route to the nearest **frontier** point is obtained. In case there is no route (there are no more reachable frontier points), execution ends, otherwise, the variables necessary for navigation are initialised and the process moves on to **MOVE** state.
    
  - **MOVE:**
  
### MAP CONSTRUCTION:


### EXPLORATION:


### NAVIGATION:


## Difficulties:

  While developing the algorithm I found some difficulties:
  
  - 
  
  - 
  
  - 

## Execution videos:

- **Explore and map warehouse (using get_odom):**
- **Explore and map warehouse (using get_odom) x2:**














