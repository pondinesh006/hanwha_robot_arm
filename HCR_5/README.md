# Hanwha HCR-5 Robot

[![license - apache 2.0](https://img.shields.io/:license-Apache%202.0-yellowgreen.svg)](https://opensource.org/licenses/Apache-2.0)
[![License](https://img.shields.io/badge/License-BSD%203--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)

#### _*Pon Dinesh S, 2023*_

## Building

### Prerequisite

Installation of Ros Noetic in Ubuntu 20.04 for refernce use this link.

[ROS NOETIC INSTALLATION](https://wiki.ros.org/noetic/Installation/Ubuntu)

### Catkin tools

It is recommended to use [catkin_tools][] instead of the default [catkin][] when building ROS workspaces. `catkin_tools` provides a number of benefits over regular `catkin_make` and will be used in the instructions below. All packages can be built using `catkin_make` however: use `catkin_make` in place of `catkin build` where appropriate.

### Building Workspace

NOTE: As of now I am using Catkin workspace for cloning my package. You can use any workspace.

he following instructions assume that a [Catkin workspace][] has been created at `$HOME/catkin_ws` and that the *source space* is at `$HOME/catkin_ws/src`. Update paths appropriately if they are different on the build machine.

These instructions build the `noetic-devel` branch on a ROS Noetic system:

```bash
# change to the root of the Catkin workspace
$ cd $HOME/catkin_ws

# retrieve the latest development version of HCR_5.
$ git clone https://github.com/pondinesh006/hanwha_robot_arm.git src/hanwha_robot

# check build dependencies. Note: this may install additional packages,
# depending on the software installed on the machine
$ rosdep update

# be sure to change 'Noetic' to whichever ROS release you are using
$ rosdep install --from-paths src/ --ignore-src --rosdistro noetic

# build the workspace (using catkin_tools)
$ catkin build
```

### Activating the workspace

Finally, activate the workspace to get access to the packages just built:

```bash
$ source $HOME/catkin_ws/devel/setup.bash
```

At this point all packages should be usable (ie: `roslaunch` should be able to auto-complete package names starting with `hcr_5_..`). In case the workspace contains additional packages (ie: not from this repository), those should also still be available.


## Steps for Running Simulation

Open the new terminal, change the directory to your workspace and source the workspace.

NOTE: This file will launch gazebo as well as rviz for running the simulation.

```
roslaunch hcr_moveit hcr_5_gazebo.launch
```

## Steps for Running on Robot

ROS Moveit with HCR-5 robot under development. In future, Controlling will done and applications also to be added.

[catkin]: http://wiki.ros.org/catkin
[catkin_tools]: https://catkin-tools.readthedocs.io/en/latest
[Catkin workspace]: http://wiki.ros.org/catkin/Tutorials/create_a_workspace
