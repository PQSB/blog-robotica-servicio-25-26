# P3 - Autoparking

**Date:** 07/11/2025

**Author:** Andrés Galea Torrecilla

## Algorithm details:
Program an autonomous car to park itself, specifically on a street where other vehicles are already parked.

### Key states:
  - **ALIGN:** In this state, the car starts from its initial position and moves until it reaches the desired safety distance and orientation relative to the row of cars. To do this, a controller is used to regulate both the orientation and the safety distance.

  - **SEARCH:** To search for a parking space, the vehicle moves along the street at a constant speed and, when the side laser detects a valid distance for parking, it records the distance travelled, detecting the valid distance so that if it matches the minimum space size value, it is a valid space.
  
  - **REFERENCE_SEARCH:** The first time the algorithm detects a valid lateral distance value for parking, it checks whether the rear laser of the car is detecting anything, since if so, it will already have a rear reference for parking. If, when this state is reached, there is no rear reference 
  
  - **FRONT_ALIGN:** If, when starting the manoeuvre, the rear laser detects an obstacle (since once the gap has been detected, the vehicle moves forward a safe distance before starting the manoeuvre), it reverses until the obstacle is no longer detected.
  
  - **PARKING_ENTRY:** This step consists of entering the gap. Depending on whether the reference is in front or behind, a different entry angle is used in order to align correctly.

  - **PARKING_ADJUST:** Turn in the opposite direction to the previous step until the desired orientation is achieved or a collision with the car behind may occur.

  - **PARKING_STRAIGHTEN:** The car straightens up by moving forward slowly and finishing correcting its orientation. The process stops when the desired orientation is achieved or when there is a risk of colliding with the car in front.

### Laser Data:
Different sections of information provided by the lasers are used depending on their application. The information is filtered, retaining only valid values.

### Distance calculation:
The distance to the line of cars is calculated in different ways. During the alignment phase, it is calculated using SVD, as this is more robust for correct alignment. However, during the gap search, the distance obtained as the median of a certain sector of the right side laser is used.

### Orientation calculation:
The orientation is calculated using SVD. In the alignment phase, it is used with the lateral sensor data, and in the subsequent parking manoeuvre phases, it is used with the reference chosen to perform them.

## Difficulties:

  While developing the algorithm I found some difficulties:
  
  - Calculate the orientation relative to the wall carefully.
  
  - Choose the right reference point for alignment during parking manoeuvres.
  
  - Combine information from different lasers depending on the situation

## Execution videos:

- 

- 







