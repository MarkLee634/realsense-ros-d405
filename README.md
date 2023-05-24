# ROS Wrapper for Intel&reg; RealSense&trade; Devices
This repo is SPECIFICALLY FOR SUPPORTING D405 camera in ROS1. The official realsense supports only ROS2. 
This was tested only on Ubuntu 20.04 with ROS1 Noetic and Python3.

## Installation Instructions
delete any realsense driver in your workspace -- including apt installs.
```
sudo apt remove ros-noetic-realsense2-camera*
sudo apt purge ros-noetic-realsense2-camera*
```

git clone this fork in your catkin ws
```
git clone --branch development https://github.com/[INSERT LINK TO GIT REPO]
```

build from source
```
catkin_make clean
catkin_make -DPYTHON_EXECUTABLE=/usr/bin/python3 DCATKIN_ENABLE_TESTING=False -DCMAKE_BUILD_TYPE=Release
catkin_make install
```


## Usage Instructions

### Start the camera node
To start the camera node in ROS:

```bash
roslaunch realsense2_camera rs_camera.launch
```

This will stream all camera sensors and publish on the appropriate ROS topics.

Other stream resolutions and frame rates can optionally be provided as parameters to the 'rs_camera.launch' file.

### Published Topics
The published topics differ according to the device and parameters.
After running the above command with D435i attached, the following list of topics will be available (This is a partial list. For full one type `rostopic list`):
- /camera/color/camera_info
- /camera/color/image_raw
- /camera/color/metadata
- /camera/depth/camera_info
- /camera/depth/image_rect_raw
- /camera/depth/metadata
- /camera/extrinsics/depth_to_color
- /camera/extrinsics/depth_to_infra1
- /camera/extrinsics/depth_to_infra2
- /camera/infra1/camera_info
- /camera/infra1/image_rect_raw
- /camera/infra2/camera_info
- /camera/infra2/image_rect_raw
- /camera/gyro/imu_info
- /camera/gyro/metadata
- /camera/gyro/sample
- /camera/accel/imu_info
- /camera/accel/metadata
- /camera/accel/sample
- /diagnostics


