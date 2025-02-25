# tello_driver [![Build Status](http://build.ros.org/job/Ksrc_uX__tello_driver__ubuntu_xenial__source/badge/icon)](http://build.ros.org/job/Ksrc_uX__tello_driver__ubuntu_xenial__source/)

# 1. Overview
Communicating with the Tello drone can be done either using official [Tello SDK](https://dl-cdn.ryzerobotics.com/downloads/Tello/Tello%20SDK%202.0%20User%20Guide.pdf) or one of the unofficial libraries. The unofficial libraries originated from the reverse-engineering the raw packages broadcasted by the Tello. This ROS package is build on top of the unofficial [TelloPy](https://github.com/hanyazou/TelloPy) library. The [TelloPy](https://github.com/hanyazou/TelloPy) library is used at this moment since it offers more functionalities than the official [Tello SDK](https://dl-cdn.ryzerobotics.com/downloads/Tello/Tello%20SDK%202.0%20User%20Guide.pdf) or any other unofficial library. 

Developing of the tello_driver ROS package is inspired by [tello_driver](https://github.com/anqixu/tello_driver), which by now diverged considerately from the original work. Furthermore, development of this ROS package pursues not to modify the TelloPy library, but instead apply any modification or addition to the ros_driver package in an encapsulated manner. This prevents breaking functionalities when updating the TelloPy library.

## Installation

### camera_info_manager_py
dependencie of tello_driver
https://github.com/ros-perception/camera_info_manager_py

### tello_driver

foi feito baseado no seguinte pacote:

https://github.com/appie-17/tello_driver

```
sudo apt install ros-noetic-codec-image-transport

sudo apt-get install python3-wheel

cd tello_driver/src/tellopy/tellopy

python3 setup.py bdist_wheel

sudo apt-get install python3-pip

pip3 install dist/tellopy-*.dev*.whl --upgrade
```

## Launch

* Turn on Tello drone
* Connect to drone's WiFi access point (```TELLO_XXXXXX)```
* ```$ roslaunch tello_driver tello_node.launch```

# 2. Nodes

## 2.1 tello_driver_node
Main node running as interface for the TelloPy library

### Subscribed topics
* ```/tello/cmd_vel``` [geometry_msgs/Twist](http://docs.ros.org/api/geometry_msgs/html/msg/Twist.html)
* ```/tello/emergency``` [std_msgs/Empty](http://docs.ros.org/api/std_msgs/html/msg/Empty.html)
* ```/tello/fast_mode``` [std_msgs/Empty](http://docs.ros.org/api/std_msgs/html/msg/Empty.html)
* ```/tello/flattrim``` [std_msgs/Empty](http://docs.ros.org/api/std_msgs/html/msg/Empty.html)
* ```/tello/flip``` [std_msgs/Uint8](http://docs.ros.org/api/std_msgs/html/msg/UInt8.html)
* ```/tello/land``` [std_msgs/Empty](http://docs.ros.org/api/std_msgs/html/msg/Empty.html)
* ```/tello/palm_land``` [std_msgs/Empty](http://docs.ros.org/api/std_msgs/html/msg/Empty.html)
* ```/tello/takeoff``` [std_msgs/Empty](http://docs.ros.org/api/std_msgs/html/msg/Empty.html)
* ```/tello/manual_takeoff``` [std_msgs/Empty](http://docs.ros.org/api/std_msgs/html/msg/Empty.html)
* ```/tello/throw_takeoff``` [std_msgs/Empty](http://docs.ros.org/api/std_msgs/html/msg/Empty.html)


### Published topics
* ```/tello/image_raw/camera_info``` [sensor_msgs/CameraInfo](http://docs.ros.org/api/sensor_msgs/html/msg/CameraInfo.html)
* ```/tello/image_raw/h264``` [h264_image_transport/H264Packet](https://github.com/tilk/h264_image_transport/blob/master/msg/H264Packet.msg)
* ```/tello/odom``` [nav_msgs/Odometry](http://docs.ros.org/api/nav_msgs/html/msg/Odometry.html)
* ```/tello/imu``` [sensor_msgs/Imu](http://docs.ros.org/api/sensor_msgs/html/msg/Imu.html)
* ```/tello/status``` [tello_driver/TelloStatus](https://github.com/appie-17/tello_driver/blob/development/msg/TelloStatus.msg)


### Parameters
* ```~/tello_driver_node/connect_timeout_sec```
* ```~/tello_driver_node/fixed_video_rate```
* ```~/tello_driver_node/local_cmd_client_port```
* ```~/tello_driver_node/local_vid_server_port```
* ```~/tello_driver_node/stream_h264_video```
* ```~/tello_driver_node/tello_cmd_server_port```
* ```~/tello_driver_node/tello_ip```
* ```~/tello_driver_node/vel_cmd_scale```
* ```~/tello_driver_node/video_req_sps_hz```
* ```~/tello_driver_node/altitude_limit```
* ```~/tello_driver_node/attitude_limit```
* ```~/tello_driver_node/low_bat_threshold```
