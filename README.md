# ROS2-Week-1
This Repository contain basics of ROS2.
📚 Course Overview
This course is designed to teach you ROS2 Humble from scratch, starting with fundamentals and progressing to advanced robotics applications.
Quick Links

📖 Complete Documentation
🔗 Official ROS2 Repository
💬 ROS Discourse Community


📅 Course Structure
WeekTopicStatusWeek 1ROS2 Basics & Installation✅ CurrentWeek 2Creating ROS2 Packages🔜 Coming SoonWeek 3Nodes: Publishers & Subscribers🔜 Coming SoonWeek 4Services & Actions🔜 Coming SoonWeek 5Launch Files & Parameters🔜 Coming SoonWeek 6-10Advanced Topics & Projects🔜 Coming Soon

🎯 WEEK 1: ROS2 Basics & Installation
Duration: 7 days | Level: Beginner | Prerequisites: Basic Linux knowledge, Ubuntu 22.04 LTS

What is ROS2?
🔍 Definition
ROS2 (Robot Operating System 2) is a flexible framework for writing robot software. It's a collection of tools, libraries, and conventions that simplify creating complex and robust robot behaviors across various robotic platforms.
💡 Think of ROS2 As:

A language robots use to communicate (like English for humans)
A toolkit for building robot applications (like Arduino IDE for microcontrollers)
A middleman between sensors and actuators (translates sensor data → motor commands)

🏗️ ROS2 Architecture
┌─────────────────────────────────────────┐
│          ROS2 Architecture              │
├─────────────────────────────────────────┤
│                                         │
│  ┌──────────────┐    ┌──────────────┐  │
│  │   Sensors    │    │   Actuators  │  │
│  │ (Camera, IMU)│    │(Motors, Pump)│  │
│  └──────┬───────┘    └───────┬──────┘  │
│         │                    │         │
│         ├────────────────────┤         │
│         │   ROS2 Framework   │         │
│         │  (DDS Middleware)  │         │
│         │                    │         │
│  ┌──────┴──────┐  ┌──────────┴──────┐  │
│  │   Nodes     │  │   Topics        │  │
│  │(C++, Python)│  │(Communication)  │  │
│  └─────────────┘  └─────────────────┘  │
│                                         │
│  ┌──────────────────────────────────┐  │
│  │  Tools: RViz2, rqt, ros2 CLI     │  │
│  │         Launch, Bag, Simulation  │  │
│  └──────────────────────────────────┘  │
│                                         │
└─────────────────────────────────────────┘

✨ Why Choose ROS2?
🆚 ROS1 vs ROS2 Comparison
FeatureROS1ROS2WinnerMiddlewareCustom (roscore)DDS (industry standard)✅ ROS2Real-time SupportLimitedFull support✅ ROS2Multi-robotDifficultNative support✅ ROS2Network SecurityWeakBuilt-in encryption✅ ROS2Scalability~50 nodes1000+ nodes✅ ROS2Multi-OSLinux onlyLinux, Windows, macOS✅ ROS2Language SupportC++, PythonC++, Python, Java, C#, Rust✅ ROS2Learning CurveSteepModerate✅ ROS2Production ReadyYesYes✅ Tie
🎯 Top 8 Advantages of ROS2
1️⃣ Decentralized Architecture (DDS)
ROS1:
Sensor → roscore (single point of failure) → Controller

ROS2:
Sensor ←──────────────→ Controller
       (DDS - peer-to-peer)
       ✓ No central server
       ✓ Works offline
       ✓ Self-healing network
2️⃣ Real-Time Guarantees

ROS1: Soft real-time (not suitable for critical systems)
ROS2: Hard real-time (millisecond precision)
Use Case: Autonomous vehicle braking must respond <10ms ⚡

3️⃣ Security Built-in 🔐
ROS1: Anyone on network can control your robot ❌
ROS2: Encryption + authentication ✅
4️⃣ Native Multi-Robot Support
ROS1:
Robot A ─┐
Robot B ─┼─→ Central server (bottleneck)
Robot C ─┘

ROS2:
Robot A ↔ Robot B ↔ Robot C (peer-to-peer)
5️⃣ Language Agnostic

C++, Python, Java, C#, Rust, Go, etc.
Use best language for each component

6️⃣ Multi-Platform Support

Ubuntu, Debian, CentOS, Windows 10/11, macOS
Deploy on any platform

7️⃣ Superior Tooling

