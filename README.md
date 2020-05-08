# Bullet Syropod

This is a operation setup readme for the Bullet Syropod platform - please do not modify.

These instructions are top-level, please consult readme of each individual package for further help.

## Requirements

* Ubuntu 18.04 LTS
* ROS Melodic

## Dependencies

### Base

* [Syropod Package](https://bitbucket.csiro.au/projects/HEX/repos/bullet_syropod):
  * `git clone https://bitbucket.csiro.au/scm/hex/bullet_syropod.git`
* [Syropod High-level Controller](https://bitbucket.csiro.au/projects/HEX/repos/syropod_highlevel_controller):
  * `git clone https://bitbucket.csiro.au/scm/hex/syropod_highlevel_controller.git`
* [Syropod Remote](https://bitbucket.csiro.au/projects/HEX/repos/syropod_remote):
  * `git clone https://bitbucket.csiro.au/scm/hex/syropod_remote.git`

### Control Input

* [Joypad Control](https://bitbucket.csiro.au/projects/HEX/repos/syropod_remote):
  * `sudo apt-get install ros-kinetic-joy`
* [RQT Reconfigure Control](https://bitbucket.csiro.au/projects/HEX/repos/syropod_keyboard_control) (Optional):
  * `git clone https://bitbucket.csiro.au/scm/hex/syropod_keyboard_control.git`

Instructions on the use of differing control inputs can be found at the individual repo links above.

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
Consult [`syropod_highlevel_controller/config/readme.md`](https://bitbucket.csiro.au/projects/HEX/repos/syropod_highlevel_controller/browse/config) for details.

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

Consult [`syropod_highlevel_controller/config/readme.md`](https://bitbucket.csiro.au/projects/HEX/repos/syropod_highlevel_controller/browse/config) for details.
