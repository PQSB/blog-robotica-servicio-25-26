# P2 - Rescue People

**Date:** 26/10/2025

**Author:** Andrés Galea Torrecilla

## Algorithm details:
Program a drone to assist in a search and rescue mission on the high seas. To do so, a **FSM** is used.

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

### FOV calculation:
The FOV is calculated as follows:
- Calculate the **meter per pixel scale** at 3.15 m high by measuring a distance in gazebo and then counting the number of pixels corresponding to that length.
- Knowing the total witdh of the image in pixels calculate the corresponding with in meters using the **meter per pixel scale**.
- FOV is calculated using the formula:
```math
\text{FOV}_h = 2 \cdot \arctan \Bigg( \frac{L_{\text{total}}}{2 H} \Bigg)
```
### Survivor detection:

The following functions are used in the order indicated for the survivor detection process.
- **1: search_and_display_faces(img, rotation_angle):** this function returns an array with the central pixels of every detected face as well as an image with the detected faces marked. It works as follows:
  - A blue colour filter is used to remove the sea from the image and improve the accuracy of the Haar cascade.
  
  - The corresponding rotation is applied (for each image, all possible rotations are tested in increments of 20 degrees).

  - The Haar cascade is used to detect whether there are faces in the image. If there are, the output is used to calculate the pixels at the centre of each face.

  - If any rotation has been applied, it is reversed to obtain the real pixels at the centre of each detected face.

  - Return the centre array and the marked image.

- **2: get_image_to_world_offset(face_center, image_shape, height, yaw, fov):** this function is used for every face detected in the centre array and returns the x and y offset of the detected face from the centre of the imagen in gazebo coordinates. It works as follows:
  - The metre-per-pixel scale is calculated using the previously calculated FOV. 

  - The offset in pixels from the centre of the image to the detected face is calculated and converted to metres by using the m/px scale.

  - The offset in metres is adjusted according to the coordinate system and the orientation of the drone.
  
  - Return x, y offsets in gazebo coordinates.

- **3: is_new_survivor(current_position, detected_list, threshold):** this function returns if the provided coordinates are already stored in the suvivors array by comparing the distance between the current location and the stored locations with a threshold. Only if the distance is greater than the threshold the surivor will be added to the list.

- **4: get_gps_from_drone(drone_loc):** this function returns the provided gazebo coordinates in GPS coordinates.

### Battery:
To calculate the battery life, a maximum flight time is set and the percentage of that time that has elapsed is calculated.

## Difficulties:

  While developing the algorithm I found some difficulties:
  
  - 
  
  - 
  
  - 

  - 

## Execution video:

- **Normal version:**

- **Accelerated version:**



















