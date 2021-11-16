#  Reinforcement Learning Experiments on an Inverted Pendulum Simulation

This meta package contains ROS packages listed in the `.rosinstall` file to run a simulation and train an agent to control the inverted pendulum. Meant to be a sandbox for experimenting with reinforcement learning algorithms and techniques.

![training_gif](images/trained_model.gif)

☝️ Training after ~600 episodes

## Prerequisites

 - [torch](https://pytorch.org/get-started/locally/) (cpu version is fine)
 - ROS Noetic recommended for Python3 support.

## Setup

```shell
$ mkdir ~/catkin_ws
$ cd ~/catkin_ws
$ git clone https://github.com/dean4ta/rl_experiments src
$ cd ~/catkin_ws/src
$ wstool update
$ cd ~/catkin_ws
$ rosdep install --from-paths src --ignore-src -r -y
$ catkin_make
```

## Quick Start

Terminal 1
```shell
$ source devel/setup.bash
$ roslaunch rrbot_gazebo rrbot_world.launch rviz:=true
```

Terminal 2
```shell
$ source devel/setup.bash
$ rosrun inverted_pendulum_rl_control train_ddpg.py
```

## Saving and Loading Model

Once training has produced a model, you can save it to a file at any time with the following command:

    rosservice call /save_model "filename: 'model_name'"

This command saves the model to the `inverted_pendulum_rl_control/models/` folder.

You can load and evaluate a model with the following command:

    roslaunch inverted_pendulum_rl_control eval.launch

This repo contains an existing model that can be evaluated like so:

    roslaunch inverted_pendulum_rl_control eval.launch rl_model_name:=trained_actor.pkl

## ROS Packages
see [`.rosinstall`](.rosinstall) for packages included in this meta package.