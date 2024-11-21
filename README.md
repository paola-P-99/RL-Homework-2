# RL-Homework-2
#  Overview
The goal of the homework  is to dynamically control a 7 DoF robot manipulator using Docker and ROS2 with RVITZ and Gazebo to ensure it follows a desired trajectory both in the joint space and the operational space. The repo contains the step to download the folders from github,launch the robot and run the controller. 
# Set-up  
Open the terminal,open the container and enter into the directory where you want to downlad the folder then clone the repository with:

`$ git clone  ... `

To build the packages, enter into the ROS2 workspace and build them with:

`$ colcon build`

After this source the workspace 

`$  source install/setup.bash`

# Launching the robot 
The robot can be controlled with 3 command interfaces
    • Position 
    • Velocity 
    • Effort 
If you want to applay a position  controller  you must launch the file with the position  interface,which is the default one, to do this you have to run the following command:

`$ ros2 launch  iiwa_bringup iiwa.launch.py `

If you want to applay a velocity controller you must launch the file with the velocity interface,to do this you have to run the following command:

`$ ros2 launch  iiwa_bringup iiwa.launch.py  command_interface:="velocity" robot_controller:="velocity_controller"`

If you want to applay an effort controller you must launch the file with the effort interface,to do this you have to run the following command: 

`$ ros2 launch  iiwa_bringup iiwa.launch.py command_interface:="effort" robot_controller:=“effort_controller" `

By default the launch file run the  RVITZ2 and ROS2 simulations to appreciate the kinematics of the robot, to be able to spawn the robot in the Gazebo environment and apreciate the dynamics of the model you have to modify the launch command adding   

` $ use_sim:=true`

to ensure that the value of the Gazebo simulation is set to true. 

# Running the controllers 
to run the node with the controller open another terminal connnect to the same docker and run the command provided below.
To ensure the proper visualization of the control action the  controllers activated must be the same as the interface selected, otherwise you wont be able to see the robot moving
If you have selected a position interface you have to run the following command:

` $ ros2 run ros2_kdl_package ros2_kdl_node`

If you have selected a velocity interface you have to run the following command:

`$ ros2 run ros2_kdl_package ros2_kdl_node --ros-args -p cmd_interface:=velocity`

If you have selected a effort interface you have to run the following command:

`$ ros2 run ros2_kdl_package ros2_kdl_node --ros-args -p cmd_interface:=effort`

# Choosing the control action
In the code is provided the possibility to choose between  circular or rectilinear trajectory provided withb both trapezioidal or polynomial velocity.To do this you have to   
`press a number between 1 and 4 then enter  `
The controller provided are two one in the joint space implemented as a PD+ and one in the operational space implemented as an Inverse Dynamics control to select between the 2 you hae to 
`press 1 or 2 then enter`

# Note
The simulation in the Gazebo environment start paused and you have to be fast to un-pause in order to ensure the correct activation of the controllers. A good way to do this is to launch the node containig the controller and select the trajectory you desire then run the launch file and un-pause the simulation then select the desired control to activate the controller in the terminal where you are runnig them. 

