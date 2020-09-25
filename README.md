# TIERS Drone Racing 

Gazebo simulator with Hector quadrotor to train for the TIERS drone racing challenge. 

The races are later done with a Tello drone controlled via ROS, as part of the master course *Perception and Navigation in Robotics*.

## Get Started

This instructions are for Ubuntu 18.04 with ROS Melodic already installed.

Clone this repo into your **catkin_ws** (the code below creates a new catkin workspace named `drone_racing_ws` in your home folder):

```
mkdir -p  ~/drone_racing_ws/src && cd ~/drone_racing_ws/src
git clone --recursive https://github.com/TIERS/drone_racing.git
```

Install dependencies

```
sudo apt install ros-melodic-geographic-msgs ros-melodic-hector-gazebo-plugins
```

We also need some Gazebo models that we use for the virtual race scenario. You have two opcions here, download the full Gazebo models database, or just a few that we provide to be able to run this simulations. Either way, first create a folder where Gazebo can find your models:

```
mkdir -p ~/.gazebo
```

### Option 1: Full Gazebo Database

Download Gazebo models database (we actually only use a few of them, this will download the full database with approx. 400MB of basic models):

```
git clone https://github.com/osrf/gazebo_models ~/.gazebo/models
```

Read more about the Gazebo database [here](http://gazebosim.org/tutorials?tut=model_structure&cat=build_robot).

### Option 2: Minimal amount of models

Copy to the same folder the models included in this repo (change the path if you cloned the repo somewhere else):

```
cp -r ~/drone_racing_ws/src/drone_racing/gazebo_models ~/.gazebo/models
```


## Build the workspace

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

Visit us at [https://tiers.utu.fi](https://tiers.utu.fi)
