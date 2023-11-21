# Navigation-and-localization-ROS-Turtlebot3-

Package ROS with param and launch for EKF localization and robot navigation. 

This package require *robot_localization* package for use the localization with odom and IMU or odon, IMU and trilateration for Xbee.

To use the navigation require *move_base*, *global_planner*, *rrt_star_global_planner*, *dwa_local_planner* and *teb_local_planner* packages.

The sources is here:
   - *robot_localization*: https://github.com/cra-ros-pkg/robot_localization
   - *trilateration for Xbee*: https://github.com/NicolasNNA/trilateration_xbee_ros
   - *move_base*: http://wiki.ros.org/move_base
   - *global_planner*: http://wiki.ros.org/global_planner
   - *rrt_star_global_planner*: https://github.com/rafaelbarretorb/rrt_star_global_planner
   - *dwa_local_planner*: http://wiki.ros.org/dwa_local_planner
   - *teb_local_planner*: http://wiki.ros.org/teb_local_planner
