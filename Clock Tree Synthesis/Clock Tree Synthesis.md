## Contents
- [Introduction](#introduction)
- [Terminologies](#terminologies)
  - [Source](#source)
  - [Sinks](#sinks)
  - [Clock Tree](#clock-tree)
  - [Insertion Delay/Delay/Latency](#insertion-delaydelaylatency)
  - [Clock Skew](#clock-skew)
  - [Global Clock Skew](#global-clock-skew)
- [Buffers](#buffers)
  - [Buffer Placement and Impact on Delay](#buffer-placement-and-impact-on-delay)
- [Clock Distribution Network](#clock-distribution-network)
  - [Global Clock Distribution](#global-clock-distribution)
    - [Symmetric Tree Architecture](#symmetric-tree-architecture)
      - [H-tree](#h-tree)
      - [X-tree](#x-tree)
    - [Mesh Architecture](#mesh-architecture)
      - [Advantages of Mesh Architecture](#advantages-of-mesh-architecture)
      - [Disadvantages of Mesh Architecture](#disadvantages-of-mesh-architecture)
  - [Local Clock Distribution](#local-clock-distribution)

## Introduction
Clock tree synthesis implements clock distribution structure on the layout having similar behavior to that of an ideal clock
- Minimizes clock skew 
- inserts clock buffers or inverters 
- Targets Lower power consumption
	- clock distribution consumes significant portion of active power (25 to 70)
- The quick up downs in signal lines can impact other lines getting signal integrity issues
## Terminologies
**Source** --> starting point of the clock 
**Sinks** --> final receiving end points of the clock signal
**Clock Tree** --> clock distribution network arranged in form of a clock
**Insertions delay/delay/latency** --> time taken to propagate though the clock tree and reach the clock sink
**Clock Skew** --> difference in arrival time of clock signal between a pair of sinks S1 and S2 
**Global Clock Skew** --> max value of clock skew between any pair of sinks

## Buffers
imagine a wire with length 2L the time taken to propagate is 

![[Pasted image 20240826121801.png]]

taking a buffer at L the delay becomes
![[Pasted image 20240826121832.png]]

if we neglect the buffer delay the delay becomes
![[Pasted image 20240826121857.png]]

which is half of the initial one .
if the delay is too high it will result in high slew 

## Clock Distribution Network

| **Global Clock Distribution**                                                       | **Local Clock Distribution**                   |
| ----------------------------------------------------------------------------------- | ---------------------------------------------- |
| Distributes clock to various parts of chips and over a large area                   | Distributes clock to smaller parts of circuits |
| Clock Buffers are large and more                                                    | Clock Buffers are smaller and fewer            |
| Consume large power                                                                 | Consume less power                             |
| Top-level Clock Distribution Network needs to be planned (more manual intervention) | Automated Clock Tree Synthesis can be used     |



### Global clock distribution network
#### Symmetric Tree Architecture 
- Clock is routed through a central point in the chip 
- symmetric architecture forks out of the centre
- Examples :
	- **H-tree**
		![[Pasted image 20240826123254.png]]
		- **X-tree**
		![[Pasted image 20240826123341.png]]
		- Due to PVT variations skew is still observed
- Non tree architectures can reduce clock skew
	![[Pasted image 20240826123649.png]]
#### Mesh architecture 
 Ensures more paths between mesh drivers and clock sinks
-  Very small skew
-  Decreased impact of process induced variations
	![[Pasted image 20240826124001.png|400]]
	
Disadvantages:
-  Increases total capacitance and the size of clock drivers
-  Increases power consumption (due to increased capacitance and short-circuit power dissipation)

