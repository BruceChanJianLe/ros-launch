# ROS Launch

This repository demonstarte the usage of roslaunch file.

## \<env\> tag

The <env> tag allows you to set environment variables on nodes that are launched. This tag may only be used within the scope of a <launch>, <include>, <node> or <machine> tag. When it is used inside of a <launch> tag, the <env> tag only applies to nodes declared after.

NOTE: Values set using the <env> tag will not be seen by $(env ...), so the <env> tag cannot be used to parametrize launch files.
  
 - Reference: [link1](http://ros.informatik.uni-freiburg.de/roswiki/roslaunch(2f)XML(2f)env.html)
