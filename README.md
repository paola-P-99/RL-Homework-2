# RL-Homework-2
# Project overview
The goal of this project is to dynamically control a 7 DoF robot manipulator arm in the Gazebo environment to ensure it follows a desired trajectory both in the joint space and the operational space. The package contains the configurarion, launch and control file.  
# Installation 
The first action is the setup of the workspace,after cloning the repository in the desired folder 
1.Clone the repository 

`$ git clone  ... `

2.Build the packages

`$ colcon build --packages-select ros2_iiwa ros2_kdl_package`

3.Source the workspace 

`$  source install/setup.bash`

# Launching the robot 
The robot can be controlled with 3 command interfaces
    • Position 
    • Velocity 
    • Effort 
If not explicitly specified it will run with the position one 
So to launch the robot with the position interface the command is the following 

`$ ros2 launch  iiwa_bringup iiwa.launch.py `

To select the  velocity interface the command is the following 

`$ ros2 launch  iiwa_bringup iiwa.launch.py  command_interface:="velocity" robot_controller:="velocity_controller"`

To select the effort interface the command is the following 

`$ ros2 launch  iiwa_bringup iiwa.launch.py command_interface:="effort" robot_controller:=“effort_controller" `

To spawn the robot also in Gazebo  to the launch command above there must be added the following instruction 

` $ use_sim:=true`

# Running the controllers 
The controllers activated must be the same as the interface selected to ensure the proper visualization of the control action 
To run the controllers in position the command line is the following

` $ ros2 run ros2_kdl_package ros2_kdl_node`

The command to control the robot in velocity is 

`$ ros2 run ros2_kdl_package ros2_kdl_node --ros-args -p cmd_interface:=velocity`

The command to run the effort controllers is 

`$ ros2 run ros2_kdl_package ros2_kdl_node --ros-args -p cmd_interface:=effort`

# Choosing the control action
After runnig the node to start the controller you have to choose between the 4 given trajectory 
`press a number between 1 and 4 `
After you have to select the control action pressing choosing between 2 option PD+ or Operational space control 
`press 1 or 2`
