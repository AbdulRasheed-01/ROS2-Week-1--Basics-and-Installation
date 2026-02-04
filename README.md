# Week 1: ROS 2 Fundamentals - Your Journey Begins!
This Repository contain basics of ROS2.
📚 Course Overview
This course is designed to teach you ROS2 Humble from scratch, starting with fundamentals and progressing to advanced robotics applications.
🎯 Learning Objectives
By the end of this week, you will be able to:

✅ Understand what ROS 2 is and why we use it

✅ Install ROS 2 Humble on Ubuntu 22.04

✅ Run your first ROS 2 commands

✅ Understand basic ROS 2 concepts (Nodes, Topics, Messages)

✅ Create and run a simple publisher-subscriber system

📚 Theory Content
1.1 What is ROS 2?
ROS (Robot Operating System) is not an actual operating system but a middleware framework that provides:

Communication tools for robots

Hardware abstraction

Package management

Development tools

Why ROS 2 Humble?

Latest LTS (Long Term Support) version

Improved performance and security

Better documentation and community support

Core Components:

Nodes - Individual programs/processes

Topics - Named buses for message passing

Messages - Data structures passed between nodes

Services - Request/response communication

Actions - Long-running tasks with feedback


⚙️ Installation Guide
Step 1: System Setup

# Update system
sudo apt update && sudo apt upgrade -y

# Set locale
sudo apt install locales

sudo locale-gen en_US en_US.UTF-8

sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8

export LANG=en_US.UTF-8

Step 2: Add ROS 2 Repository

# Ensure Ubuntu Universe repository is enabled

sudo apt install software-properties-common

sudo add-apt-repository universe

# Add ROS 2 GPG key
sudo apt update && sudo apt install curl -y

sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

# Add repository to sources list
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(source /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null




