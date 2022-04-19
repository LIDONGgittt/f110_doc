# Initialize

Basic settings
--------
Hardwares:
- Computing board: [Nvidia Xavier NX Developer Kit](https://developer.nvidia.com/embedded/jetson-xavier-nx-devkit)
- Sensers:
  - Lidar: [Hokuyo UST-10LX](https://hokuyo-usa.com/products/lidar-obstacle-detection/ust-10lx)
  - Camera: [Intel RealSense D345i](https://www.intelrealsense.com/depth-camera-d435i/)
- Racecar: [Traxxas Slash 4X4 Ultimate](https://traxxas.com/products/models/electric/slash-4x4-ultimate)

Softwares:
- [JetPack 4.6.1](https://developer.nvidia.com/embedded/jetpack)
- [ROS2](https://docs.ros.org/en/foxy/index.html)
- [Docker](https://docs.docker.com/)

Install system
--------
Follow https://developer.nvidia.com/jetpack-sdk-461 to flush a pre-compiled system into the SD card.

Follow [link for ROS2](https://f1tenth.readthedocs.io/en/foxy_test/getting_started/firmware/index.html) to build the car and setup basic system.  
This is the [link](https://f1tenth.org/build.html) for ROS1 and Ubuntu Melodic version.  
To avoid using _sudo_ before every docker command, add user to the docker group:  
```sudo usermod -aG docker ${USER}```  
Re-login to activate the changes.  
[Nvidia docker container toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#docker)

Install VNC server: [link](https://github.com/f1tenth/f1tenth_doc/blob/stable/getting_started/software_setup/software_advance.rst)

Setup Lidar: [link](https://github.com/f1tenth/f1tenth_doc/blob/stable/getting_started/firmware/firmware_hokuyo10.rst)

Setup RealSense: [link](https://github.com/IntelRealSense/realsense-ros)

Applications
--------
SLAM: [link](https://github.com/NVIDIA-ISAAC-ROS/isaac_ros_visual_slam)
