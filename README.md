# RL-Homework-2
# Project overview
The goal of this project is to dynamically control a 7 DoF robot manipulator arm in the Gazebo environment to ensure it follows a desired trajectory both in the joint space and the operational space. The package contains the configurarion, launch and control file.  
# Installation 
The first action is the setup of the workspace,after cloning the repository in the desired folder 
1.Clone the repository 

`  $ git clone ///repository`

2.Build the packages

`$ colcon build --packages-select ros2_iiwa ros2_kdl_package`

3.Source the workspace 

$  source install/setup.bash

# Launching the robot 
The robot can be controlled with 3 command interfaces
    • Position 
    • Velocity 
    • Effort 
If not explicitly specified it will run with the position one 
So to launch the robot with the position interface the command is the following 

`$ ros2 launch  iiwa_bringup iiwa.launch.py `

To select a velocity interface the command is the following 

`$ ros2 launch  iiwa_bringup iiwa.launch.py`

