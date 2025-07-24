# Robot_Simulation
Robot Simulation Model
## 基于LeRobot的仿真配置过程：  
### 1.环境搭建
#### 1.1安装Python和依赖库  
确保已安装Python（推荐3.10版本），并安装必要的库：  
```bash
sudo apt-get update  
sudo apt-get install python3.10  
pip install torch transformers gym
```
#### 1.2 克隆LeRobot仓库并安装依赖
```bash
git clone https://github.com/huggingface/lerobot  
cd lerobot  
pip install .  
sudo apt-get install cmake build-essential
```
#### 1.3 创建并激活Conda虚拟环境
```bash
conda create -y -n lerobot python=3.10  
conda activate lerobot
```
### 2. 配置仿真环境
#### 2.1 安装ROS和Gazebo 
LeRobot支持ROS与Gazebo仿真环境，安装命令如下：  
```bash
sudo apt install ros-noetic-desktop-full  
sudo apt install ros-noetic-gazebo-ros
```
会出现问题：  
```bash
(lerobot) dwei@Dwei:~/lerobot$ sudo apt install ros-noetic-desktop-full  
sudo apt install ros-noetic-gazebo-ros
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package ros-noetic-desktop-full
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package ros-noetic-gazebo-ros
```
是因为 ROS Noetic 的软件源未被正确添加到你的系统中  
需要添加 ROS Noetic 的软件源。可以通过以下步骤完成：  
##### (1)添加ROS Noetic软件源
```bash
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```
##### (2)添加ROS Noetic的密钥
```bash
sudo apt install curl
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
```
##### (3)更新软件包列表
```bash
sudo apt update
```








```bash
# 直接使用系统已安装的ur_description
source /opt/ros/jazzy/setup.bash
ros2 launch ur_description view_ur.launch.py ur_type:=ur5
```
