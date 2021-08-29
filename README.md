# SPOTTER

A**s**ynchronous and inde**p**endent WiFi and BLE fusi**o**n method based on **p**article fil**ter**

The main repo has been altered to an industrial code named *[ParsinServer](https://github.com/ParsIOT/ParsinServer)*. 

ParsinServer contains various different tools for deploying Indoor Positioning System based on fingerprinting. 
Refer to *[ParsinServer](https://github.com/ParsIOT/ParsinServer)* for more info.

Here for SPOTTER, We just focused on some sides of the main project that are related to Wi-Fi and BLE fusion algorithm.

## Installation
1. Build project
```
go build
```

3. Run Particle Filter 
```
python algorithms/particlefilter/particlefilterserver.py
```

4. Run IPS server
```
./ParsinServer -particlefilterServer 127.0.0.1:50051
```

5. open 127.0.0.1:8003. Default username and password are *admin*
7. There is a sample BLE database named *ble-c-ips-138_0*. Enter its name to open the dashboard.
8. Now you are in the main dashboard. To see fingerprint select *map/show locations* from the main menu. 
9. ParsinServer contains different panels for various purposes. For example, we developed a panel to calculate CDF on the algorithm errors. 

## Main Parts
+ **Particle Filter**: We developed particle filter based on [https://github.com/jerkern/pyParticleEst](https://github.com/jerkern/pyParticleEst). 
The main code is developed by golang, but we used python to implement the Particle filter algorithm. 
You can access particle filter details in **algorithms/particlefilter** directory. 

+ **WKNN Algorithm**: The major part of the algorithm is in the **algorithms/knn.go** file.
 
As we need some tools for developing our algorithm, This code contains other parts. To make it simple we just mention the most important ones as follows:

+ **algorithms/crossValidation.go**: Some functions for n-fold cross-validation and the implementation of the learning phase of ML algorithms.
+ **glb/algoVar.go**: Default algorithm parameters 
+ **algorithms/runner.go**: Main functions for which are connected to the server APIs. Learning and Tracking APIs are implemented in this file.


## Side projects
+ [Android app](https://github.com/ParsIOT/Find_BLE/)
