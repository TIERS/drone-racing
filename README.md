# TIERS Drone Racing 

Gazebo simulator with Hector quadrotor to train for the TIERS drone racing challenge. 

The races are later done with a Tello drone controlled via ROS, as part of the master course *Perception and Navigation in Robotics*.

## Get Started

This instructions are for Ubuntu 18.04 with ROS Melodic already installed.

Install dependencies

```
sudo apt install ros-melodic-geographic-msgs ros-melodic-hector-gazebo-plugins
```

and download Gazebo models database (we actually only use a few of them, this will download the full database with approx. 400MB of basic models):

```
mkdir -p ~/.gazebo
git clone https://github.com/osrf/gazebo_models ~/.gazebo/models
```

Read more about the Gazebo database [here](http://gazebosim.org/tutorials?tut=model_structure&cat=build_robot).

With all dependencies downloaded, now clone this repo into your **catkin_ws** (the code below creates a new catkin workspace named `drone_racing_ws` in your home folder):

```
mkdir -p  ~/drone_racing_ws/src && cd ~/drone_racing_ws/src
git clone --recursive https://github.com/TIERS/drone_racing.git
```

We recommend using `catkin build`. Install it if needed with

```
sudo apt install python-catkin-tools
```

and then run

```
cd ~/drone_racing_ws
catkin init
catkin build
```

Build the uav messages with
```
catkin build hector_uav_msgs
```

## Run the simulator

Run the simulator with

```
roslaunch tiers_drone_racing hector_dronerace.launch
```

Start the motors
```
rosservice call /enable_motors "enable: true"
```

In order to control the UAV with keyboard teleop, run the teleop node (install it with `sudo apt install ros-melodic-teleop-twist-keyboard` if you don't have it yet):
```
rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```

## Contact

For any questions, write to `jopequ@utu.fi`.

Visit us in [https://tiers.utu.fi](https://tiers.utu.fi)
