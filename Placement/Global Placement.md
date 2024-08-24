## Basics
- Cells are Spread over the core area
- wire length is tried to be memories
- spread out cause routing resources can be utilized effectively
- Overlapping may exist because dimensions are not considered
- ### Analytical Placement Algorithm
	- Considers each cell as point object with co-ordinates (xi,yi)
	- Cost Function ( such as wirelength ) and constants are defined mathematically 
		- wirelength is a function of
		![[Pasted image 20240824115448.png]]
		-  based on this we get total wirelength
		-  and use solvers to get min length
		- Suitable constraints should be given
		- cost related cell density is added
	- Cells are allowed to overlap in Global Placement