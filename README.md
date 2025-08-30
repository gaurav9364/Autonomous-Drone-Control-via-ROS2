# Autonomous Drone Control via ROS2 and AirSim
# Overview

This project enables autonomous drone navigation in simulation using ROS2 and Microsoft AirSim. Through a publisher–subscriber architecture, it becomes easy to send and update waypoints to a virtual drone in real time—mimicking real-world scenarios and supporting robust testing of autonomous logic without the need for physical hardware.

# Features
Real-time waypoint delivery to an AirSim drone using ROS2 topics and nodes

Seamless interface between ROS2 and AirSim via Python scripts

Modular, extensible system for autonomy experiments in realistic 3D simulation

# System Architecture
AirSim serves as the high-fidelity, Unreal Engine-based drone simulation platform.

ROS2 provides the standardized middleware for inter-process communication.

Custom Python ROS2 Nodes act as publishers (transmitting waypoints) and subscribers (listening to telemetry), enabling dynamic, on-the-fly navigation instructions to the simulated drone.

# Installation

# Prerequisites

Ubuntu Linux

ROS2 Humble (or later)

Python 3.8+

Microsoft AirSim (instructions available on the official AirSim GitHub)

# ROS2 Workspace and Package Setup

1. Create a new ROS2 workspace:

bash
mkdir -p ~/ros2_ws/src
cd ~/ros2_ws

2. Install ROS2 if not already installed:
Follow the official ROS2 installation guide.

3. Initialize the workspace and environment:

bash
source /opt/ros/humble/setup.bash

4. Create the ROS2 package for AirSim bridge:

bash
cd ~/ros2_ws/src
ros2 pkg create --build-type ament_python airsim_ros2_bridge --dependencies rclpy geometry_msgs std_msgs

5. Build the package:

bash
cd ~/ros2_ws
colcon build
source install/setup.bash

6. Implement the node (example):
In airsim_ros2_bridge/drone_control.py, implement ROS2 publishers and subscribers to communicate with the AirSim Python API as described in the [documentation].

# AirSim Configuration
1. Install Microsoft AirSim and its dependencies using instructions from the official AirSim GitHub.

2. Create a Simulation Settings File:

    In your simulation directory, create a settings.json file (mkdir -p AirSimNH && cd AirSimNH && nano settings.json).
    Use simulation settings as described for your use-case.

# Usage
1. Start AirSim in the desired simulation environment.

2. Source the ROS2 workspace:

bash
source ~/ros2_ws/install/setup.bash

Run the custom AirSim-ROS2 bridge node:

Example:

bash
ros2 run airsim_ros2_bridge drone_control
Use ROS2 commands or other nodes to publish waypoints to the topic(s) that control drone movement. The node relays these commands to the virtual drone in AirSim, which updates the flight path in real time.

# Customization
Extend or modify the drone_control.py node to implement new behaviors, integrate additional sensor topics, or test alternative autonomy logic—all without any risk to hardware or need for real-world deployment.

# License
MIT License

# Acknowledgements
ROS2 developers and community

Microsoft AirSim project

