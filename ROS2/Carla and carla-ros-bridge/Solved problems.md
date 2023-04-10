2023.04.07
## - Module not found
注意使用python3 和 ros2 launch xxx.launch.py运行

## - carla attribute problem/ bridge process failed
#### 不要使用pip3 install carla！！！使用此种方法导入egg。虽然py3.8，egg写着3.7，但实际只要py3都兼容
#### 不知道是否bug：一定要这样写：${CARLA_ROOT}/PythonAPI/util，如果直接使用绝对路径还是报错
.bahrc
```
export CARLA_ROOT=/home/bing/workspaces/carla/carla13
export PYTHONPATH=$PYTHONPATH:${CARLA_ROOT}/PythonAPI/carla/dist/carla-0.9.13-py3.7-linux-x86_64.egg
export PYTHONPATH=$PYTHONPATH:${CARLA_ROOT}/PythonAPI
export PYTHONPATH=$PYTHONPATH:${CARLA_ROOT}/PythonAPI/util
export PYTHONPATH=$PYTHONPATH:${CARLA_ROOT}/PythonAPI/carla
export PYTHONPATH=$PYTHONPATH:${CARLA_ROOT}/PythonAPI/carla/agents


