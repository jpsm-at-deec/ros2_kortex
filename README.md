- ros2 rolling from source (notes here https://github.com/jpsm-at-deec/ros2)
- Ubuntu 22.04.3

WIP for briging ros_kortex_vision[1] to ROS2[2]

[1] https://github.com/Kinovarobotics/ros_kortex_vision
[2] https://github.com/Kinovarobotics/ros2_kortex

(jpsm@deec.uc.pt)

```
export COLCON_WIP=~/workspace/ros2_kortex_wip
mkdir -p $COLCON_WIP/src
```

```
cd $COLCON_WIP
git clone https://github.com/jpsm-at-deec/ros2_kortex.git src/ros2_kortex
vcs import src --skip-existing --input src/ros2_kortex/vision_ros2.repos
vcs import src --skip-existing --input src/ros2_kortex/missing_ros2.repos
rosdep install --ignore-src --from-paths src -y -r
colcon build --cmake-args -DCMAKE_BUILD_TYPE=Release
source install/setup.bash
```
