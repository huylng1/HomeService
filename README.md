# Home Service Robot Project Overview
Within this repository lies the submission for the "Home Service Robot" project, an integral part of the UDACITY Robotics Software Engineer program, more specifically, the Home Service Robot course. This project is a practical application of the skills acquired throughout the program, focusing on the deployment of a home service robot assigned with the task of collecting an object and delivering it to a designated location.
### 1. Localization, Mapping, and Navigation: Challenges and Insights
### Localization:
#### Challenges:
##### Sensor Fusion Complexity: 
Integrating data from various sensors for robust localization introduces challenges in managing sensor fusion complexity.
##### Particle Set Management: 
Efficiently managing a large set of particles in Monte Carlo Localization (MCL) poses computational challenges.
##### Dynamic Environments: 
Adapting to dynamic environments requires adaptive strategies, such as dynamic re-sampling.
##### Parameter Tuning: 
Achieving optimal performance demands careful tuning of MCL parameters.

### Mapping:
#### Challenges:
##### Adapting to Diverse Environments: 
SLAM implementation faces challenges in adapting to diverse and dynamic environments.
##### Sensor Noise: 
Addressing sensor noise is essential for accurate mapping.
##### Real-world Tuning: 
Fine-tuning SLAM algorithms for real-world scenarios presents ongoing obstacles.
##### Parameter Refinement: 
Continuous refinement of parameters is imperative to address issues like drift and loop closures.

### Navigation:
#### Challenges:
##### Parameter Tuning: 
Achieving smooth and collision-free navigation requires careful tuning of parameters.
##### Dynamic Obstacles: 
Handling dynamic obstacles poses challenges in path planning.
##### Accurate Localization: 
Ensuring accurate robot localization is crucial for effective navigation.

--------------------------------------------------------------------------------

### 2. Project Components
### SLAM Mapping
To initiate SLAM testing, leverage the test_slam.sh script provided. Execute this script to launch essential components for conducting manual SLAM tests, aiming to create a functional map of the environment. This map is critical for subsequent tasks related to localization and navigation.
### Localization and Navigation
Included in the toolkit is the test_navigation.sh script for manual navigation testing. This script empowers the robot to manually navigate by responding to 2D Nav Goal commands. The pick_objects.sh script adds complexity by sending multiple goals for the robot to accomplish. The robot's journey involves reaching the designated pickup zone, confirming arrival, waiting for 5 seconds, progressing to the assigned drop-off zone, and confirming arrival once again.
### Home Service Functions
To infuse home service capabilities, employ the add_marker.sh script. This script orchestrates the publication of a marker to rviz, initially positioning it at the pickup zone. After an interval of 5 seconds, the marker gracefully fades away, only to reappear at the drop-off zone after an additional 5 seconds. The overarching conductor of this symphony is the home_service.sh script, expertly conducting all necessary nodes. The simulated home service robot gracefully follows these choreographed steps:

1. Unveil the marker initially at the pickup zone.
2. Conceal the marker upon the robot's arrival at the pickup zone.
3. Artfully simulate a 5-second pause for the pickup.
4. Present the marker at the drop-off zone with finesse once the robot gracefully reaches its destination.

## Directory structure
```
├── add_markers                                   # add_markers package        
│   ├── src
│   │   ├── add_markers.cpp                       
│   │   ├── add_markers_State.cpp                  # for testing add_markers node purpose
├── map                                           # map and world file       
├── pick_objects                                  # pick_objects package     
│   ├── src                                       
│   │   ├── pick_objects.cpp                      
├── rvizConfig                                    # rvizConfig file for home service robot demo     
│   ├── home_service.rviz                         
├── scripts                                       # shell scripts folder
│   ├── add_marker.sh                             
│   ├── home_service.sh                           
│   ├── pick_objects.sh                           
│   ├── test_navigation.sh                        
│   ├── test_slam.sh                              
├── slam_gmapping                                 
├── turtlebot                                    
├── turtlebot_interactions                      
├── turtlebot_simulator                           
├── CMakeLists.txt                                # make file
```
- [add_markers.cpp](/catkin_ws/src/add_markers/src/add_markers.cpp): This C++ script facilitates communication with the `pick_objects` node and manages marker visibility, simulating object pick-up and drop-off events.
- [pick_objects.cpp](/catkin_ws/src/pick_objects/src/pick_objects.cpp): A C++ script tailored to interact with the `add_markers` node, commanding the robot to pick up objects.
- [home_service.rviz](/catkin_ws/src/rvizConfig/home_service.rviz): The `home_service.rviz` file, integral to the rvizConfig, configures the visualization for the home service robot demo, including marker display options.
- [test_navigation.sh](/catkin_ws/src/scripts/test_navigation.sh): A shell script that deploys a TurtleBot, defines two distinct goals, and assesses the robot's ability to reach and orient itself concerning these goals.
- [test_slam.sh](/catkin_ws/src/scripts/test_slam.sh): A shell script responsible for deploying a TurtleBot, guiding it through keyboard commands, interacting with a SLAM package, and visualizing the generated map in `rviz`.
- [add_marker.sh](/catkin_ws/src/scripts/add_marker.sh): A shell script deploying a TurtleBot, creating a virtual object with markers in `rviz`, and showcasing marker-related functionalities.
- [pick_objects.sh](/catkin_ws/src/scripts/pick_objects.sh): A shell script deploying a TurtleBot, communicating with the ROS navigation stack, and autonomously sending successive goals for the robot to achieve.
- [home_service.sh](/catkin_ws/src/scripts/home_service.sh): A shell script designed to deploy a TurtleBot, simulating a comprehensive home service robot capable of navigating to pick up and deliver virtual objects.
