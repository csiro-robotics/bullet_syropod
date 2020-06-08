# Bullet Syropod

[![Syropod Banner](https://i.imgur.com/QyMTwG3.jpg "CSIRO Robotics")](https://research.csiro.au/robotics/)

This repository contains the configuration, model and launch files specific to the Bullet robot.

This is an operation setup readme for the Bullet Syropod platform - please do not modify.
These instructions are top-level, please consult readme of each individual package for further help.

[![Bullet Syropod](https://i.imgur.com/cHAZ10Y.gif "Bullet Syropod")](https://research.csiro.au/robotics/our-work/research-areas/legged-robots/)

## Getting Started

If you haven't looked at the tutorials for using Syropod Highlevel Controller, see [SHC Tutorials](https://github.com/csiro-robotics/shc_tutorials).

### Requirements

* Ubuntu 18.04 LTS
* ROS Melodic

### Dependencies

#### Base

* [Syropod High-level Controller](https://github.com/csiro-robotics/syropod_highlevel_controller):
  * `git clone https://github.com/csiro-robotics/syropod_highlevel_controller.git`
* [Syropod Remote](https://github.com/csiro-robotics/syropod_remote):
  * `git clone https://github.com/csiro-robotics/syropod_remote.git`

#### Control Input

* [ROS Joystick](http://wiki.ros.org/joy)
  * `sudo apt-get install ros-melodic-joy`
* [RQT Reconfigure Control](https://github.com/csiro-robotics/syropod_rqt_reconfigure_control) (Optional):
  * `git clone https://github.com/csiro-robotics/syropod_rqt_reconfigure_control.git`

Instructions on the use of differing control inputs can be found at the individual repo links above.

### Installation

```bash
mkdir -p openshc_ws/src
cd openshc_ws/src
git clone https://github.com/csiro-robotics/bullet_syropod.git
cd ..
catkin build
```

## Operation

### High-Level Control

To run the Bullet high-level control run the following launch file with optional arguments

`roslaunch bullet_syropod bullet_highlevel.launch`

Below are the default values for optional high-level arguments

* Bullet Configuration: `config:=bullet_insectoid` (loads bullet_insectoid.yaml for SHC)
* Gait Parameters: `gait:=gait` (loads gait.yaml for SHC)
* Auto-Pose Parameters: `auto_pose:=auto_pose` (loads auto_pose.yaml for SHC)
* Control input method: `control:=joy` ('rqt' to use rqt_reconfigure_control)
* RVIZ Visualisation: `rviz:=true`
* Gazebo Simulation: `gazebo:=false`
* RQT Plot: `plot:=false`
* RQT Reconfigure: `reconfigure:=false`
* Auto-Logging: `logging:=false`

Example: To run Bullet Insectoid configuration in Gazebo but without rviz visualisation with parameter reconfiguration panel and rqt_plot run the following:

`roslaunch bullet_syropod bullet_highlevel.launch config:=bullet_insectoid rviz:=false gazebo:=true reconfigure:=true plot:=true`

Tuning of configuration parameters is done using the corresponding config yaml files.
Consult [`syropod_highlevel_controller/config/readme.md`](https://github.com/csiro-robotics/syropod_highlevel_controller/tree/master/config) for details.

### Typical Usage

RVIZ Visualisation of Mammalian Config:

`roslaunch bullet_syropod bullet_highlevel.launch config:=bullet_mammalian rviz:=true`

Gazebo Simulation of Insectoid Config:

`roslaunch bullet_syropod bullet_highlevel.launch config:=bullet_insectoid gazebo:=true`

## Tuning & Experimentation

Before tuning please make a copy of the desired parameter file (eg: bullet_insectoid) and make changes there.

In order to use the new parameter file launch 'bullet_highlevel' with the specific argument set to the new parameter file.

eg: `roslaunch bullet_syropod bullet_highlevel config:=bullet_insectoid`

Tuning of high-level parameters is done using the following parameter files.

* Syropod Parameters - arg=config:
  * `/config/bullet_*.yaml`
* Gait Cycle Parameters - arg=gait:
  * `/config/gait.yaml`
* Auto Posing Cycle Parameters - arg=auto_pose:
  * `/config/auto_pose.yaml`

Consult [`syropod_highlevel_controller/config/readme.md`](https://github.com/csiro-robotics/syropod_highlevel_controller/tree/master/config) for details.

## Authors

* Samith Ashan
* Benjamin Tam

## License

This project is licensed under the CSIRO Open Source Software Licence Agreement (variation of the BSD / MIT License) - see the [LICENSE](LICENSE) file for details.

## Issues

Please report bugs using [Issue Tracker](https://github.com/csiro-robotics/bullet_syropod/issues) or contact us via email [shc-support@csiro.au](mailto:shc-support@csiro.au).
