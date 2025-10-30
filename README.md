# 🤖 Autonomous Patrol Robot for Smart Parking Enforcement Using ROS2 & SLAM

![ROS2](https://img.shields.io/badge/ROS2-Humble-blue?logo=ros)
![Gazebo](https://img.shields.io/badge/Simulator-Gazebo-yellow?logo=gazebo)
![Python](https://img.shields.io/badge/Python-3.8+-blue?logo=python)


> **Autonomous Parking Enforcement Robot**  
> _A ROS2-based mobile robot system that autonomously patrols parking lots, detects wrongly parked vehicles using sensor fusion and computer vision, and reports violations in real time._

---

## 🚦 Problem Statement

Urban parking management is a persistent challenge, with illegal or improper parking leading to congestion, safety hazards, and inefficient use of space. Manual enforcement is labor-intensive and error-prone.

**This project addresses the need for autonomous, scalable, and real-time parking enforcement using robotics, sensor fusion, and AI.**

---
## 🔧 Subsystems

## 🧠 1️⃣ Perception
- **Lidar**: Provides 360° spatial awareness for mapping and obstacle detection.  
- **Camera**: Captures RGB frames for vehicle and sign detection.  
- **Sensor Fusion**: Integrates Lidar point clouds and camera data for precise localization.  

## 🚗 2. Navigation & Mapping

- **SLAM Toolbox**: Real-time mapping and localization using slam_toolbox (CeresSolver backend).
- **Path Planning**: Implemented with ROS2 Navigation Stack for patrol route execution.
- **Simulation**: Urban parking lot world simulated in Gazebo (main.world, parking.world).

## 🚨 3. Violation Detection

- **Rule-based Logic**: Detects improperly parked vehicles (e.g., blocking driveways, no-parking zones).
- **Event Handling**: Triggers reporting once patrol goals are achieved.

## 📡 4. Reporting

- **ROS2 Node**: Publishes violation events and logs details.
- **Notification System**: Sends alerts to owners or authorities (simulated).
---

## 🧰 Experimental Setup

| 🧩 **Component** | **Description** |
|------------------|-----------------|
| 🧱 **Simulation Environment** | Gazebo with custom parking lot worlds |
| 🤖 **Robot Model** | Differential drive robot *(URDF/XACRO-based)* |
| 🎯 **Sensors** | Lidar + RGB Camera |
| 🗺️ **Mapping** | SLAM Toolbox *(outdoor-tuned parameters)* |
| 🧩 **RViz Visualization** | Real-time 3D mapping and patrol path rendering |

---

<p align="center">
  <em>Figure: Real-time 3D mapping and patrol path rendering in RViz during autonomous parking violation detection.</em>
</p>


<p align="center">
  <img src="parking_images/image (23).png" alt="RViz Visualization" width="80%" style="border-radius: 10px; box-shadow: 0px 0px 10px rgba(0,0,0,0.2);" />
</p>

---

### 🎥 Simulation Video  
If available, view **`Simulation.mp4`** for a full patrol demonstration.

---

### 🧩 Key Code Snippet – Violation Event Subscriber

```python
from rclpy.node import Node
from lifecycle_msgs.msg import TransitionEvent

class GoalStatusSubscriber(Node):
    def __init__(self):
        super().__init__('goal_status_subscriber')
        self.subscription = self.create_subscription(
            TransitionEvent,
            '/bt_navigator/transition_event',
            self.goal_status_callback,
            10
        )

    def goal_status_callback(self, msg):
        if msg.label == "Goal succeeded":
            self.get_logger().info("Wrongly parked vehicles; Reporting to the owner")

```
## ⚙️ How to Run

Follow the steps below to set up, build, and run the autonomous patrol simulation.  

---

### 🪄 Install Dependencies

```bash
sudo apt install ros-<distro>-gazebo-ros-pkgs ros-<distro>-slam-toolbox
```

### 🏗️ Build the Workspace

```bash
colcon build
source install/setup.bash
```
### 🚀 Launch Simulation

```bash
ros2 launch my_rosject launch_sim.launch.py
```
### 🛰️ Visualize in RViz

```bash
rviz2 -d config/final_map.rviz
```
### 📡 Monitor Violation Events
``` bash
ros2 run my_rosject GoalStatusSubscriber.py
```
📘 *For further details, see the codebase and the simulation video for a complete patrol demonstration.*
