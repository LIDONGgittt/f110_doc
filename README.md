F1TENTH docs
---
Thanks to mLAB UPenn for providing comprehensive documentation on F1TENTH.  
Most contents are from and linking to [F1TENTH TEAM](https://f1tenth.org/about.html) or 
[F1TENTH github community](https://github.com/f1tenth).  
Video resources from mLAB UPenn on [Youtube](https://www.youtube.com/user/RealTimemLAB).

Because of hardware shortage, this repo is used for recording some adjustments and personal modifications. 

Basic settings
--------
Hardwares:
- Computing board: [Nvidia Xavier NX Developer Kit](https://developer.nvidia.com/embedded/jetson-xavier-nx-devkit)
- Sensers:
  - Lidar: [Hokuyo UST-10LX](https://hokuyo-usa.com/products/lidar-obstacle-detection/ust-10lx)
  - Camera: [Intel RealSense D345i](https://www.intelrealsense.com/depth-camera-d435i/)
- Racecar: [Traxxas Slash 4X4 Ultimate](https://traxxas.com/products/models/electric/slash-4x4-ultimate)
- Joystick: [DualShock 4 (PS4)](https://www.playstation.com/en-us/accessories/dualshock-4-wireless-controller/) Bluetooth controller

Softwares:
---
- ROS2 foxy + Ubuntu 20.04
  - [JetPack 5.0](https://developer.nvidia.com/jetpack-sdk-50dp) is released and updated to Ubuntu 20.04.
  - [ROS2](https://docs.ros.org/en/foxy/index.html)
- ROS melodic + Ubuntu 18.04
  - [JetPack 4.6.1](https://developer.nvidia.com/embedded/jetpack)
  - [Docker](https://docs.docker.com/)

Install system
--------
- Follow [JetPack 5.0](https://developer.nvidia.com/jetpack-sdk-50dp) or [JetPack 4.6.1](https://developer.nvidia.com/jetpack-sdk-461)
to flush a pre-compiled system into the SD card.

- Follow [link for ROS2](https://f1tenth.readthedocs.io/en/foxy_test/getting_started/firmware/index.html) to build the car
and setup basic system.  
This is the [link](https://f1tenth.org/build.html) for ROS1 and Ubuntu Melodic version.  
To avoid using _sudo_ before every docker command, add user to the docker group:  
```>$ sudo usermod -aG docker ${USER}```  
Re-login to activate the changes.  
[Nvidia docker container toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#docker)

- Install VNC server [vino-server](https://developer.nvidia.com/embedded/learn/tutorials/vnc-setup),
or use remote desktop software [NoMachine](https://f1tenth.readthedocs.io/en/foxy_test/getting_started/software_setup/software_combine.html#using-a-remote-desktop)
to connect desktop remotely. 

- Setup Lidar: [link](https://github.com/f1tenth/f1tenth_doc/blob/stable/getting_started/firmware/firmware_hokuyo10.rst)

- Setup VESC: [link](https://f1tenth.readthedocs.io/en/foxy_test/getting_started/firmware/drive_workspace.html#udev-rules-setup)

- Setup RealSense: [link](https://github.com/IntelRealSense/realsense-ros)  
  1. First is to install librealsense SDK. There is no official repo supporting Ubuntu 20.04 Focal. It is suggested to
  build librealsense from source. [tutorial](https://robots.uc3m.es/installation-guides/install-realsense2.html#install-realsense2-from-sources-ubuntu-1404-trusty-and-2004-bionic)
- RealSense Mount: 
  [Here](/SensorMount) is a personalized sensor mount to support both Lidar [Hokuyo UST-10LX](https://hokuyo-usa.com/products/lidar-obstacle-detection/ust-10lx)
  and [Intel RealSense D345i](https://www.intelrealsense.com/depth-camera-d435i/) on the car. This model can fit well to the
  [Platform Deck V3](https://drive.google.com/drive/u/1/folders/1m6JuSgbCYWefAvTAbb9SPebGBG61cLQo). 

- Install driver for DualShock 4 (PS4) Bluetooth controller: [link1](http://wiki.ros.org/ds4_driver), [link2](http://willshw.me/2018/12/24/connect-ps4-joystick.html),
[github](https://github.com/naoki-mizuno/ds4_driver)  
Connect to DS4: It is suggested to connect using a remote desktop.   
Here is another way to connect without desktop, ***be aware that this may cause unexpected and serious communication delay*** :
  1. Press *SHARE* and *PS* buttons simultaneously to enter pair mode
  2. Open a new shell window and run `>$ duso ds4drv` to connect automatically 

Drive the car manually
---
[Manual Control](https://f1tenth.readthedocs.io/en/foxy_test/getting_started/driving/drive_manual.html)


Applications
---
SLAM: [link](https://github.com/NVIDIA-ISAAC-ROS/isaac_ros_visual_slam)  
Only run successfully with Jetpack 4.6.1 + Docker(ROS2). Refer to [ros1_jetpack4.6.1](https://github.com/LIDONGgittt/f110_doc/tree/ros1_jetpack4.6.1) branch

Tips
---
- If some nodes keep running for a long time (more than 2 hours), `ros2 node list` / `ros2 topic list` might return
  empty or not-complete info, try to restart the ros2 daemon.   
  `>$ ros2 daemon stop`  
  `>$ ros2 daemon start`  
  Or check [this](https://fast-dds.docs.eprosima.com/en/latest/fastdds/ros2/discovery_server/ros2_discovery_server.html#ros-2-introspection).
- Python version control via ANACONDA for arm64 [link](https://docs.anaconda.com/anaconda/install/graviton2/)
- Use `--symlink-install` to saves you from having to rebuild every time you tweak python scripts
- For configs, create a symbolic link in the install/package_name/share folder to apply changes without need to rebuild the package 