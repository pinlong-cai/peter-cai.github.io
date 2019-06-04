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

*  CCS-1:
  In a situation with a low proportion of CAVs, the STA is similar to the general protocol. However, part of CAVs during red time can pass through the intersection by self-organization regardless of the signal status provided that their trajectories do not conflict those of the other vehicles. To avoid confusion in practical application, the privileged CAVs passing by selforganization are also supposed to obtain a permit from the control center, such as an extra marker light.
* CCS-2:
  In regular phases, a green light exists for mixed flow from a pair of non-conflicting directions to pass through the intersection. In special phases, the CAVs from all directions can pass by self-organization. Considering the fairness for both vehicles, regular and special phases both exist in each period. Owing to the permission for CAVs in the special phase, the CAVs must to drive into the other lanes and bypass the HVs stopping ahead of them. Deploying a pre-signal within a certain distance before the stop line is important. In regular phases, the pre-signal controls all vehicles to pass or stop; in the special phase, the HVs must queue before the pre-signal, whereas CAVs from all entrances can bypass the queue of HVs and go through the intersection by self-organization. 

# FINDINGS
* We set the flow of each lane from 50 veh/h to 500 veh/h and the penetrance to 0.5, which means that the probability of generating a CAV is equal to that of an HV. 
* The heterogeneity of the arriving vehicles of two passable lanes in green time causes a waste of green time under fixed STA and does not affect on the efficiency under CCS-1. Thus, the average delay time of the vehicles under the control of CCS-1 is approximately 3 s less than that under fixed STA with any flow.
* The average difference of DVPs between the two strategies is merely 1.6%. This finding means that CAVs and HVs benefit from the application of CCS-1 because the service capacity of the intersection increases.
* CCS-1 performs better than fixed STA when the penetrance is more than 0. As the improvement of fixed STA, CCS-1 does not influence the travel of HVs. Thus, replacing the fixed STA with CCS-1 once CAVs come into service is acceptable.
* The performance of CCS-2 dramatically changes from low to high penetrance. However, CCS-2 has high efficiency and the smallest average delay time and delayed vehicle proportion when the penetrance is more than 0.7.

# CONCLUSION
* With no effect on the functioning of HVs, the proposed composite control strategies can ensure the efficient passage of CAVs through intersections.
* CCS-1 can be adopted when the penetrance is smaller than 0.7, whereas CCS-2 performs better than does CCS-1 when the penetrance is larger than 0.7.
* The parameter of STA is changeable and must correspond to the real flow and penetrance at different intersections, especially time allocation between regular phases and the special phase in CCS-2.
