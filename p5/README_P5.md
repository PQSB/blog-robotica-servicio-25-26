# P5 - Laser Mapping

**Date:** 11/12/2025

**Author:** Andrés Galea Torrecilla

## Algorithm details:
Implement a navigation algorithm that allows a robot to autonomously explore a warehouse environment while generating an accurate map of the area using LIDAR sensor data.

### Key states:
  - **INIT_MAP:** Mapping begins by updating the map for the first time.
  
  - **PLAN:** The following procedure is followed:
    - The current **grid_map** is overwritten with a new one that takes into account the changes made to the map.
    - The **frontier** points of the new grid_map are obtained.
    - The robot's position is calculated in **grid_map** coordinates.
    - Using BFS, the route to the nearest border point is obtained.
    
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

- **Explore and map warehouse:**












