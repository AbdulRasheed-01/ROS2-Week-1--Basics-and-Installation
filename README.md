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

Step 3: Install ROS 2 Humble

# Update and install
sudo apt update

sudo apt install ros-humble-desktop

# Source ROS 2 in your shell
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc

source ~/.bashrc

# Install development tools
sudo apt install python3-colcon-common-extensions python3-rosdep2

sudo rosdep init

rosdep update

Step 4: Verify Installation

# Test ROS 2 installation
printenv | grep ROS

# Should show:
ROS_VERSION=2

ROS_PYTHON_VERSION=3

ROS_DISTRO=humble

# Test a simple command
ros2 --help

🔧 Hands-On Practice
Exercise 1: Your First ROS 2 Commands

Open Terminal 1:

# Start ROS 2 demo talker (publisher)
ros2 run demo_nodes_cpp talker

Open Terminal 2:

# Start ROS 2 demo listener (subscriber)
ros2 run demo_nodes_cpp listener

Expected Output:

Terminal 1: Publishing "Hello World" messages

Terminal 2: Receiving and displaying messages

Exercise 2: Explore ROS 2 Graph

# List all active nodes
ros2 node list

# List all topics
ros2 topic list

# Echo messages from a topic
ros2 topic echo /chatter

# Get topic info
ros2 topic info /chatter

# Get message type
ros2 topic type /chatter

Exercise 3: Understanding Topics

# See data being published in real-time
ros2 topic hz /chatter

# See message bandwidth
ros2 topic bw /chatter

# Publish a custom message
ros2 topic pub /chatter std_msgs/msg/String "data: 'Hello from CLI!'"

💻 Code Examples

Example 1: Simple Publisher (Python)

Create simple_publisher.py:

    #!/usr/bin/env python3

    import rclpy

    from rclpy.node import Node

    from std_msgs.msg import String

    class SimplePublisher(Node):

    def __init__(self):
    
        super().__init__('simple_publisher')
        
        self.publisher = self.create_publisher(String, 'greeting', 10)
        
        timer_period = 2.0  # seconds
        
        self.timer = self.create_timer(timer_period, self.timer_callback)
        
        self.counter = 0
    
    def timer_callback(self):
        msg = String()
        msg.data = f'Hello ROS 2! Count: {self.counter}'
        self.publisher.publish(msg)
        self.get_logger().info(f'Publishing: "{msg.data}"')
        self.counter += 1
        

    def main(args=None):

    rclpy.init(args=args)
    
    node = SimplePublisher()
    
    try:
    
        rclpy.spin(node)
        
    except KeyboardInterrupt:
    
        pass
    
    node.destroy_node()
    
    rclpy.shutdown()

    if __name__ == '__main__':

    main()

Example 2: Simple Subscriber (Python)

    #!/usr/bin/env python3

    import rclpy

    from rclpy.node import Node

    from std_msgs.msg import String

    class SimpleSubscriber(Node):

    def __init__(self):
    
        super().__init__('simple_subscriber')
        
        self.subscription = self.create_subscription(
            String,
            'greeting',
            self.listener_callback,
            10)
    
    def listener_callback(self, msg):
    
        self.get_logger().info(f'I heard: "{msg.data}"')

    def main(args=None):
        rclpy.init(args=args)
        node = SimpleSubscriber()
    
    try:
    
        rclpy.spin(node)
        
    except KeyboardInterrupt:
    
        pass
    
    node.destroy_node()
    
    rclpy.shutdown()

    if __name__ == '__main__':

    main()


Running the Examples

# Terminal 1: Run publisher
python3 simple_publisher.py

# Terminal 2: Run subscriber
python3 simple_subscriber.py

# Terminal 3: Logger
python3 temperature_logger.py

# Terminal 4: Monitor topics
ros2 topic list

ros2 topic echo /temperature_data

