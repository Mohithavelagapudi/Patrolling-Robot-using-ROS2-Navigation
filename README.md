# 🤖 Patrol-Robot: Intelligent Parking Lot Patrolling with ROS2 & SLAM

![ROS2](https://img.shields.io/badge/ROS2-Humble-blue?logo=ros)
![Gazebo](https://img.shields.io/badge/Simulator-Gazebo-yellow?logo=gazebo)
![Python](https://img.shields.io/badge/Python-3.8+-blue?logo=python)
![License](https://img.shields.io/badge/license-MIT-green)


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

SLAM Toolbox: Real-time mapping and localization using slam_toolbox (CeresSolver backend).

Path Planning: Implemented with ROS2 Navigation Stack for patrol route execution.

Simulation: Urban parking lot world simulated in Gazebo (main.world, parking.world).

🚨 3. Violation Detection

Rule-based Logic: Detects improperly parked vehicles (e.g., blocking driveways, no-parking zones).

Event Handling: Triggers reporting once patrol goals are achieved.

Machine Learning Extension (optional): Future versions may use CNNs for visual violation classification.

📡 4. Reporting

ROS2 Node: Publishes violation events and logs details.

Notification System: Sends alerts to owners or authorities (simulated).

Database Logging: Optional extension for violation storage and analytics.
