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


=========================================
Parsin Server
=========================================

Introduction
===========================
**ParsinServer** is a Fingerprint-based Indoor Positioning System based on `Find <https://github.com/schollz/find>`_. In `Parsiot <https://parsiotco.ir>`_, we are working on Indoor Positioning Solutions and ParsinServer is one of the main products that we were working on. After developing the code for two years, in the end, we decided to make the code free and opensource. Our reasons are as follow:

* **Find is opensource** : Although we changed and refactor the code base, we used Find when we started. Therefore, we sense that as our duty to make the code opensource.
* **Help other research** : As we spend a lot of our time to test and research on Fingerprint-based IPS solutions, We know how it can be useful or precious for any researcher to start their study and research on the pre-build code base.
* **Opportunity for new contributions** : Current IPS solutions that work with Wi-Fi and BLE are usually based on heuristic ideas. So we need others to contribute.



.. attention::
    We don't provide documentation for ParsinServer and the code accessories(e.g. the Android and ios app). If you need more help email me (`Mohammad Hadi Azaddel, m.h.azaddel -- at -- gmail.com`).

.. _Quickstart Concepts:

Capabilities
===========================

**ParsinServer** contains complete capabilities as follow:



1. Main Dashboard

    .. image:: ParsinServer/docs/images/d1.png
        :alt: Dashboard

Dashboard consists of :
    * Algorithm configs
    * Algorithm hyperparameter tuning
    * Display Algorithm details
    * Upload different map image
    * Total algorithm evaluation

2. Collecting and Showing Fingerprints

    .. image:: ParsinServer/docs/images/d2.png
        :alt: Fingerprint Map



3. Live user positioning:
    * User Management
    * Collaboration with PDR solutions(on the android app)
    * Live UWB localization

    .. image:: ParsinServer/docs/images/d3.png
        :alt: Live map

4. Arbitrary fingerprint location:

    .. image:: ParsinServer/docs/images/d4.png
        :alt: Arbitrary Location

5. Access Points management:

    .. image:: ParsinServer/docs/images/d5.png
        :alt: access points locations

6. Fingerprint ambiguity: helps to find similar fingerprints

    .. image:: ParsinServer/docs/images/d6.png
        :alt: fingerprint ambiguity map

7. Graph & Map: This tool provides:
    * Set map constraints and borders(It can be used in Particle Filter models)
    * Set valid connections between nodes

    .. image:: ParsinServer/docs/images/d7.png
        :alt: Map borders

    .. image:: ParsinServer/docs/images/d8.png
        :alt: Connection links

8. RSS heatmap

    .. image:: ParsinServer/docs/images/d9.png
        :alt: RSS heatmap

9. Error heatmap:

    .. image:: ParsinServer/docs/images/d10.png
        :alt: Error heatmap

10. Offline tracking: Use to evaluate offline collected test data. E.g. in the below figure, you can see user track as a timeline.

    .. image:: ParsinServer/docs/images/d11.png
        :alt: Test track map

10. Error calculation: This is a complete panel to get different algorithm localization accuracy and localization details like the association between real fingerprint and the estimated positions.

    .. image:: ParsinServer/docs/images/d12.png
        :alt: Algorithm error calculation

11. Error comparison and CDF graph:

    .. image:: ParsinServer/docs/images/d13.png
        :alt: CDF1

    .. image:: ParsinServer/docs/images/d14.png
        :alt: CDF2

12. Particle Filter algorithm
13. UWB compatible data collection: You can collect fingerprints with the accurate localization systems like UWB. ## `Android and ios app <https://github.com/schollz/find>`_

Side Projects
===========================

14. `Tag tracking <https://github.com/ParsIOT/Parsin-rtls>`_ : You can use BLE and Wi-Fi tags and some signal receivers to track tags.
15. `Android app <https://github.com/ParsIOT/Find_BLE/>`_ and `react-native app (ios) <https://github.com/ParsIOT/RNative>`_
16. Proximity advertisement framework, `Parsin Admin Panel <https://github.com/ParsIOT/Parsin-Admin-Panel>`_. It works alongside Parsinserver. Besides we provided a proximity advertisement.
