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

## The Need for Cobotics

 Industrial Robots are used to automate tasks that are to complicated, to repetitive, or too dangerous for humans to accomplish manually. In order to accomplish these tasks, the power output and payload forces of an industrial Robot are often beyond what is safe for humans to interact with.

In the deployment of these industrial robots, it is required to take various safety precautions to ensure that human operators will not come into contact with the Robots During operation. You can see in page `iv` in the [Safety Precaution][FanucUserManual] preamble to the *Fanuc R-30iA* controller that an outline is given for safety connections and emergency stop wiring to the Robot controller. It outlines that a safety fence must be installed around the Robot arm, and gives an example diagram.

![](../img/Fanuc_SafetyFence.png)


In section **1.1.1** The [manual][FanucUserManual] outlines:

>[Robot] Operators cannot work in the inside of the safety fence.

Accepted insustrial robotics safety precautions are outlined by international safety standard [ISO 10218-1:2011](ISO_Robot_Standard). While this safety standard gives some consideration to guidelines regarding collaborative robotics applications, it is quite vague and does not clearly define the safety considerations needed to create a collaborative robot. New advances in robotics research have allowed industrial robotics to manufacture robots that can safely operate in collaboration with human operators. ISO has responded by publishing the [ISO 15066][ISO_Cobot_Specification] which gives new clarity regarding the guidelines for colaborative Robotics operation and safety. With these standards in place, Robot makers can ensure that they are using the best available.




## What are Cobots?


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
