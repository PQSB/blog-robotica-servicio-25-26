# P4 - Amazon Warehouse

**Date:** 25/11/2025

**Author:** Andrés Galea Torrecilla

## Algorithm details:
Implement the logic that allows a logistics robot to deliver shelves to the required place by making use of the location of the robot.

### Key states:
  - **PLANNING:** 

  - **FOLLOW_ROUTE:** 
  
  - **PICK_SHELF:** 
  
  - **LEAVE_SHELF:** 
### Planner:
Different sections of information provided by the lasers are used depending on their application. The information is filtered, retaining only valid values.

### Mask creation for state validation:
The distance to the line of cars is calculated in different ways. During the alignment phase, it is calculated using SVD, as this is more robust for correct alignment. However, during the gap search, the distance obtained as the median of a certain sector of the right side laser is used.

### Using different geometries:
The orientation is calculated using SVD. In the alignment phase, it is used with the lateral sensor data, and in the subsequent parking manoeuvre phases, it is used with the reference chosen to perform them.

### Holonomic vs Ackerman differences:

## Difficulties:

  While developing the algorithm I found some difficulties:
  
  - 
  
  - 
  
  - 

  - 

## Execution videos:

- **Holonomic using different geometries:** https://urjc-my.sharepoint.com/:v:/g/personal/a_galea_2022_alumnos_urjc_es/EcUxpmUzKpZDnxaXRFpBjMIBHboN-38nUtGyEpBGpiNtUg?nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D&e=TMBldg

- **Ackerman using different geometries:** https://urjc-my.sharepoint.com/:v:/g/personal/a_galea_2022_alumnos_urjc_es/ESwTzxt6guxHmWKZvV5JR_MBICKcvwqpdpUpqWxpoExcLQ?nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D&e=ejEfhz
