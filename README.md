# Particle Filter for Localization
This project utilizes a 2D particle filter to localize a lost car on a map. The vehicle has access to the initial position estimate provided by a GPS (simulated from a simulator) sensor and LIDAR sensor to measure distances from 
landmarks on the map. The system uses the Bicycle motion model to approximate the motion dynamics of the vehicle and propagate particles through the map.

## Overview of Implementation
- 100 particles are initialized around the initial estimate provided by GPS.
- Using the initial estimate all the particles are propagated through the map using the motion model. The equations of the model are given by:

<p align="center">
<img width="1200" height="400" src="https://github.com/Badri-R-S/2D_Particle_filter_for_Localization/blob/main/Results/motion_formulae.png"
</p> 

- Now that the particles are propagated, they need to be assigned weights depending on, how close their observations are, with respect to actual observations. This can be achieved using multivariate gaussian distribution formulae:

<p align="center">
<img width="800" height="200" src="https://github.com/Badri-R-S/2D_Particle_filter_for_Localization/blob/main/Results/multivariate_gaussian_density.png"
</p> 

- Finally, the particles are resampled with replacement, with a probability proportional to their weights for the next iteration.

### Point to note:
After the prediction step, before finding weights, the observations and particle positions are different coordinate systems. The particle positions are in the map coordinate system and the obervations are in the vehicle coordinate
system. Hence a homogenous transformation has to be performed to convert the observations to map coordinate system:

<p align="center">
<img width="800" height="400" src="https://github.com/Badri-R-S/2D_Particle_filter_for_Localization/blob/main/Results/homogenous_transformation.png"
</p> 

## Steps to run the code
- The simulator can be downloaded from this link : [Simulator](https://github.com/udacity/self-driving-car-sim/releases/)
- The dependencies can be installed by simply running the **install-ubuntu.sh** file that has been provided in the repository.
- Clean the workspace by running the script **clean.sh**
- Build the workspace by running the script **build.sh**
- To finally run the code, run **run.sh**, after opening the simulator.

## Results
The blue circle depicts the estimated position of the vehicle provided by the particle filter. The green line depicts the distances to multiple landmarks.

<p align="center">
<img width="800" height="400" src="https://github.com/Badri-R-S/2D_Particle_filter_for_Localization/blob/main/Results/pf.png"
</p> 

The full video can be viewed at : [Result](https://drive.google.com/file/d/1RD8tdLTu4puxlo64wrby93LxXeOSZZqM/view?usp=sharing)