RViz2: Next-gen 3D visualization
rqt: Modular GUI tools
ros2 CLI: Powerful command-line interface
rosbag2: Better data recording & playback

8️⃣ Flexible Quality of Service (QoS)
python# Tune for your specific needs:
QoS Settings:
- Reliability: Best-effort vs Reliable
- Durability: Volatile vs Transient-local
- History: Keep-last vs Keep-all
- Deadline: Max time between messages

📦 ROS2 Versions & Timeline
Version Release Schedule
┌─────────────┬────────────┬──────────────┬────────────────┐
│  Version    │  Release   │  LTS         │  Sunset        │
├─────────────┼────────────┼──────────────┼────────────────┤
│ ROS2 Foxy   │ Jun 2020   │ Yes (5 yrs)  │ Jun 2027       │
│ ROS2 Galactic│ May 2021   │ No           │ Dec 2022 ❌    │
│ ROS2 Humble │ May 2022   │ Yes (5 yrs)  │ May 2027 ✅    │
│ ROS2 Iron   │ May 2023   │ No           │ Nov 2024       │
│ ROS2 Jazzy  │ May 2024   │ Yes (5 yrs)  │ May 2029       │
│ ROS2 Rolling│ Ongoing    │ Cutting-edge │ No sunset      │
└─────────────┴────────────┴──────────────┴────────────────┘
🎯 Why Humble for This Course?
✅ LTS (Long Term Support) - Supported until May 2027
✅ Stable & Proven - Industry standard
✅ Best for Job Market - Most demanded in 2024-2025
✅ Well-Documented - Largest community resources
✅ Ubuntu 22.04 LTS Compatible - Both have 5-year support

🖥️ System Requirements
✅ Minimum Requirements
ComponentRequirementOSUbuntu 22.04 LTS (Jammy Jellyfish)CPUDual-core 2GHz+RAM2GB (4GB+ recommended)Disk Space10GB freeNetworkEthernet or WiFi
🚀 Recommended Setup (for Learning)
Operating System:  Ubuntu 22.04 LTS
Processor:         Intel i5/i7 or AMD Ryzen 5+
Memory:            8GB RAM
Storage:           SSD 256GB+
Network:           Stable WiFi or Ethernet
Optional:          USB3 for sensors/cameras
✔️ Verify Your System
bash# Check Ubuntu version
lsb_release -a
# Expected: Release: 22.04

# Check Available RAM
free -h
# Need: At least 2GB

# Check Disk Space
df -h /
# Need: At least 10GB free

# Check CPU Cores
nproc
# Expected: 2 or more

🛠️ Installation Guide (Step-by-Step)
⚡ Quick Install (Copy-Paste)
bash# Step 1: Update System
sudo apt update && sudo apt upgrade -y

# Step 2: Install prerequisites
sudo apt install -y curl gnupg lsb-release ubuntu-keyring

# Step 3: Add ROS2 repository
curl -sSL https://repo.ros2.org/ros.key | sudo tee /usr/share/keyrings/ros-archive-keyring.gpg > /dev/null
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://repo.ros2.org/ubuntu $(source /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

# Step 4: Update package lists
sudo apt update

# Step 5: Install ROS2 Humble (Desktop - RECOMMENDED)
sudo apt install -y ros-humble-desktop

# Step 6: Setup environment
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc

# Step 7: Install build tools
sudo apt install -y python3-colcon-common-extensions python3-rosdep build-essential cmake
sudo rosdep init
rosdep update

# Step 8: Verify installation
ros2 --version
echo $ROS_DISTRO  # Should output: humble
⏱️ Installation Time: 10-20 minutes (depending on internet speed)
📝 Detailed Step-by-Step
Step 1: Update Your System
bashsudo apt update
sudo apt upgrade -y
Step 2: Install Required Tools
bashsudo apt install -y curl gnupg lsb-release ubuntu-keyring
Step 3: Add ROS2 GPG Key
bashcurl -sSL https://repo.ros2.org/ros.key | sudo tee /usr/share/keyrings/ros-archive-keyring.gpg > /dev/null
Step 4: Add ROS2 Repository
bashecho "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://repo.ros2.org/ubuntu $(source /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
Step 5: Update Package Lists
bashsudo apt update
Step 6: Install ROS2 Humble
Option A: Full Desktop (RECOMMENDED FOR LEARNING)
bashsudo apt install -y ros-humble-desktop
Includes: RViz2, demos, tutorials
Option B: Minimal (Console Only)
bashsudo apt install -y ros-humble-ros-core
Lightweight, CLI only
Option C: Developer Edition
bashsudo apt install -y ros-humble-ros-core build-essential
Step 7: Setup Environment Variables
bash# Add to ~/.bashrc to source automatically
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc

