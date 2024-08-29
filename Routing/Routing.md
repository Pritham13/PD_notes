## Introduction
Routing is the process of making interconnections between different components of the design  

## Global Routing
creates plan of routing for each net (in terms of routing regions ) and the actual layout of nets are not made
![[Pasted image 20240828185854.png]]
### Routing Model
Routing is divided into rectangular grids and each of these grids are known as **Global Bins** (aks GB ,global tile, routing tile , global Cell or bucket)
#### Grid Graphs
it is build using Global Bins 
- Vertices (v) : GBs
- Edges : represent boundary between adjacent GBs
![[Pasted image 20240828200021.png]]

If we run a large number of nets through an edge and the capacity which basically is the user constraint given to the number of nets passing through the edge .
overflow = number of nets passing through the edge - the cap on the number of nets to be used per edge

congestion = use(e)/capacity(e)

global routing tries to get an overflow of 0


## Detailed Routing
to determine the exact layout of the net , including all the attributes of wire segments such as width and location

### Constraints and considerations
- Design rules
- Connectivity
- timing
- Signal integrity 