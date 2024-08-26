[Reference](https://vlsitutor.com/nots/introduction-to-floorplan/)
[Implementation Methodology](Implementation%20Methodology.md)

## Contents
- [[#Steps|Steps]]
- [[#IO Cells|IO Cells]]
  - [[#Functions of IO Cells|Functions of IO Cells]]
  - [[#Connection to the Package|Connection to the Package]]
  - [[#Placement of IO Cells|Placement of IO Cells]]
- [[#Macro Placement|Macro Placement]]
  - [[#Initial Macro placement|Initial Macro Placement]]
  - [[#Types of Macros|Types of Macros]]
  - [[#Guidelines for placing Macros|Guidelines for Placing Macros]]
- [[#Width and Height of cells|Width and Height of Cells]]
  - [[#Core Utilization|Core Utilization]]
- [[#Chip Partitioning|Chip Partitioning]]
- [[#De-Coupling capacitors|De-Coupling Capacitors]]
  - [[#working|Working]]
- [[#Power Supply|Power Supply]]
	- [[Power Planning#Power Delivery Network|PDN]]
- [[#Pin Placement|Pin Placement]]




## Steps
- Decide Core height and width
- creates Power / ground connections 
- determines IO pin / pad placements
### Simple Layout for reference 
![[Pasted image 20240825122515.png]]

**Die area should account for :**
-  IO Cells/ IO Pads
-  Standard Cells
-  Macro + Halo (area around the macro where nothing must be placed) 
-  Interconnects
>Note :  Macro is a predefined and reusable blocks of logic which can perform specific tasks
## IO Cells
 -  special cells through which a chip communicates with the external world
 ![[Pasted image 20240825123043.png|300]]
###  Functions of IO cells
- Drive Capability
	- they enhance the drive capacity using buffers
- Voltage Transformation
- Protection from ESD (electro static discharge) 
### Connection to the Package
 ![[Pasted image 20240825123447.png|300]]

- Metallic pads (MPADs) are connected to the package using bond wires
- **Power Pads** 
	- Cells that provide power to the chip 
	- Number of power pads
		- Target level of internal voltage
		- Depends on the current drawn by the chip and current rating of the power pad 
### Placement of IO cells
- Assign nearby positions to two primary inputs that jointly drive a multi-input logic gate
- Spread power-hungry I/O cells all over the die area to avoid creating voltage drop hotspots 
- Avoid placing sensitive (such as clock signals) near IO cells

## Macro Placement
- Floor Planning we only place Macros not standard cells
- Macros are placed in floor planning since its easier to make any changes since they are lesser in number as compared to standard cells
### Initial Macro placement
	- Strongly connected macros are placed together
	- Fly lines guide the floor plan 
		- they indicate the number of nets going going in and out of the macros
		![[Pasted image 20240825125028.png|300]]
	- Macros interacting with IO is placed close to IO cells
### Types of Macros
- Hard macros 
	- non-flexible , Aspect ratio is not flexible
	- PPA and timing is fixed
	- available as ICs
	- industry graded
	
- Soft macros 
	- Aspect ratio is  flexible 
	- PPA and timing is unpredictable
	-  synthesizable RTL.
### Guidelines for placing Macros
- Allot contiguous region for standard cells
	 ![[Pasted image 20240825125314.png|200]]  ![[Pasted image 20240825125342.png|200]]
		Considering the above floor plans the right one has more contiguous space to place standard cells
- Avoid narrow channels for macros 
	- the aspect ratio can be changed if the macro is a soft macro  
		![[Pasted image 20240825125525.png|200]]  ![[Pasted image 20240825125647.png|200]]  ![[Pasted image 20240825125828.png|200]]
- Add Halos around Macros
	- if cells are placed too close to the macros there is congestion is formed after routing since all the wires will be congested in one place
		![[Pasted image 20240825232420.png]]
		
## Width and Height of cells 
Lets consider a basic example of a combo logic between capture and launch flops. Each cell and each flop will have dimensions (in this case lets take unit dimensions). Now to produce the components of the netlist (cell and flops) , it needs to be structured on the silicon wafer die. Hence I would need to place these components of the netlist in certain way such that it fits in the core to be placed on the die.

![[Pasted image 20240824150648.png]]
![[Pasted image 20240824150700.png]]

**Utilization factor** = Area of the netlist / Total area of the core ( < 1 usually 0.5/0.6 )  
**Aspect ratio** = Height / Width of the core ( if 1 --> square core; else --> rectangle core )  

### Core Utilization:
-  Utilization: Utilization defines the area occupied by standard cell, macros and blockages. In general, 70 to80% of utilization is fixed because more number of inverters and buffers will be added during the process of CTS (Clock Tree Synthesis) in order to maintain minimum skew.
-  A core utilization of 0.8 means that 80% of the area is available for placement of cells, whereas 20% is left free for routing.

The below image explains the factors
![[Pasted image 20240824150720.png]]

## Chip Partitioning
lets consider a combo logic which consists of a massive number of gates (50,000). When implementing this on a single die the utilization factor will surely increase. Hence the gates are partitioned into smaller blocks with input and outputs between these blocks. These blocks can further be converted to a black box to aid in reusability of the function in the design.

![[Pasted image 20240824150855.png]]
When hard macros such as memory, comparator,.. etc. are used in the designs, these locations are user defined and the tools will not touch these IPs during the automated PnR flow.



## De-Coupling capacitors
![[Pasted image 20240824180810.png]]
Memory elements are often placed close to the input sides and served as pre placed cells . Connectivity with these supplies are done with supply/power wires . The physical distance causes a voltage drop and in such cases the voltage supplied to the cells are not enough to meet the noise margin specifications . In such cases De-coupling capacitors are used .
![[Pasted image 20240824181325.png]]
The capacitor gets the voltage almost equal to the supply voltage , since they are close to the blocks there will not be drop in voltage .
> More reference for necessity of Decoupling capacitors [[Power Planning#Voltage Drop]]
### working 
- When there is no switching activity happening the capacitor charges 
- It discharges when there is switching activity happening 
![[Pasted image 20240824181740.png]]

In the block it looks like the above figure

## Power Supply
The power fluctuation issue was stabilized for a local module using de-coupling capacitors .
Now we have the macro repeated multiple times 

![[Pasted image 20240824182443.png]]
								Let the orange wire be 16 bit bus
It is not feasible to have capacitors throughout the chip

A 16 bit bus can be represented as

![[Pasted image 20240824182948.png]]

When all the capacitors discharge at the same time there is a momentary increase in the ground voltage this is called **Ground Debounce** 

![[Pasted image 20240824183457.png]]

When all the capacitors charge at the same time there is a momentary decrease in the ground voltage this is called **Voltage Droop**

![[Pasted image 20240824183749.png]]

if the voltage droop goes below the noise margin an issue is caused

This problem is caused by having a single power supply

![[Pasted image 20240824183910.png]]

Voltage droop and Ground Debounce can be solved by giving multiple power supplies given in form of a mesh . Hence the capacitor closest to the power line can tap into whichever needed. VDD power lines are placed in vertically and horizontal layers with metal contacts. The GND lines are also placed similarly in the same level as VDD. However it is made sure that both these lines are isolated from each other.
![[Pasted image 20240824184304.png]]

**Demerits** - > increases die area , leakage power dissipation
Number of De-coupling capacitors should be optimized 
## Pin Placement

Let us consider the following circuit , Where Block A,B,C  are Pre placed Cells 

![[Pasted image 20240824184720.png]]

The input ports are placed on the left, and the output ports are placed on the right. Clock ports are made larger than other ports because they drive the entire load and require minimal resistance in the signal path. The pins are optimized by distributing the fanout from a central point, with various factors like connectivity, proximity, and pin type (e.g., I/O, clock, power/ground) considered during placement within the designated area.
![[Pasted image 20240824185108.png]]