# Apply changes immediately
source ~/.bashrc

# Verify ROS_DISTRO is set
echo $ROS_DISTRO  # Should output: humble
Step 8: Install Build Tools
bash# colcon - ROS2 build system
sudo apt install -y python3-colcon-common-extensions

# rosdep - dependency manager
sudo apt install -y python3-rosdep

# Initialize rosdep
sudo rosdep init
rosdep update

# Development tools
sudo apt install -y build-essential cmake python3-pip git

# Python setup tools
pip install --user -U setuptools pip
Step 9: Final Verification
bash# Check ROS2 version
ros2 --version
# Output: ROS 2 Humble Hawksbill (version number)

# Check distro
echo $ROS_DISTRO
# Output: humble

# Test installation
ros2 run demo_nodes_cpp talker
# Should print: Publishing messages...

✅ Verification & First Test
Test 1: Check Installation
bash# Verify ROS2 is installed correctly
ros2 --version

# Check your distro
echo $ROS_DISTRO
# Should output: humble

# Check ROS_DOMAIN_ID (default is fine)
echo $ROS_DOMAIN_ID
Test 2: Run Talker/Listener Demo ⭐ (IMPORTANT!)
This is your first successful ROS2 program!
Terminal 1 - Run Talker (Publisher):
bashros2 run demo_nodes_cpp talker
Expected output:
[INFO] Publishing: "Hello World: 1"
[INFO] Publishing: "Hello World: 2"
[INFO] Publishing: "Hello World: 3"
...
Terminal 2 - Run Listener (Subscriber):
bashros2 run demo_nodes_cpp listener
Expected output:
[INFO] I heard: [Hello World: 1]
[INFO] I heard: [Hello World: 2]
[INFO] I heard: [Hello World: 3]
...
✅ SUCCESS - Both terminals showing matching messages means ROS2 is working!
Test 3: Explore Nodes
Terminal 3 - List Running Nodes:
bashros2 node list
Output:
/talker
/listener
Test 4: Visualize Communication Graph
Terminal 3 - View Communication Graph:
bashros2 run rqt_graph rqt_graph
This opens a GUI showing:
/talker ──→ /chatter (topic) ──→ /listener

📋 Essential ROS2 Commands Reference
🔍 Node Management
bashros2 node list                      # List all running nodes
ros2 node info /node_name           # Get detailed node info
📢 Topic Management
bashros2 topic list                     # List all topics
ros2 topic info /topic_name         # Get topic details
ros2 topic echo /topic_name         # View live messages
ros2 topic hz /topic_name           # Check publish rate (Hz)
ros2 topic bw /topic_name           # Check bandwidth usage
ros2 topic pub /topic_name message  # Publish a message
⚙️ Service Management
bashros2 service list                   # List all services
ros2 service info /service_name     # Get service details
ros2 service call /service ServiceType "args"
🎛️ Parameter Management
bashros2 param list                     # List all parameters
ros2 param get /node_name param_name
ros2 param set /node_name param_name value
🚀 Building & Running
bashros2 launch package launch_file.py  # Run launch file
colcon build                        # Build all packages
colcon build --packages-select pkg  # Build specific package
🔧 Debugging & Tools
bashros2 doctor                         # System health check
rqt_graph                          # Visualize node graph
rviz2                              # 3D visualization tool
rqt                                # Modular GUI toolkit
📁 Recording & Playback
bashros2 bag record -o bagname -a      # Record all topics
ros2 bag record /topic1 /topic2    # Record specific topics
ros2 bag play bagname.db3          # Playback recording
ros2 bag info bagname.db3          # Show recording info

🎯 Week 1 Hands-On Exercises
✏️ Exercise 1: Installation Verification (Day 1)
Objective: Ensure ROS2 is properly installed and working
Tasks:
bash# 1. Check ROS2 version
ros2 --version

# 2. Verify distro
echo $ROS_DISTRO

# 3. List installed packages
apt list --installed | grep ros2

# 4. Run talker and listener (see "Verification" section above)

# 5. Document your system
uname -a > system_info.txt
lsb_release -a >> system_info.txt
free -h >> system_info.txt
df -h >> system_info.txt
Deliverable: system_info.txt file showing successful installation ✅

