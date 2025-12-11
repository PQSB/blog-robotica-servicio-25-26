# P5 - Laser Mapping

**Date:** 11/12/2025

**Author:** Andrés Galea Torrecilla

## Algorithm details:
Implement a navigation algorithm that allows a robot to autonomously explore a warehouse environment while generating an accurate map of the area using LIDAR sensor data.

### PROCESS LASER DATA
The **laser_data_to_points** function is used to filter valid values and convert them into pixel coordinates, as well as to indicate whether or not the beam collided.

### MAP CONSTRUCTION:
- Map construction is based in Baye's rule but using **log-odds** aproximation, which allows the robot to accumulate sensor measurements efficiently and stably. Each pixel's log-odds value is updated by adding positive increments for occupied observations and negative increments for free observation simplifying the updates to sums. To avoid excessive probabilistic inertia, increments saturate when they reach a maximum value. These increments are calculated the following way (obstacle increment is greater, since it should be easier to mark a free pixel as occupied than an occupied pixel as free):
```python
pobs = 0.9
L_obs = np.log(pobs/(1-pobs))

pfree = 0.3
L_free = np.log(pfree/(1-pfree))
```
- There are two np arrays involved in map construction (both maps are updated each time):
  - **pixel_map:** stores integer values from **0 (black/no doubt obstacle) to 255 (white/no doubt free)** for every pixel. This is the map showed.
  
  - **prob_map:** stores the log-odds value of every pixel.

- To convert log-odds values to 0 to 255 pixel values, the function **calculate_pixel_color** which calculates the probability belonging to each log-odds value and then turns that probability into a 0-255 integer value.

- The map is updated using valid laser values converted into pixel coordinates. This allows an increase in occupancy or freedom to be added according to the distance measured by the laser.
For the map to update correctly, it is also necessary to add an increase in freedom to all intermediate pixels between the robot's position and the positions measured by the laser. This is done using the **Bresenham** algorithm.

### EXPLORATION AND ROUTE CONSTRUCTION:
- The exploration is carried out by **frontier exploration**, which allows the robot to always advance to an area that will provide new information to the map, as well as determine when the map is complete. To do so,  a **grid_map** is created from pixel_map and its cells are marked as **FREE**, **OCCUPIED**, or **UNKNOWN** depending on the value of the pixels that compose them.

- To choose the frontier point to follow, the criterion of the robot's closet frontier (using Manhattan distance) has been used.

- The route is created using **BFS**, which returns a path in grid_map coordinates.

### NAVIGATION:
Navigation is carried out using grid coordinates, which provides greater safety during movement, since as soon as a pixel belonging to a grid cell has a value considered to be an obstacle, the entire cell is marked as an obstacle.

**V** and **W** velocities are calculated using simple controllers.

### KEY STATES:
  - **INIT_MAP:** Mapping begins by updating the map for the first time and the moving on to **PLAN** state. **INIT_MAP** state is only executed once.
  
  - **PLAN:** The following procedure is followed:
    - The current **grid_map** is overwritten with a new one that takes into account the changes made to the map.
    - The **frontier** points of the new grid_map are obtained.
    - The robot's position is calculated in **grid_map** coordinates.
    - Using BFS, the route to the nearest **frontier** point is obtained. In case there is no route (there are no more reachable frontier points), execution ends, otherwise, the variables necessary for navigation are initialised and moves on to **MOVE** state.
    
  - **MOVE:** The route calculated in **PLAN** is followed, updating the map whenever the robot has travelled a distance of **0.3 m** since the map must be updated with independent measurements. Once the route is completed, it moves on to **PLAN** state.

## Difficulties:

  While developing the algorithm I found some difficulties:
  
  - Finding the appropriate log-odds increments and saturation values.
  
  - Create grid maps propperly. 
  
  - Find and create routes to frontiers ponints propperly.

## Execution video:

```python
odom_type = ODOM
```
- **Explore and map warehouse (using HAL.getOdom):** https://urjc-my.sharepoint.com/:v:/g/personal/a_galea_2022_alumnos_urjc_es/IQBtJmmNXI9ZToJfRanBSInQAQmY0WP__keSbriHtOyfJtA?nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D&e=LO3LeT














































