### Run carla
```
./CarlaUE4.sh -quality-level=Epic -prefernvidia
```
### Start the ROS bridge with RVIZ enabled
```
ROS 1
roslaunch carla_ros_bridge carla_ros_bridge.launch
ROS 2
ros2 launch carla_ros_bridge carla_ros_bridge.launch.py
```
### Start RVIZ
```
# ROS 1
rosrun rviz rviz

# ROS 2
ros2 run rviz2 rviz2
# 进入rviz之后，file导入config
```
### Spawn an ego vehicle with the carla_spawn_objects package
```
# ROS 1
roslaunch carla_spawn_objects carla_spawn_objects.launch

# ROS 2
ros2 launch carla_spawn_objects carla_spawn_objects.launch.py
```
###  Control the ego vehicle with the carla_manual_control package (press B to enable manual steering, N to manual gearbox)
```
# ROS 1
roslaunch carla_manual_control carla_manual_control.launch

# ROS 2
ros2 launch carla_manual_control carla_manual_control.launch.py
```
