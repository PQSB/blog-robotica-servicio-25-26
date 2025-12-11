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
    - Using BFS, the route to the nearest **frontier** point is obtained. In case there is no route (there are no more reachable frontier points), execution ends, otherwise, the variables necessary for navigation are initialised and moves on to **MOVE** state.
    
  - **MOVE:** The route calculated in **PLAN** is followed, updating the map whenever the robot has travelled a distance of **0.3 m** since the map must be updated with independent measurements. Once the route is completed, it moves on to **PLAN** state.
  
### MAP CONSTRUCTION:
Map construction is based in Baye's rule but using **log-odds** aproximation, which allows the robot to accumulate sensor measurements efficiently and stably. Each cell’s log-odds value is updated by adding positive increments for occupied observations and negative increments for free observation simplifying the updates to simple sums. These increments are calculated the following way:
```python
pobs = 0.9
L_obs = np.log(pobs/(1-pobs))

pfree = 0.3
L_free = np.log(pfree/(1-pfree))
```
The probability of occupancy can be recovered from the log-odds when needed using the


For map construction, two np arrays are used:
  - pixel_map:
  - prob_map:
  
### EXPLORATION AND ROUTE CONSTRUCTION:


### NAVIGATION:


## Difficulties:

  While developing the algorithm I found some difficulties:
  
  - 
  
  - 
  
  - 

## Execution videos:

- **Explore and map warehouse (using get_odom):**
- **Explore and map warehouse (using get_odom) x2:**



















