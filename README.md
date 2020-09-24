# TIERS Drone Racing 

Gazebo simulator with Hector quadrotor for training for the TIERS drone racing. 

The races are later done with a Tello drone controlled via ROS, as part of the master course *Perception and NAvigation in Robotics*.

## Get Started

Clone the repo into your **catkin_ws**:

```
mkdir -p  ~/drone_racing_ws/src && cd ~/drone_racing_ws/src
git clone https://github.com/TIERS/drone_racing.git
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
roslaunch
```

Start the motors
```
rosservice call /enable_motors "enable: true"
```

In order to control the UAV with keyboard teleop, first remap the topic
```
roslaunch tiers_drone_racing hector_dronerace.launch
```

and then run the teleop node (install it with `sudo apt install ros-melodic-teleop-twist-keyboard` if you don't have it yet):
```
rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```
