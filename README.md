## CARLA-Based Sensor Fusion for Improved Trajectory Mapping

**Author:** Neil Zarghami, MSEE

---

Introduction: 
- This guide will assist in the integration of camera and LiDAR data for Simultaneous Localization and Mapping (SLAM) in AV using the CARLA simulator.

Objectives:
- Estimate vehicle trajectory using visual odometry from camera data
- Build a 3D mapped point cloud of the environment using LiDAR data
- Combine trajectory and 3D map data to enhance localization and navigation

Tools and Technologies:
- CARLA Simulator for data generation
- Jupyter Notebook 
- OpenCV, Open3D

### Step 1: Installation
Familiarization with CARLA is crucial. We recommend the following linked tutorials provided in the links below. These tutorials aid in the installation of CARLA and offer an introduction to implementing the sensors. 

NOTE: As an alternative to a fresh install, you may run the "Main.ipynb" notebook to launch the CARLA simulated environment. However, this is not recommended. Ensure that all code dependencies are satisfied.   

 - CARLA Tutorial 00 - Getting Started: https://youtu.be/AaJekfFR1KQ?si=OD5RXXNbr7YMdAQw 
 - An in depth look at CARLA's sensors: https://youtu.be/om8klsBj4rc?si=a5Gh-28bpZ5um0cP

<img src="https://github.com/CZGITEE/CARLA-SensorFusion-TrajectoryMapping/raw/main/Docs/images/1.png" width="600">

### Step 2: Export Data
The "Toolset_ExportData.ipynb" notebook is part of this project's toolset to export RGB camera and LiDAR data.
Once the sensors are operating correctly, use the "ExportData" tool to export sensor data for post processing. 

<img src="https://github.com/CZGITEE/CARLA-SensorFusion-TrajectoryMapping/raw/main/Docs/images/2.png" width="600">

### Step 3: Post Processing
The "Toolset_PostProcess.ipynb" notebook is designed to process the RGB camera and LiDAR data. The RGB camera data and LiDAR data are used to create a sequential visual representation of the vehicle over time. Additionally, the RGB camera data is used to identify keypoint matches, which are then applied in visual odometry to estimate the vehicle's trajectory.
 
 <img src="https://github.com/CZGITEE/CARLA-SensorFusion-TrajectoryMapping/raw/main/Docs/images/3.png" width="400">
  -  
 <img src="https://github.com/CZGITEE/CARLA-SensorFusion-TrajectoryMapping/raw/main/Docs/images/4.png" width="600">

*RGB camera and LiDAR represenations of the ego car performing a left turn.*

 <img src="https://github.com/CZGITEE/CARLA-SensorFusion-TrajectoryMapping/raw/main/Docs/images/5.png" width="400">

*Plotted trajectory estimate of ego vehicle driving straight for a duration, making a left turn, and then continuing to drive straight.*

### Step 4: SLAM Fusion
The "Toolset_FusionSLAM.ipynb" notebook is designed to integrate the visual odometry data from the RGB camera with the 3D point cloud data from the LiDAR. This fusion process enhances the accuracy of the vehicle's localization and mapping capabilities. This fusion can be explored further for precise trajectory mapping and improved navigation within the simulated environment. The image below demonstrates the vehicle's trajectory combined with the point cloud map. 

 <img src="https://github.com/CZGITEE/CARLA-SensorFusion-TrajectoryMapping/raw/main/Docs/images/6.png" width="600">
 
*Trajectory infused with point cloud map showcasing the SLAM implementation.*

<img src="https://github.com/CZGITEE/CARLA-SensorFusion-TrajectoryMapping/raw/main/Docs/images/7.png" width="600">

*Fused view  with red arrow highlighting the pedestrian and major surrounding buildings through route.*

### Summary:
 - Generate data using the CARLA simulator
 - Export sensor data to disk
 - Process camera data with OpenCV to detect and match keypoints between frames
 - Use keypoint matches for odometry to estimate the vehicle's trajectory
 - Process LiDAR data with Open3D to create a 3D point cloud of the environment
 - Visualize the 3D point cloud to analyze the spatial layout
 - Integrate the estimated trajectory with the point cloud to perform SLAM
 - Use SLAM to provide a comprehensive view of the vehicle's path and its environment

### Notebook Descriptions:
 - Main.ipynb
   - Main notebook to run CARLA simulation
 - Toolset_ExportData.ipynb
   - Export sensor data
 - Toolset_PostProcess.ipynb
   - Create sequential visual representations and estimate ego vehicle trajectory with the exported sensor data
 - Toolset_FusionSLAM.ipynb
   - Integrate the estimated trajectory with the LiDAR 3D point cloud data to perform SLAM
   
### Additional Notebooks:
 - Extras_ConnectivityCheck.ipynb
   - Notebook to test and verify connectivity  
 - Extras_RemoveAll.ipynb
   - Notebook to remove all cars, actors, and sensors




