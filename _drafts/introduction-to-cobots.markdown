---
layout: "post"
title: "Introduction to Cobots"
subtitle: "Everything you wanted to know about Cobotics"
Author: "Gabriel Isko"
date: "2018-11-06 18:10"
tags:
  - Robots
  - Industry
  - Cobots
---

The Need for Cobotics
---------------

 Industrial Robots are used to automate tasks that are to complicated, to repetitive, or too dangerous for humans to accomplish manually. In order to accomplish these tasks, the power output and payload forces of an industrial Robot are often beyond what is safe for humans to interact with.

In the deployment of these industrial robots, it is required to take various safety precautions to ensure that human operators will not come into contact with the Robots During operation. You can see in page `iv` in the [Safety Precaution][FanucUserManual] preamble to the *Fanuc R-30iA* controller that an outline is given for safety connections and emergency stop wiring to the Robot controller. It outlines that a safety fence must be installed around the Robot arm, and gives an example diagram.

![](../img/Fanuc_SafetyFence.png)


In section **1.1.1** The [manual][FanucUserManual] outlines:

>[Robot] Operators cannot work in the inside of the safety fence.

Accepted insustrial robotics safety precautions are outlined by international safety standard [ISO 10218-1:2011](ISO_Robot_Standard). While this safety standard gives some consideration to guidelines regarding collaborative robotics applications, it is quite vague and does not clearly define the safety considerations needed to create a collaborative robot. New advances in robotics research have allowed industrial robotics to manufacture robots that can safely operate in collaboration with human operators. ISO has responded by publishing the [ISO 15066][ISO_Cobot_Specification] which gives new clarity regarding the guidelines for collaborative Robotics operation and safety. With these standards in place, Robot makers can ensure that they are using the best available practices for building and implementing collaborative Robots.

What are Cobots?
-------------------

By adhering to safety practices, Cobots are able to perform industrial applications alongside human operators. While non-collaborative industrial robots require external safety devices to be safe, cobots are designed for the possibility of contact with humans. Safety measures must be implemented to ensure that human-robot contact does not result in injury. [ISO 15066][ISO_Cobot_Specification] specifies two contact scenarios:

- Transient contact
  - Classification of short contact (<50ms). In a transient contact instance, the human body part is not constrained and is free to recoil. In transient contact scenarios the peak force and energy transfer must be accounted for in the safety design.
  ![Cobot Safety Development](assets/markdown-img-paste-20181108171216826.png "Transient Contact Illustration")
- Quasi-Static Contact
  - Classification for extended contact scenario between the human and the Cobot, caused when the human body part is constrained and cannot pull away. Along with the considerations for transient contact, the pressure and stress the robot exerts must be accounted for. Therefore, factures such as contact area and duration must be taken into consideration for the safety design of the Cobot during these scenarios.
   ![Cobot Safety Development](assets/markdown-img-paste-20181108171232289.png "Quasi-Static Contact illustration")

You should notice that most of the values in both these contact scenarios are generally fixed values - the Mass and contact area of an industrial robot is based on it's construction and doesn't normally change during operation. Safety designers seek to limit the duration of contact to be as short as possible once contact is detected by the cobot. Therefore, the main design task for collaborative Robots is force sensing and limiting. By limiting the force it exerts, the cobot can ensure that none of the thresholds outlined in [ISO 15066][ISO_Cobot_Specification] are broken in the event of a contact scenario.

Force Limiting
-------------------

The first, and easiest method to make sure that a cobot doesn't exert a dangerous amount of force during a contact scenario is to design it so that it is unable to exert a dangerous amount of force in any scenario. The first method is to deign the size of the Robot so that it is incapable of exerting enough force to exceed a set limit. In the case of transient contact, this is very important since limiting the amount of force directly limits the amount of energy the robot will transfer in that contact scenario.

In Quasi Static contact scenarios, more sophisticated approaches to force control are required. One approach is to be able to sense the force the cobot exerts by monitoring the current draw of its output motors, and finding the exerted torque that the motors are outputting, and calculating the force output at the end effector of the cobot. The torque or force of an electric actuator can be calculated by monitoring the current draw of the actuator. Using current draw measurements, torque output of each actuator can be calculated. Electronic implementations for sensing current are quite common, and are often constructed by applying the use of an operational amplifier. For instance, [Linear Technology] of [Analog Devices][Linear Technology] offers the [LT6100][LT6100 Datasheet] package, which is recommended for use in current sensing applications. An example deployment of the amplifier for current sensing is given in the [LTC6100 Datasheet]:

![](assets/markdown-img-paste-20181113164243520.png)

As you can see from the above schematic, the LTC6100 will output a mirror of the voltage across $R_sense$ in the above schematic. By implementing this circuit on the power supply rail of an output actuator the current draw of the actuation can be measured by knowing the value of $R_sense$, and using ohm's law: $V=IR$. With the output current measured, the robot can effectively measure the torque output of an electric actuator. By doing this at each of it's output joints, the possible force transfer during a contact scenario can be calculated, and a safety condition can be triggered if it exceeds the value specified in [ISO 15066][ISO_Cobot_Specification].





<!-- sources -->
[InjuryForces]:http://www.hse.gov.uk/research/hsl_pdf/2003/hsl03-09.pdf
[FanucUserManual]: http://rab.ict.pwr.wroc.pl/~malewicz/Fanuc/Fanuc/iRVision_Operation_Manual_V7.50Pxx_%5BB-82774EN03%5D.pdf
[ISO_Robot_Standard]: https://www.iso.org/obp/ui/#iso:std:iso:10218:-1:ed-2:v1:en
[ISO_Cobot_Specification]: https://www.iso.org/obp/ui/#iso:std:iso:ts:15066:ed-1:v1:en
[ANSI_Robot_Standard]: https://www.robotics.org/robotics/safety-resources
[ANSI_Cobot_Specification]: https://webstore.ansi.org/Standards/ISO/ISOTS150662016
[OSHA_Robot_standard]: https://www.osha.gov/dts/osta/otm/otm_iv/otm_iv_4.html

[Cobot_Safety]: https://cobotsguide.com/safety/
[Robotiq ISO]: https://blog.robotiq.com/hubfs/eBooks/ebook-ISOTS15066-Explained.pdf?hsLang=en-ca&t=1541623946382
[Cobot Safety Development]: https://www.researchgate.net/publication/282809861_ISOTS_15066_-_Collaborative_Robots_-_Present_Status
[Robotiq Force sensing Blog]:http://blog.robotiq.com/hubfs/Force_Sensors_in_Robotics_Research.pdf


[LTC6100 Datasheet]: https://www.analog.com/media/en/technical-documentation/data-sheets/6100fd.pdf
[Linear Technology]: https://www.analog.com/en/index.html

[UR Force FAQ]: https://www.universal-robots.com/how-tos-and-faqs/how-to/ur-how-tos/seek-using-force-16117/
