Welcome to the Use-Turtlebot3-with-SLAMTurtlebot3-with-SLAM-approach-to-create-and-save-a-map wiki!
# To use Turtlebot3 with SLAM approach to create and save a map
*  Follow the steps
## Install the required dependency packages to turtlebot3  build 
### install-dependent-ros-1-packages
>  $ sudo apt-get install ros-melodic-joy ros-melodic-teleop-twist-joy 
>   ros-melodic-teleop-twist-keyboard ros-melodic-laser-proc \
>   ros-melodic-rgbd-launch ros-melodic-depthimage-to-laserscan \
>   ros-melodic-rosserial-arduino ros-melodic-rosserial-python \
>   ros-melodic-rosserial-server ros-melodic-rosserial-client \
>   ros-melodic-rosserial-msgs ros-melodic-amcl ros-melodic-map-server \
>   ros-melodic-move-base ros-melodic-urdf ros-melodic-xacro \
>   ros-melodic-compressed-image-transport ros-melodic-rqt* \
>   ros-melodic-gmapping ros-melodic-navigation ros-melodic-interactive-markers
### Install TurtleBot3 Packages
* $ sudo apt install ros-melodic-hls-lfcd-lds-driver  
* $ sudo apt-get install ros-melodic-dynamixel-sdk
* $ sudo apt-get install ros-melodic-turtlebot3-msgs
* $ sudo apt-get install ros-melodic-turtlebot3
### create  source folder under the  catkin workspace
* $ mkdir -p ~/catkin_ws/src
* $ cd ~/catkin_ws/src/
### download turtleBot3 pakages from GitHub
* $ git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3.git
* $ git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git

*$ cd ~/catkin_ws && catkin_make
  
### Run burger model in GAZEBO simulator as gazebomap.png
* $ export TURTLEBOT3_MODEL=burger
* $ roslaunch turtlebot3_gazebo turtlebot3_world.launch
### To move the model with keyboard as map_keyboard.png using this command:
* $export TURTLEBOT3_MODEL=burger
* roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
 ## To create  using slam and save map as map.pgm file 
1. open GAZEBO as previous step 
1.  Create a map using SLAM
* $roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping **Simulation RVIZ will work as initial map.png**
1.  Run the turtlebot3 using keyboard as map_keyboard.png by  Opening  a new terminal and run the teleoperation node 
* $export TURTLEBOT3_MODEL=burger
*$roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
*  **Finally**  save the  map  by create **a new terminal** and write this command :
$rosrun map_server map_saver -f ~/map

