# ROS installation and configuration on ubuntu 18.04


<p align="center"><img src="https://user-images.githubusercontent.com/85819577/127329673-cd329a99-e434-40ce-90a4-e8e92322ff6d.png" width="120" height="55" /></p>

What is **ROS**? The Robot Operating System (ROS) is a set of software libraries and tools that help you build robot applications. 
It connects all the devices by one operating system which can control them once and reduce layers of control, the benefit is that the synchronization will be more faster and the control will be more better.


The main steps involved in setting up ROS are as follows:
1. Downloading VMware (Enables users to set up virtual machines on a single physical device)
2. Downloading Ubuntu 18.04 desktop image
3. Creating the virtual machine
4. Installing ROS melodic on Ubuntu
5. Preparing ROS
6. Installing the package arduino_robot_arm



____________________________________________________________________


# 1. Downloading VMware

I've download vmware instead of virtual box, you can download it from this link:

https://www.vmware.com/products/workstation-player/workstation-player-evaluation.html

# 2. Downloading Ubuntu 18.04 desktop image

from the link bellow, choose the desktop image:

https://releases.ubuntu.com/18.04/

# 3. Creating the virtual machine

After running VMware, now you have to create a new virtual machine with Ubuntu system, you can follow the steps shown in this video:

https://www.youtube.com/watch?v=lIhRkea8LpA


# 4. Installing ROS melodic on ubuntu

Open the terminal to write the installation commands for ROS

1. Setup your sources.list:
```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```

2. Set up your keys:
```
sudo apt install curl
```
```
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
```

3. install the ROS:
You have to update your Debian package index first, so type:
```
sudo apt update
```
install the Desktop-Full copy:
```
sudo apt install ros-melodic-desktop-full
```

4. setup the environment:
```
echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc
```
```
source ~/.bashrc
```

5.  install tools and other dependencies for building ROS packages:
```
sudo apt install python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential
```

6.  initialize rosdep before use ROS tools:
install rosdep:
```
sudo apt install python-rosdep
```

initialize rosdep
```
sudo apt install python-rosdep
```

# 5. Preparing ROS

<p align="center"><img src="https://user-images.githubusercontent.com/85819577/127341341-c4748d1f-0071-4bc4-b5d3-1e37911df7c5.jpg" width="500" height="300" /></p>

ROS use a workspace called "catkin", this workspace contains src file, at this file we have to put all the packagaes that we will need.

1. build the catkin workspace:
```
mkdir -p ~/catkin_ws/src
```
```
cd ~/catkin_ws/
```
```
catkin_make
```
```
source devel/setup.bash
```
```
echo $ROS_PACKAGE_PATH
/home/youruser/catkin_ws/src:/opt/ros/kinetic/share
```


# 6. Installing the package arduino_robot_arm

1. go to the src file:
```
cd ~/catkin_ws/src
```

2. install git, then clone the arduino_robot_arm package:
```
sudo apt install git
```
```
git clone https://github.com/smart-methods/arduino_robot_arm.git 
```

3. move to catkin_ws file:
```
cd ~/catkin_ws
```

4. install the dependencies to run the package:
```
rosdep install --from-paths src --ignore-src -r -y
```
```
sudo apt-get install ros-kinetic-moveit
```
```
sudo apt-get install ros-kinetic-joint-state-publisher ros-kinetic-joint-state-publisher-gui
```
```
sudo apt-get install ros-kinetic-gazebo-ros-control joint-state-publisher
```
```
sudo apt-get install ros-kinetic-ros-controllers ros-kinetic-ros-control
```

5. then compile the package:
```
catkin_make
```

6. type this command:
```
sudo nano ~/.bashrc
```

7. go to the end of the window an type this command, then press **ctrl + o**:
```
source /home/Yourdevicename/catkin_ws/devel/setup.bash
```

8. type this command:
```
source ~/.bashrc
```

9. then type:
```
roslaunch robot_arm_pkg check_motors.launch
```

______________________________________________________________________________

# The result
![simulator](https://user-images.githubusercontent.com/85819577/127345840-1512223d-c392-4ac0-a9cf-15bdc6ce82a0.png)

