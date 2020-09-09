3D Systems Geomagic Touch-X ROS Driver for Windows
============

ROS Packages for 3D Systems Geomagic Touch-X haptic device, **USB** version.

This repository has been forked from the original repository by Bharat Mathur, [https://github.com/bharatm11/Geomagic_Touch_ROS_Drivers](https://github.com/bharatm11/Geomagic_Touch_ROS_Drivers) for the Touch-X haptic device in ubuntu. I have made a few changes to adapt it for touch-X model for working in windows 10. 
###Tested with
Touch-X, OpenHaptics3.5, MS Windows 64bit 10.0.18362, ROS-Melodic, Visual studio 2019, Windows SDK 10.0.18362.0
###Additional Dependencies
Pthreads
## Installation

1. Install ROS-melodic, Chocolatey, Git and Visual Studio on Windows
Follow the instructions from:
http://wiki.ros.org/Installation/Windows

2. Setup Catkin workspace using VC comand prompt
```
cd \
mkdir catkin_ws & cd catkin_ws & mkdir src
catkin_make
```

3. Download and Install OpenHaptics 3.5 and Haptic Device drivers
Download drivers using instructions at: 
https://support.3dsystems.com/s/article/OpenHaptics-for-Windows-Developer-Edition-v35?language=en_US

4. Install Dependencies: 
Clone and make the Pthread repo following the instructions from 
https://github.com/jwinarske/pthreads4w
There are several seeting in which you can make Pthreads, I hva used VCE
```
nmake realclean VCE
```

5. Device setup
Run Touch Smart Setup to setup and calibrate the device. Its a good idea to perform calibration everytime beore device is used.


8. Launch ROS Node

Clone and build this repository.
```
cd <ROS_workspace> & catkin_make
cd <ROS_workspace>/devel
source setup.bash
roslaunch omni_common omni_state.launch 
```

Data from the haptic device can be read from the following topics:
  /phantom/button
  /phantom/force_feedback
  /phantom/joint_states
  /phantom/pose
  /phantom/state 

## Directory structre assumed:
C:\
+---opt
+---pthreads
+---catkin_ws
+---OpenHaptics
