# deltaStartup
Intro:
This is a description document of a Ros simulation package created for the project “P3 project autonomous toilet cleaner”.
The document will explain the gazebo,  robot description, Slam_gmapping, navigation, iraLaserTools, and moveit integration packages.
A demo video can be found at: https://youtu.be/FsXPII8OoOU
Gitrepo: 
Gazebo environment:
The environment consists of two main spaces. The first one simulates a main area (living room , office ..), the second is a main space that has access to a toilet space. The environment was created to  simulate a scenario where the robot can perform  mapping and navigation tasks.

Robot description:
Models:
The package consists of two main 3D models. A design provided by the manufacturer, a holonomic platform where the arm is mounted, and 3D models of RGB, depth, and lidar sensors.

Ros Plugins:
The description package includes multiple ROS/Gazebo plugins:
Libgazebo_ros_planar_move : for holonomic movement simulation.
Libgazebo_ros_control,
libgazebo_joint_control,
libgazebo_joint_state_publisher,
Libgazebo_joint_trajectory_server: for publishing and controlling the arm joints state using moveit.
Ros transmissions : to simulate joints control.
Libgazebo_ros_laser: to simulate lidar sensors.
Libgazebo_ros_openni_kinect: to simulate rgb and depth cams.


Control files:
A .yaml file that includes configurations used further by movit to control the arm.
World file:
Includes the design of the environment.
Launch files:
Gazebo.launch: not to run, included in robot.launch
Arm.launch: not to run , included in robot.launch
Robot.launch : starts the robot and arm simulation in gazebo.
Slam_gmapping.launch : start the nodes required for gmapping.
Launch commands: 
$ roslaunch toiletcleaner robot.launch
$ roslaunch toiletcleaner slam_gmapping.launch

Tcnav:
The package include teb.launcn file to start the ROS nodes required to perform navigation using Teb local planner and dwa global planner.
Launch command:
$ roslaunch tcnav teb.launch

IRA_laser_tools:
Used to merge the data from both lidars and publish results on /Scan topic.
The nodes are started at the launch of toiletcleaner/robot.launch
TcMoveit:
The package contains moveit configuration files and a launch file to start required nodes in order to simulate moveit integration with the robot.
Launch command:
$ roslaunch tcmoveit tc.launch
