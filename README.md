# Overview

This project is a reinforcement learning environment for a quadruped. It uses python, ROS (robot operating system), Tensorflow and Gazebo simulation. The robot interacts with Gazebo simulation using ROS. It is trained to walk forward in Gazebo simulation. Deep Deterministic Policy Gradient(DDPG) is used for the robot.

# Files

#### quadruped folder

This folder contains files for reinforment learning environment.

- config/quadruped_control.yaml : joint controller config for Gazebo
- launch/quadruped_control.launch : Spawn quadruped model with controller in Gazebo
- launch/quadruped_gazebo.launch : Spawn quadruped model only in Gazebo
- src/model/ : tensorflow model files of learned agent
- src/agent_mem.p : agent Replay buffer memory
- src/eps_rewards.npy : agent episode rewards
- src/ddpg.py : Deep Deterministic Policy Gradient agent written in tensorflow
- src/quadruped_env.py : quadruped environment for gazebo simulation
- src/quadruped_learn.py : learn a ddpg agent
- src/quadruped_gazebo_act.py : learned agent takes actions in Gazebo
- src/plot_eps_rewards.py : plot episode rewards from eps_rewards.npy
- urdf/quadruped_model.dae : collada file for quadruped urdf
- worlds/quadruped.world : Gazebo world file
- CMakeLists.txt : ROS CMakeLists file
- package.xml : ROS package file

# Prerequisites

- python
- ROS
- Tensorflow
- Gazebo simulation

### additional installations for simulation

- ROS control

```
sudo apt-get install ros-kinetic-ros-control
sudo apt-get install ros-kinetic-ros-controllers
sudo apt-get install ros-kinetic-gazebo-ros-control
```

#### Learning an agent

```
roslaunch quadruped quadruped_control.launch
python quadruped_learn.py
```

#### simulate learned agent

```
roslaunch quadruped quadruped_control.launch
python quadruped_gazebo_act.py
```

- on computer running tensorflow

```
python quadruped_act.py
```

# Tips

#### always

```
source ~/catkin_ws/devel/setup.bash
```

#### ROS core

roscore

#### collada to URDF file

```
rosrun collada_urdf collada_to_urdf quadruped_model.dae > model1.urdf
```
