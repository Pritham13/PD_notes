- Placer needs to compute the wirelength of each net multiple times 
- Ideally the estimated wirelength should match the post routing wirelength
## Methods to estimate the wirelength

### Half Perimeter Wirelength (HPWL)
- Easy to compute 
- Half of the perimeter of the bounding rectangle encloses all the pins of a net
- Half of the perimeter of the rectangle that encloses all the pins of a net is the Half Perimeter Wirelength estimate of the bounding box
- Widely used 
- ![[Pasted image 20240824114541.png]]
	- Lets try to estimate the wire length of the above figure
	- Let the below figure be the placed cells
	 ![[Pasted image 20240824114557.png]]
	 - using the most simple method the estimation is 
	 ![[Pasted image 20240824114714.png]]
	 
	