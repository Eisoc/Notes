## Open Carla server
```
./CarlaUE4.sh -quality-level=Epic -prefernvidia
```
## Start ROS-Bridge with ego_vehicle
```
ros2 launch carla_ros_bridge carla_ros_bridge_with_example_ego_vehicle.launch.py
```
## Start Rviz and config
```
ros2 run rviz2 rviz2
```
## Start Waypoint_publisher
#### ~/carla-ros-bridge/src/ros-bridge/carla_waypoint_publisher/src/carla_waypoint_publisher/carla_waypoint_publisher.py
#### when there is a goal published or there is a goal default, it will calculate the route and give the waypoints.
```
ros2 launch carla_waypoint_publisher carla_waypoint_publisher.launch.py
# terminal 2: subscribe the topic and check if the goal is published
ros2 topic echo /carla/ego_vehicle/goal
```
## connect ad_agent to start autonomous drving mode
```
ros2 launch carla_ad_agent carla_ad_agent.launch.py 
```
## give the wanted speed to the agent, unit:m/s
```
ros2 topic pub /carla/ego_vehicle/target_speed std_msgs/Float64 "{data: 9.0}"
```
# BRANCH: manual set the goal
#### use 2d Navi goal in the rviz and in the terminal of rviz it will show the pos of the goal,for example
#### [INFO] [1681145423.171937835] [rviz2]: Setting estimate pose: Frame:map, Position(92.2649, -270.035, 0), Orientation(0, 0, 0.597592, 0.8018) = Angle: 1.28099
#### Then we can manually publish this. Tips:W is always 1 or 0(two direction of lanes)
```
ros2 topic pub /carla/ego_vehicle/goal geometry_msgs/PoseStamped "{header: {frame_id: 'map'}, pose: {position: {x: 118, y: -198, z: 0.0}, orientation: {w: 1}}}"
```
# BRANCH: use 2D navi Goal in Rviz to set the goal
/home/bing/carla-ros-bridge/src/ros-bridge/carla_waypoint_publisher/src/carla_waypoint_publisher/carla_waypoint_publisher.py
```
        # set initial goal
        self.goal = self.world.get_map().get_spawn_points()[0]

        self.current_route = None
        self.goal_subscriber = self.new_subscription(
            PoseStamped,
            #原代码：，订阅主题并不是RVIZ navi goal，修改为下面一行内容后即可使用 "/carla/{}/goal".format(self.role_name),
            '/move_base_simple/goal',
            self.on_goal,
            qos_profile=10)
```

ros2 launch carla_ad_demo ad_agent_waypoint.launch.py town:=Town10HD_Opt spawn_point:=-24,-135.4,2,0,0,180

