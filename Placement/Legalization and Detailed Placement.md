## Intro
- The overlap caused in Global Placement are removed
- Cells are moved to legal locations
- Placement is illegal If :
	- Cells overlap
	- Cells occupy illegal site (ex : between Placement rows)
		![[Pasted image 20240824121230.png| 400]]
- **Legalization** 
	- Removes all overlaps and snap cells to legal sites
		- with minimum impact on wirelength , timing and congestion		 ![[Pasted image 20240824121506.png]]
		- As seen it does not do much optimization just makes small snaps or moves to put it in the legal zone as larger moves would require recalculation and optimization of wirelengths
- **Detailed Placement**
	- Improve the QoR by incremental changes to the cell locations
	- improves wirelength and routability by :
		- swapping location of neighboring cells
		- Re-Distributing free sites
		- Moving cells to unused locations
- **Timing-driven Placement**
	- Performs timing analyses internally and incrementally during placement
		- Makes incremental (small) changes to the cells and analyses the timing of the model 
			- optimizes based on the timings
		- Target Worst Negative slack (WNS) and the Total Negative Slack (TNS)
			- among the negative slack the one having the worst slack is called worst negative slack 
			- When we have many negative slacks we targeting WNS may not work then we target the TNS
	- Controls the proximity of the cells that are on the critical path
		- decreases the wirelength by bringing cells closer in order to decrease the interconnect delay
