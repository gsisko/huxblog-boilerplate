---
layout: "post"
title: "7 DOF Arms - the New Kid on the Block"
date: "2018-11-26 21:00"
Author: "Gabriel Isko"
tags:
  - Robots
  - Industry
  - 7-DOF
---


Degrees of Freedom - Six and Beyond
------------------------

In industrial Robotics applications, the use of 6 Degree of Freedom serial manipulation arms is widespread.  6 degrees of freedom are the maximum amount of degrees of freedom that a free object can have in 3 dimensional space. They come from the three dimensions - width, height and depth, as well as the rotations around those three dimensions - roll, pitch and yaw:

![](assets/markdown-img-paste-20181126211133606.png)

By having 6 degrees of freedom, an industrial robot can manipulate an end effector as if it were a free object in space, bringing it to any point within it's work space from any orientation. The only limits of a 6 Degree of Freedom robot come from physical restraints. The length of the robot's joints, the movement range, and the speed all play a role in how fast and how far the robot can move it's end effector.

The most common configuration for a 6 Degree of Freedom robot in industry is as a serial manipulator. In a serial manipulator, the robot uses a series of joints, one attached to the end of the other. These joints are connected by hinges that allow each one to rotate with respect to the two connecting joints. For instance, here is a joint diagram of a [6 Degree of Freedom Arm]:  
![](assets/markdown-img-paste-20181126213204157.png)

Many industiral Robots depend on this configuration. For instance, all three [Universal Robots]' UR Models are 6 Degree of Freedom Serial Manipulators:

![](assets/markdown-img-paste-2018112622010019.png)

Other common arms from manufactuers such as Fanuc and Nachi also use 6 Degree of Freedom Serial Manipulators.
<div style= "box ={clear}">

|

</div>

Notice how in each of these robots, there are no two consecutive rotary joints that rotate around the same axis. If this were the case, the consecutive joints would be constrained to the same degree of freedom, and the serial manipulator would not have 6 degrees of freedom.

If a robot were to have more joints along it's chain, it would actually extend the number of Degrees of Freedom it has. However, because there are only 6 degrees of freedom in 3 dimensional space, any degrees of freedom beyond 6 are considered redundant. While it has been common practice. Within a robots workspace, redundant degrees of freedom do not help achieve new positions or orientations. However, it is becoming more common for industrial robots to incorporate 7 Degree of Freedom structures and include one redundant degree of freedom. To examine why, we must discuss the concept of singularities.

Singularities - the Bane of Serial Manipulators
------------------------------

Singularities in a Robot workspace occur when the robot has one degree of freedom unavailable to it, and it becomes less than a 6 degree of freedom manipulator. In these configurations, it is still possible for the robot to move the end effector to any position and orientation in the workspace, through the singularity. However, continuous motions cannot be made through a singularity - the end effector has to stop and wait for the arm to reconfigure itself, often until all six degrees of fredom are alailable.

It is much easier to show singularities than to just describe them. Singularties of Six degree of freedom Serial Manipulators can be broken into [three categories][Robotiq Singularities]:

- **Wrist Singularties**:

<img src="assets/wrist_singularity.gif" alt="Wrist Singularity">

Wrist singularities occur when the wrist joint is on the same axis of rotation as an earlier joint on the robot.

-**Elbow Singularities**
<img src="assets/elbow_singularity.gif" alt="Elbow Singularity">
This singularity occurs because 3 joints are co-planar with each other, and the movement of the robot along an entire plane is constricted. This singularity is what happens when the robot tries to reach to far, and occurs when the manipulator tries to reach past it's workspace.

-**Shoulder singularity**
<img src="assets/shoulder_singularity.gif" alt="Shoulder Singularity">
This singularity occurs when one of the wrist joints lines up with one of the base joints.
>All images were taken from [this video]().

When a singularity occurs, the robot cannot make a continuous linear move through a point. If we were to plot the joint velocities of each of these moves, they would actually trend towards infinity. Since it is impossible to achieve infinite speed, an industrial robot will often throw an error when a path is planned through a singularity. These errors can be disabled, however movement around the singularity can become unpredictable and become a safety hazard.

7 Degrees of Freedom to the Rescue
-------------------------
Since 6 Degree of freedom Serial Manipulators display this behavior around singularities, many robot makers are building 7 Degree of Freedom industrial robot arms.  With 7 Degrees of Freedom, the robot arms actually match the freedom of movement of a human arm.

By adding a single redundant degree of freedom, each of the singularities are eliminated. As industrial automation applications become more complicated, continuous motion through these singularity points are often necessary. If *you* have an application that requires complex motion throughout a large workspace, you should consider using the extra degree of freedom. 

<!-- sources -->

[Universal Robots]:https://www.universal-robots.com/?gclid=CjwKCAiA0O7fBRASEiwAYI9QAnmYyRTORDity8H-FiPwIuzoLP-1W2NirBj0SZUtqN2-YWz-ATx1nxoCFpgQAvD_BwE

[Singularity video]:

[Robotiq Singularities]: https://blog.robotiq.com/why-singularities-can-ruin-your-day

[6 DOF Arm Diagram]: https://www.researchgate.net/publication/261281825_A_screw_dual_quaternion_operator_for_serial_robot_kinematics
