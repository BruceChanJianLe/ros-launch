# ROS Launch

This repository demonstarte the usage of roslaunch file.

## Delaying node in launch file

There is two option in delaying a node from running in launch file.
- Within a same launch file
```xml
<arg name="node_start_delay" default="1.0" />  
<node name="listener" pkg="roscpp_tutorials" type="listener" launch-prefix="bash -c 'sleep $(arg node_start_delay); $0 $@' " />
```
- In another launch file (use timed_roslaunch)

- Reference: [link_rosanswer](https://answers.ros.org/question/233353/set-delay-between-starting-nodes-within-launch-file/)
- Reference: [link_roswiki](http://wiki.ros.org/timed_roslaunch)

## \<rosparam\> tag

```xml
<?xml version="1.0" encoding="UTF-8"?>

<launch>

    <arg name="my_env_var" default="$(optenv MY_ENV_VAR '')"/>

    <group if="$(eval my_env_var == 'Successfully setup!')">
        <rosparam param="debug">true</rosparam>
    </group>

    <group unless="$(eval my_env_var == 'Successfully setup!')">
        <rosparam param="debug">false</rosparam>
    </group>

</launch>
```
For more information, please visit https://wiki.ros.org/roslaunch/XML/rosparam.

## \<env\> tag

The <env> tag allows you to set environment variables on nodes that are launched. This tag may only be used within the scope of a <launch>, <include>, <node> or <machine> tag. When it is used inside of a <launch> tag, the <env> tag only applies to nodes declared after.

NOTE: Values set using the <env> tag will not be seen by $(env ...), so the <env> tag cannot be used to parametrize launch files.
  
 - Reference: [link1](http://ros.informatik.uni-freiburg.de/roswiki/roslaunch(2f)XML(2f)env.html)
  
## Env Hooks
  
For more information on using environment hooks, please check out this repository. https://github.com/BruceChanJianLe/ros-env-hooks

## ROS Service
```xml
<?xml version="1.0"?>

<launch>

  <!-- remove pallet from the scene -->
  <node pkg="rosservice" type="rosservice" name="remove_pallet" args="call --wait /gazebo/delete_model 'model_name: 'aws_robomaker_warehouse_PalletJackB_01_001''" />

</launch>
```

## \<include\> tag

This launches another launch file.

```xml
<?xml version="1.0"?>

<launch>

  <!-- launch another launch file -->
  <include file="$(find pkg-name)/path/filename.launch"/>

</launch>
```

- Reference: https://wiki.ros.org/roslaunch/XML/include
