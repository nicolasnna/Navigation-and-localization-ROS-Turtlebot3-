# Navegación y localización de Turtlebot3 en ROS

Paquete ROS con parámetros y lanzador para localización por fusión de sensores con EKF y navegación del robot.

El paquete utiliza `robot_localization` para emplear la fusión de sensores con EKF utilizando la odometría, IMU y trilateración con Xbee. Para esto último, es necesario el paquete `trilateration_xbee_ros`.

Para la navegación utiliza el paquete `move_base` y distintos planificadores locales y globales: RRT Star, A*, DWA y TEB.

# Requisitos

* ROS Noetic
* Catkin Tools
* Rviz
* Turtlebot3

# Dependencias

* [robot_localization](https://github.com/cra-ros-pkg/robot_localization)

* [trilateration_xbee_ros](https://github.com/NicolasNNA/trilateration_xbee_ros)

* [move_base](http://wiki.ros.org/move_base)

* [rrt_star_global_planner](https://github.com/rafaelbarretorb/rrt_star_global_planner)

* [global_planner](http://wiki.ros.org/global_planner)

* [dwa_local_planner](http://wiki.ros.org/dwa_local_planner)

* [teb_local_plannner](http://wiki.ros.org/teb_local_planner)

# Utilización

> [!NOTE]
> Los parámetros para la localización y navegación, se ajustan en archivos formato YAML en la carpeta `param`.

Para la localización por fusión de sensores se dispone de dos archivos _roslaunch_ dependiendo de los sensores y técnicas utilizadas en el robot:

* `localization_odom_imu.launch`: Emplea la odometría del robot y los datos de la IMU para la fusión de sensores.

```
roslaunch robot_navigation_turtlebot3 localization_odom_imu.launch
```

* `localization_fusion.launch`: Emplea la odometría del robot, datos de la IMU y la posición entregada por la trilateración con Xbee.

```
roslaunch robot_navigation_turtlebot3 localization_fusion.launch
```

Para la navegación es necesario un mapa del entorno (carpeta `maps`). Para obtenerlo se puede emplear métodos SLAM con LiDAR, como por ejemplo _gmapping_:

```
roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
```

Se tienen definidos distintas combinaciones de planificadores, las cuales pueden ser utilizados para la navegación:

* A* - DWA (`astar_dwa`)
* A* - TEB (`astar_teb`)
* RRT* - DWA (`rrtstar_dwa`)
* RRT* - TEB (`rrtstar_teb`)

Para seleccionar una combinación, se debe especificar el parámetro `planner` en el _roslaunch_:

```
roslaunch robot_navigation_turtlebot3 turtlebot3_navigation.launch planner:=astar_dwa
```


