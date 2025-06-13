# 🛠️ Jetson Orin Nano Robot Setup (ODrive + CAN + ROS 2 + RTAB-Map)

This repository contains launch files and configurations for a four-wheel differential drive robot using ODrive over CAN, running on a Jetson Orin Nano.

---

## 🔧 Step 1: Start CAN Communication

Enable CAN interface on Jetson Orin Nano:

```bash
sudo ip link set can0 up type can bitrate 250000

🤖 Step 2: Launch ODrive Control

Start the motor drivers (ODrive) and bring up the robot controller:

# ros2 launch odrive_botwheel_explorer botwheel_explorer.launch.py

Once everything is up and indicators are green, you can control the robot using keyboard teleoperation:

# ros2 run teleop_twist_keyboard teleop_twist_keyboard

📷 Step 3: Launch Camera Node

Launch camera independently (no URDF required):

# ros2 launch odrive_botwheel_explorer camera_as_a_part_of_robot.launch.py

🧭 Step 4: Launch SLAM (RTAB-Map)

Option 1: Launch SLAM with additional robot setup in rtabmap:

# ros2 launch odrive_botwheel_explorer test.launch.py

Option 2: Launch RTAB-Map only:

# ros2 launch odrive_botwheel_explorer rtabmap.launch.py

✅ Tips

    Ensure all ODrive boards are detected via CAN and show green indicators.

    Check topics using:

ros2 topic list

    Visualize the robot and map using:

rviz2

