# 🛠️ Jetson Orin Nano Robot Setup (ODrive + CAN + ROS 2 + RTAB-Map)

This repository contains launch files and configurations for a four-wheel differential drive robot using ODrive over CAN, running on a Jetson Orin Nano. It includes teleoperation, camera integration, SLAM, and autonomous navigation using ROS 2.

---

## 🔧 Step 1: Start CAN Communication

Enable CAN interface on Jetson Orin Nano:

```bash
sudo ip link set can0 up type can bitrate 250000

    ✅ Ensure that can0 is properly connected and visible using ifconfig can0.

🤖 Step 2: Launch ODrive Control

Start the ODrive motor controller nodes:

# ros2 launch odrive_botwheel_explorer botwheel_explorer.launch.py

Once all status indicators are green, you can control the robot using keyboard teleoperation:

# ros2 run teleop_twist_keyboard teleop_twist_keyboard

📷 Step 3: Launch Camera Node

Launch your camera without any URDF model:

# ros2 launch odrive_botwheel_explorer camera_as_a_part_of_robot.launch.py

🗺️ Step 4: Launch SLAM (RTAB-Map)
Option A: SLAM with full robot system

# ros2 launch odrive_botwheel_explorer test.launch.py

Option B: RTAB-Map only

# ros2 launch odrive_botwheel_explorer rtabmap.launch.py

🧭 Step 5: Launch Autonomous Navigation (Nav2)

To start the Nav2 stack with a custom parameter file:

# ros2 launch nav2_bringup navigation_launch.py params:=/home/ubuntu/odrive_ws/src/odrive_botwheel_explorer/config/nav2_params.yaml

    🗺️ Make sure the map server, localization, and controller plugins are properly configured in your nav2_params.yaml.

✅ Tips

    Ensure all ODrive boards are detected via CAN and show green indicators.

    To see all active topics:

ros2 topic list

    To visualize the robot and navigation in RViz:

rviz2

    To record data:

ros2 bag record -a

📁 Example Folder Structure

odrive_botwheel_explorer/
├── launch/
│   ├── botwheel_explorer.launch.py
│   ├── camera_as_a_part_of_robot.launch.py
│   ├── test.launch.py
│   └── rtabmap.launch.py
├── config/
│   └── nav2_params.yaml
├── urdf/
├── nodes/
└── README.md

👨‍🔧 Maintainers

Developed and maintained by [Your Name / Team / Lab]
