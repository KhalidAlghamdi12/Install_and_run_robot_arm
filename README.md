# Install_and_run_robot_arm
how to install and run robot arm (ROS NOETIC)

this is for ROS noetic ONLY .. if you want to install on other types of ROS please visit https://github.com/smart-methods/arduino_robot_arm


First thing you need to do a folder and source folder named (for example) catkain_ws and also src file to work on
$ mkdir catkin_ws
$ cd catkin_ws
$ mkdir src

then type the following command to start the work space 

$ catkin_make

$cd ~/catkin_ws/src

$sudo apt install git

$git clone https://github.com/smart-methods/arduino_robot_arm

2-Add the Dependencies

$cd ~/catkin_ws

$ rosdep install --from-paths src --ignore-src -r -y

Make sure to use the commands based on your ROS version .. as i said this is for noetic virsion

$ sudo apt-get install ros-noetic-moveit

$ sudo apt-get install ros-noetic-joint-state-publisher ros-noetic-joint-state-publisher-gui

$ sudo apt-get install ros-noetic-gazebo-ros-control joint-state-publisher

$ sudo apt-get install ros-noetic-ros-controllers ros-noetic-ros-control

3- Install Arduino IDE https://www.arduino.cc/en/software 

after install run ($ sudo ./install.sh) after unzipping the folder or from the folder press open in terminal 

$ roslaunch robot_arm_pkg check_motors.launch

to connect it with the hardware

$ rosrun rosserial_python serial_node.py _port:=/dev/ttyUSB0 _baud:=115200

To run the arm using gazebo

$ roslaunch robot_arm_pkg check_motors.launch

$ roslaunch robot_arm_pkg check_motors_gazebo.launch

$ rosrun robot_arm_pkg joint_states_to_gazebo.py

If you have a permission problem try use this commands

$ sudo chmod +x ~/catkin_ws/src/arduino_robot_arm/robot_arm_pkg/scripts/joint_states_to_gazebo.py

To control the arm by Moveit and Kinematics

$ roslaunch moveit_pkg demo.launch

$ rosrun rosserial_python serial_node.py _port:=/dev/ttyUSB0 _baud:=115200

To run the arm using gazebo

$ roslaunch moveit_pkg demo_gazebo.launch

if you encounter any problems make sure you are working on the correct file it goes tricky sometimes Also make sure you have the source on bashrc. (ctrl+h on files to show hiddens .. it's there)

done .. thanks for reading
