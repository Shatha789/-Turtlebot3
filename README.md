# Turtlebot3
Use Turtlebot3 with SLAM approach to create and save a map
firstly, install Ubuntu on PC and open the terminal and install  ROS 1 on Remote PC using this commands : 

$ sudo apt update

$ sudo apt upgrade

$ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_melodic.sh

$ chmod 755 ./install_ros_melodic.sh 

$ bash ./install_ros_melodic.sh

Then Install Dependent ROS 1 Packages using this command : 

$ sudo apt-get install ros-melodic-joy ros-melodic-teleop-twist-joy \
  ros-melodic-teleop-twist-keyboard ros-melodic-laser-proc \
  ros-melodic-rgbd-launch ros-melodic-depthimage-to-laserscan \
  ros-melodic-rosserial-arduino ros-melodic-rosserial-python \
  ros-melodic-rosserial-server ros-melodic-rosserial-client \
  ros-melodic-rosserial-msgs ros-melodic-amcl ros-melodic-map-server \
  ros-melodic-move-base ros-melodic-urdf ros-melodic-xacro \
  ros-melodic-compressed-image-transport ros-melodic-rqt* \
  ros-melodic-gmapping ros-melodic-navigation ros-melodic-interactive-markers
  
  # Install TurtleBot3 Packages
Then Install TurtleBot3 via Debian Packages by using this commands : 

$ sudo apt-get install ros-melodic-dynamixel-sdk

$ sudo apt-get install ros-melodic-turtlebot3-msgs

$ sudo apt-get install ros-melodic-turtlebot3 

![image](https://user-images.githubusercontent.com/86571348/124517914-daa27680-dded-11eb-8848-fa063841fe88.png)


# Set TurtleBot3 Model Name 
Using this commands : 

$ echo "export TURTLEBOT3_MODEL=burger" >> ~/.bashrc

$ echo "export TURTLEBOT3_MODEL=waffle_pi" >> ~/.bashrc

![image](https://user-images.githubusercontent.com/86571348/124517460-b003ee00-ddec-11eb-8ace-4f795013c1c8.png)

To Connect PC to a WiFi device and find the assigned IP address with the command below you have to use this command : 

$ ifconfig

Then to Source the bashrc with below command use this command : 

$ source ~/.bashrc

# Gazebo Simulation
You have to Install Simulation Packages by using this commands : 

$ cd ~/catkin_ws/src/

$ git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git

$ cd ~/catkin_ws

$ catkin_make

![image](https://user-images.githubusercontent.com/86571348/124518036-22c19900-ddee-11eb-9d5b-ffb8edebf014.png)

# Launch Simulation World

1. Empty World 

Using this commands:

$ export TURTLEBOT3_MODEL=burger

$ roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch

![image](https://user-images.githubusercontent.com/86571348/124518465-1d188300-ddef-11eb-87c5-6cff03559334.png)

2. TurtleBot3 World

Using this commands:

$ export TURTLEBOT3_MODEL=waffle

$ roslaunch turtlebot3_gazebo turtlebot3_world.launch

![image](https://user-images.githubusercontent.com/86571348/124518513-433e2300-ddef-11eb-8a32-0a1695c7507f.png)

3. TurtleBot3 House

Using this commands:

$ export TURTLEBOT3_MODEL=waffle_pi

$ roslaunch turtlebot3_gazebo turtlebot3_house.launch

![image](https://user-images.githubusercontent.com/86571348/124518632-97490780-ddef-11eb-95e6-863baa1bc14a.png)

Then use this command ($ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch) to operate TurtleBot3

# SLAM Simulation
When SLAM in Gazebo simulator, you can select or create various environments and robot models in virtual world

# Launch Simulation World 

$ export TURTLEBOT3_MODEL=burger

$ roslaunch turtlebot3_gazebo turtlebot3_world.launch

# Run SLAM Node

$ export TURTLEBOT3_MODEL=burger

$ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping

# Run Teleoperation Node 

$ export TURTLEBOT3_MODEL=burger

$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch

![image](https://user-images.githubusercontent.com/86571348/124519167-2f93bc00-ddf1-11eb-8c84-1b948247c1e5.png)

![image](https://user-images.githubusercontent.com/86571348/124519255-6bc71c80-ddf1-11eb-94c9-12c250b30ca9.png)

Then move the robot by using (a,s,w,d,x) to complete all the map

# Save Map 

![image](https://user-images.githubusercontent.com/86571348/124519361-bba5e380-ddf1-11eb-8647-9282fc96db6d.png)

Then use this command ($ rosrun map_server map_saver -f ~/map )