🔍 Exercise 2: Explore ROS2 Tools (Days 2-3)
Objective: Get familiar with ROS2 command-line tools
Tasks:
bash# 1. In Terminal 1: Run talker
ros2 run demo_nodes_cpp talker

# 2. In Terminal 2: Run listener
ros2 run demo_nodes_cpp listener

# 3. In Terminal 3: Explore tools
# List all nodes
ros2 node list

# List all topics
ros2 topic list

# Get topic details
ros2 topic info /chatter

# Monitor messages in real-time
ros2 topic echo /chatter

# Check publish rate (frequency)
ros2 topic hz /chatter

# 4. Visualize communication
ros2 run rqt_graph rqt_graph

# 5. Check system health
ros2 doctor
Deliverable: Screenshot of rqt_graph showing talker→listener connection 📸

🏗️ Exercise 3: Understand ROS2 Architecture (Days 4-5)
Objective: Learn fundamental ROS2 concepts
Research Questions:

What is DDS (Data Distribution Service)?
How does topic-based communication work?
What are the differences between nodes, topics, and services?
Why is ROS2 decentralized while ROS1 is centralized?

Deliverable: Create week1_notes.md answering above questions

🛠️ Exercise 4: Setup Development Environment (Days 6-7)
Objective: Prepare your machine for ROS2 development
Tasks:
bash# 1. Create ROS2 workspace
mkdir -p ~/ros2_ws/src
cd ~/ros2_ws

# 2. Create environment setup script
cat > ~/setup_ros2.sh << 'EOF'
#!/bin/bash
source /opt/ros/humble/setup.bash
source ~/ros2_ws/install/setup.bash
export ROS_DOMAIN_ID=0
EOF

chmod +x ~/setup_ros2.sh

# 3. Test workspace
source ~/setup_ros2.sh
ros2 pkg list | head

# 4. Install development tools
sudo apt install -y code git

# 5. Configure VS Code (optional)
# Install these extensions:
# - C/C++ (Microsoft)
# - Python (Microsoft)
# - ROS (Microsoft)
Deliverable: Working ROS2 workspace at ~/ros2_ws/ ✅

📝 Exercise 5: Create GitHub Repository (Days 6-7)
Objective: Upload your course progress to GitHub
Steps:
bash# 1. Initialize git repository
cd ~/ros2_humble_course
git init

# 2. Create structure
mkdir -p week1/exercises week1/scripts images

# 3. Create files
touch README.md week1/README.md

# 4. Add your exercise files
# Copy exercise results here

# 5. Create .gitignore
cat > .gitignore << 'EOF'
*.o
*.a
build/
devel/
install/
.DS_Store
*.pyc
__pycache__/
.vscode/
.idea/
EOF

# 6. Commit and push
git add .
git commit -m "Week 1: ROS2 Basics and Installation"
git push -u origin main
Deliverable: Public GitHub repository with Week 1 content 🚀

❌ Troubleshooting
⚠️ Issue 1: "ros2: command not found"
Cause: ROS2 not sourced in terminal
Solution:
bash# Temporary fix
source /opt/ros/humble/setup.bash

# Permanent fix (should already be done)
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc

⚠️ Issue 2: "Cannot locate ROS distro"
Cause: ROS_DISTRO environment variable not set
Solution:
bash# Check current value
echo $ROS_DISTRO

# Re-source setup file
source /opt/ros/humble/setup.bash

# Verify
ros2 --version

⚠️ Issue 3: Talker/Listener not connecting
Cause: Nodes on different DDS domains
Solution:
bash# Ensure same ROS_DOMAIN_ID
export ROS_DOMAIN_ID=0

# Or add to ~/.bashrc
echo "export ROS_DOMAIN_ID=0" >> ~/.bashrc
source ~/.bashrc

⚠️ Issue 4: "DDS: Real data writer for topic not found"
Cause: Network connectivity or firewall issues
Solution:
bash# Test network connectivity
ping localhost

# Check system health
ros2 doctor

# Ensure firewall allows DDS ports (7400-7413)

📚 Additional Resources
📖 Official Documentation

ROS2 Official Docs
ROS2 Humble Tutorials
ROS2 Concepts

🎥 YouTube Channels

Robotics Back-End
The Construct - ROS2 Basics
Josh Newans - ROS2 from Scratch

💬 Community Support

ROS Discourse - Official forum
Stack Overflow - Q&A
GitHub Issues - Bug reports

📚 Additional Learning

ROS2 Design
ROS2 Security
DDS Overview
