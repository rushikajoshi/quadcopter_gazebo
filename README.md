# quadcopter_gazebo
Package for simulation of a quadcopter in gazebo
## Installation
Install ROS Control packages
```
sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654 
sudo apt-get update
sudo apt-get install ros-noetic-gazebo-ros-pkgs ros-noetic-gazebo-ros-control ros-noetic-ros-control ros-noetic-ros-controllers
sudo apt-get install ros-noetic-joint-state-controller ros-noetic-effort-controllers ros-noetic-position-controllers
```

Create a package in catkin_ws/src directory with rospy and std_msgs dependencies
```
cd ~/catkin_ws/src
catkin_create_pkg quadcopter rospy std_msgs
```
clone this repo inside the package
```
cd ~/catkin_ws/src/quadcopter
git clone https://github.com/Ayush1285/quadcopter_gazebo.git
```
You have to replace all existing files/folders with this repo's files/folders.

Now compile/build the package
```
cd ~/catkin_ws
catkin_make
```
Launching quadcopter in gazebo
```
roslaunch quadcopter quad_gazebo.launch
```

**Publishing velocity to propeller joints:**
* Topic - /quad/joint_motor_controller/command
* msg -  std_msgs/Float64MultiArray
```
rostopic pub -1 /quad/joint_motor_controller/command std_msgs/Float64MultiArray "data: [100, -100, 100, -100]"
```
Provides 100 unit of speed to all propeller joints

Note: Camera, Depth Camera, 2D LiDar, IMU sensors have been added to Quadcopter.

