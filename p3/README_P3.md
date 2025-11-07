# P3 - Autoparking

**Date:** 07/11/2025

**Author:** Andrés Galea Torrecilla

## Algorithm details:
Program an autonomous car to park itself, specifically on a street where other vehicles are already parked.

### Key states:
  - **ALIGN:** In this state, the car starts from its initial position and moves until it reaches the desired safety distance and orientation relative to the row of cars. To do this, a controller is used to regulate both the orientation and the safety distance.

  - **SEARCH:** To search for a parking space, the vehicle moves along the street at a constant speed and, when the side laser detects a valid distance for parking, it records the distance travelled, detecting the valid distance so that if it matches the minimum space size value, it is a valid space.
  
  - **REFERENCE_SEARCH:** The first time the algorithm detects a valid lateral distance value for parking, it checks whether the rear laser of the car is detecting anything, since if so, it will already have a rear reference for parking. If, when this state is reached, there is no rear reference 
  
  - **FRONT_ALIGN:** 
  
  - **PARKING_ENTRY:**

  - **PARKING_ADJUST:**

  - **PARKING_STRAIGHTEN:**

### Laser Data:

### Distance calculation:

### Orientation calculation:

### Navigation:

### Parking place detection:

## Difficulties:

  While developing the algorithm I found some difficulties:
  
  - 
  
  - 
  
  - 

  - 

## Execution videos:

- 

- 



