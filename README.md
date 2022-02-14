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

## \<env\> tag

The <env> tag allows you to set environment variables on nodes that are launched. This tag may only be used within the scope of a <launch>, <include>, <node> or <machine> tag. When it is used inside of a <launch> tag, the <env> tag only applies to nodes declared after.

NOTE: Values set using the <env> tag will not be seen by $(env ...), so the <env> tag cannot be used to parametrize launch files.
  
 - Reference: [link1](http://ros.informatik.uni-freiburg.de/roswiki/roslaunch(2f)XML(2f)env.html)
  
## Env Hooks
  
For more information on using environment hooks, please check out this repository. https://github.com/BruceChanJianLe/ros-env-hooks
