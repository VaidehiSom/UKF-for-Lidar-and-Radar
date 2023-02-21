# UKF for Lidar and Radar

Sensor Fusion by combing lidar's high resolution imaging with radar's ability to measure velocity of objects we can get a better understanding of the sorrounding environment than we could using one of the sensors alone.

<img src="media/ukf_highway_tracked.gif" width="700" height="400" />

I have implemented Unscented Kalman Filter to estimate the state of multiple cars on a highway using noisy lidar and radar measurements. RMSE values are lower that the tolerance.

<img src="media/ukf_highway.png" width="700" height="400" />

`main.cpp` is using `highway.h` to create a straight 3 lane highway environment with 3 traffic cars and the main ego car at the center. 
The viewer scene is centered around the ego car and the coordinate system is relative to the ego car as well. The ego car is green while the other traffic cars are blue. The traffic cars will be accelerating and altering their steering to change lanes. Each of the traffic car's has it's own UKF object generated for it, and will update each indidual one during every time step. 

The red spheres above cars represent the (x,y) lidar detection and the purple lines show the radar measurements with the velocity magnitude along the detected angle. The Z axis is not taken into account for tracking, so you are only tracking along the X/Y axis.

---

## Other Important Dependencies
* cmake >= 3.5
* make >= 4.1
* gcc/g++ >= 5.4
 * PCL 1.2

## Basic Build Instructions

```
mkdir build && cd build
cmake .. && make
./ukf_highway
```