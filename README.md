# RGBD_ORB_SLAM2_RT
Real-time envrionment reconstruction based on ORB_SLAM2 with XTION (RGBD sensor) <br>
 
### Introduction
This is a modified version based on [ORB_SLAM2](https://github.com/raulmur/ORB_SLAM2) and [ORBSLAM2_with_pointcloud_map](https://github.com/gaoxiang12/ORBSLAM2_with_pointcloud_map) , thanks for Raul's and Gao's great work! This works with XTION whicn privide us the rgb image and depth image and reconstruct the around environment by the trajectory of sensors. You can visualize the environment by point cloud map during the SLAM process. <br>

### How to install
Unzip the file you will find two directories. First compile the modified g2o: <br>
```c
  cd g2o_with_orbslam2
  mkdir build
  cd build
  cmake ..
  make 
```
If you have some problems, follow the instructions from the [original g2o library](https://github.com/RainerKuemmerle/g2o) <br>

Then compile the ORB_SLAM2. You need firstly to compile the DBoW2 in ORB_SLAM2_modified/Thirdpary, and then the [Pangolin module](https://github.com/stevenlovegrove/Pangolin). Finally, build ORB_SLAM2:
```c
  cd ORB_SLAM2_modified
  mkdir build
  cd build
  cmake ..
  make
```

### Run examples
Then you can run the examples. In the *Examples/RGB-D*, *rgbd_tum* deals with the datasets of TUM (*desk.jpg room.jpg*), *rgbd_cc* deals with the datasets of your own, *rgbd_xtion_cc* runs with XTION and reconstruct the environment in real-time (*demo1-4.png*). To run *rgbd_xtion_cc*, you can try under ORB_SLAM2_modified/: <br>
```c
  ./Examples/RGB-D/rgbd_xtion_cc Vocabulary/ORBvoc.txt ./Examples/RGB-D/xtion.yaml
```
You can get the intrinsic parameters of your xtion by ROS/OPENCV/MATLAB *calibration*. <br>
 
### Notes
1. If you use *kinectv1*, just change the driver for kinect and this project could work. <br>
2. If you use *kinectv2*, maybe you need to change the driver and code to get data from sensors. <br>
3. If you have some problems about g2o when compiling the orb_slam2, it must be the problem that orb_slam2 finds a wrong version of g2o. Change the *CMakeLists.txt* and *add absolute path* for g2o which is the g2o_with_orbslam2 you just compiled.
