# Autonomous_Vision
Autonomous Driving Pipeline
Overview
This repository contains an end-to-end pipeline for autonomous driving, implemented in Python using the CARLA simulator. The pipeline integrates sensor data acquisition (camera and LiDAR), perception (object detection and obstacle identification), path planning (global and local), and vehicle control (PID-based steering and throttle). It is designed to navigate a vehicle safely through a simulated urban environment, avoiding obstacles and following a predefined route.
Problem Statement
The goal is to develop a modular autonomous driving system that:

Processes camera and LiDAR data to detect objects and obstacles.
Plans a collision-free path adhering to traffic rules.
Executes precise vehicle control for smooth navigation.
Operates in real-time within a 100ms cycle.

For a detailed problem statement, see problem_statement.md.
Features

Sensor Suite: Captures and processes RGB camera images and LiDAR point clouds using CARLA's sensor APIs.
Perception: Uses YOLOv5 for object detection and DBSCAN clustering for LiDAR-based obstacle detection.
Path Planning: Generates global routes using CARLA's map and local paths to avoid obstacles.
Control: Implements a PID controller for steering and throttle to follow the planned path.
Real-Time Operation: Runs at 10 Hz (100ms per cycle) for responsive performance.

Prerequisites

CARLA Simulator: Version 0.9.x (tested with 0.9.13).
Python: Version 3.8 or higher.
Hardware: GPU (e.g., NVIDIA RTX 3080) recommended for YOLOv5 inference; CPU fallback supported.
Dependencies:pip install numpy opencv-python open3d torch yolov5 carla


Operating System: Tested on Ubuntu 20.04 and Windows 10.

Installation

Install CARLA:
Download and install CARLA from carla.org.
Follow CARLA's setup instructions to configure the simulator.


Clone Repository:git clone https://github.com/your-repo/autonomous-driving-pipeline.git
cd autonomous-driving-pipeline


Install Dependencies:pip install -r requirements.txt

Ensure requirements.txt includes:numpy==1.23.5
opencv-python==4.7.0
open3d==0.16.0
torch==1.13.1
yolov5==7.0.0
carla==0.9.13


Download YOLOv5 Weights:
Download yolov5s.pt from the YOLOv5 repository and place it in the project root.



Usage

Start CARLA Simulator:
./CarlaUE4.sh  # Linux
# or
CarlaUE4.exe  # Windows


Run the Pipeline:
python autonomous_driving_pipeline.py

The script connects to the CARLA server (default: localhost:2000), spawns a vehicle, and starts autonomous navigation to a predefined destination (x=100, y=100, z=0).

Configuration:

Modify Config class in autonomous_driving_pipeline.py to adjust parameters like sensor tick rate, speed limit, or LiDAR range.
Update destination coordinates in the initialize method for custom routes.



Project Structure

autonomous_driving_pipeline.py: Main pipeline implementation.
problem_statement.md: Detailed problem description and objectives.
README.md: This file.
requirements.txt: Python dependencies.

Limitations

Simulation-Only: Designed for CARLA; real-world deployment requires additional safety and hardware integration.
Simplified Control: Uses basic PID; advanced controllers (e.g., MPC) could improve performance.
Obstacle Handling: Local planner avoids obstacles but may not handle complex dynamic scenarios (e.g., moving pedestrians).
Dependency on YOLOv5: Object detection performance depends on the pretrained model’s generalization.

Future Improvements

Integrate advanced localization (e.g., GPS/IMU fusion).
Enhance local planner with dynamic obstacle prediction (e.g., Kalman filters).
Optimize for real-world hardware with ROS integration.
Add support for traffic signals and lane changes.

Contributing
Contributions are welcome! Please:

Fork the repository.
Create a feature branch (git checkout -b feature/your-feature).
Commit changes (git commit -m "Add your feature").
Push to the branch (git push origin feature/your-feature).
Open a pull request.

License
This project is licensed under the MIT License. See LICENSE for details.
Contact
For questions or feedback, contact your-email@example.com.