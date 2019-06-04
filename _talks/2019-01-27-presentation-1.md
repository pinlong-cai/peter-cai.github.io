---
title: "COMPOSITE CONTROL STRATEGY FOR SHARING HUMAN-DRIVEN AND AUTONOMOUS VEHICLE INTERSECTIONS"
collection: talks
type: "Tutorial"
permalink: /talks/2019-01-27-talk-3
venue: "97th Annual Meeting of the Transportation Research Board"
date: 2019-01-27
location: "Washington DC, USA"
---

[More information here](http://exampleurl.com)

# BACKGROUND
* Reliable communication networks and internal intelligent control units ensure that connected autonomous vehicles (CAVs) can perform normal motion functions without human control.
* The availability of CAVs to the common people will increase their popularity because they can liberate humans from highly intensive operations.
* Unlike human-driven vehicles (HVs), CAVs have validated technologies that can improve vehicle safety and reduce the number of traffic incidents.

# HIGHLIGHT
* Propose two composite control strategies combining STA and self-organization, named CCS-1 and CCS-2, which are oriented to sharing passing at intersections.
* Discuss the passing efficiency of different strategies varying with the change of flow and penetrance.
* Results indicate that the proposed composite control strategies can be used in practical application to improve the capacity of sharing intersections.

# METHODOLOGY
* Compared with HVs, CAVs have considerable privilege in passing through intersections at any time provided that they do not conflict with HVs. The traffic rules of CAVs are as follows.
* During green time, CAVs from the permitted direction can pass through the intersection, similar to the HVs.
* During the other times, CAVs can pass through the intersection according to the occupation status of conflict points in their estimated trajectories. If these points are unoccupied within the estimated passing slots, then the CAVs are permitted to go. These permitted CAVs are called “privileged CAVs.” The key point of self-organization passing strategy is deciding the departure sequence of the privileged CAVs to improve effectiveness. In this work, we use Monte Carlo tree search (MCTS) to solve this problem. Then, we propose two composite control strategies for mixed flow with HVs and CAVs in this research.

# COMPOSITE CONTROL STRATEGIES 

(1) CCS-1
In a situation with a low proportion of CAVs, the STA is similar to the general protocol. However, part
of CAVs during red time can pass through the intersection by self-organization regardless of the signal
status provided that their trajectories do not conflict those of the other vehicles.
To avoid confusion in practical application,
the privileged CAVs passing by selforganization are also supposed to obtain a
permit from the control center, such as an
extra marker light.
