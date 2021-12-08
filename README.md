youbot_simulation
=================

Packages to run the KUKA youBot in the Gazebo simulation with ROS

# Fork description
This fork introduces is focused on the use of the Youbot in Gazebo under ROS Noetic.
## Installation instructions
- `cd <your catkin_ws>/src`
- `git clone git@github.com:Tstienstra/youbot_description.git -b noetic-devel`
- `git clone git@github.com:Tstienstra/youbot_simulation.git`
- `sudo apt-get install ros-noetic-ros-control ros-noetic-ros-controllers ros-noetic-gazebo-ros-control`
- `sudo apt install ros-noetic-pr2-msgs`
- `cd ..`
- `catkin_make`

You should now be able to launch: `roslaunch youbot_gazebo_robot youbot.launch` and control the youbot. Example message to control the arm:
```
rostopic pub /arm_1/arm_controller/command trajectory_msgs/JointTrajectory "header:
  seq: 0
  stamp:
    secs: 0
    nsecs: 0
  frame_id: ''
joint_names: [arm_joint_1, arm_joint_2, arm_joint_3, arm_joint_4, arm_joint_5]
points:
- positions: [0.0, 1.0, 0.0, 0.0, 0.0]
  velocities: [0.0, 0.0, 0.0, 0.0, 0.0]
  accelerations: [0.0, 0.0, 0.0, 0.0, 0.0]
  effort: []
  time_from_start: {secs: 1, nsecs: 0}"
```
Example message to move the base:
```
rostopic pub /cmd_vel geometry_msgs/Twist "linear:
  x: 0.4
  y: 0.0
  z: 0.0
angular:
  x: 0.0
  y: 0.0
  z: 0.0"
```