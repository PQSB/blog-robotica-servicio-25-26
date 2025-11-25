# P4 - Amazon Warehouse

**Date:** 25/11/2025

**Author:** Andrés Galea Torrecilla

## Algorithm details:
Implement the logic that allows a logistics robot to deliver shelves to the required place by making use of the location of the robot.

### Key states:
To simplify planning, two arrays are saved, one with the positions of the shelves and another with the locations where they should be moved.
The execution is divided into the following stages:

  - **PLANNING:** The robot's current position is obtained and it is checked whether the robot has the platform raised, in which case the destination position for that shelf is selected. Otherwise, the corresponding target shelf is selected. The route to the destination position is then calculated and the next step is taken. If the route cannot be created, the process ends.
  To plan, the **create_route** function is called, which is responsible for creating the plan. If creation fails, the processing time is increased until a maximum is reached, in which case the planning is considered a failure.

  - **FOLLOW_ROUTE:** Reactive control is performed by position, selecting the points on the calculated route as target points (when one is reached, the next one is selected). To do this, the **calculate_v** function is used, which returns the linear and angular velocities (wheel rotation in the case of Ackerman steering) calculated using the position and orientation error obtained from the difference between the position of the robot and the corresponding route waypoint. Once the destination has been reached, the system checks whether the platform is raised, in which case it moves to the **LEAVE_SHELF** state. Otherwise, it moves to the **PICK_SHELF** state.
  
  - **PICK_SHELF:** The platform is raised to lift the shelf, then the shelf is removed from the map by marking its pixels as free using the **remove_shelf** function, since while it is raised, the shelf will no longer be an obstacle. Finally, the next target for shelf droping is selected and the state is returned to **PLANNING**.
  
  - **LEAVE_SHELF:** The platform is lowered to leave the shelf, then the shelf is added to the map by marking corners as occupied using the add_shelf function, as it must be considered an obstacle again. Finally, the next target shelf is selected and the state is returned to **PLANNING**.

### Planner:
Different sections of information provided by the lasers are used depending on their application. The information is filtered, retaining only valid values.

### Mask creation for state validation:


### Using different geometries:


### Holonomic vs Ackerman main differences:

## Difficulties:

  While developing the algorithm I found some difficulties:
  
  - 
  
  - 
  
  - 

  - 

## Execution videos:

- **Holonomic using different geometries:** https://urjc-my.sharepoint.com/:v:/g/personal/a_galea_2022_alumnos_urjc_es/EcUxpmUzKpZDnxaXRFpBjMIBHboN-38nUtGyEpBGpiNtUg?nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D&e=TMBldg

- **Ackerman using different geometries:** https://urjc-my.sharepoint.com/:v:/g/personal/a_galea_2022_alumnos_urjc_es/ESwTzxt6guxHmWKZvV5JR_MBICKcvwqpdpUpqWxpoExcLQ?nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D&e=ejEfhz








