![[Pasted image 20240825232825.png]]
**Power Pads** : Supply power to the chip from external world 
**Power Rings** : carry power around the periphery of the die
- Usually top metal layer
	- top layer is used because the thickness of the interconnects is more at the top layer therefore the resistance will be lower and the voltage drop will be less
- Number of power pads required is dependent on the current and voltage required by the module
## Power Delivery Network

![[Pasted image 20240825233341.png]]

The above diagram shows the mesh Grid topology :
 - Popularly known as the PDN
 Advantages of mesh grid topology
 - Provides reliability 
 - Uniform distribution of current
 - low resistance 
 > Note : the width or spacing between the rails is usually decided by the foundry
	For Further advantages of PDN  [[Floor Planning#Power Supply]]
## Electromigration
Flow of electrons can cause collisions with metal atoms which may lead to transport of metal mass this is called electromigration .
This is prevalent in places where is there is current flow only in one direction 
- PDN are prone to electromigration
- Current in PDN needs to be kept within limit defined by the process technology
	-  ensure conductor size is  adequate 
>Note : the metal mass is transported in direction of movement of electrons which is opposite to the of current

## Voltage Drop
### Causes 
- Resistance : between supply voltage origin and load
- Inductance : mainly between package to die interconnection 
- Static and Dynamic Voltage drop
		![[Pasted image 20240826000017.png]]
	- when computational load increases the current pulled will increase which will result in the increase of the voltage drop in the power lines
### Consequences

If there is a voltage Drop in the power lines the delay of other components increase and signal propagation slows down and the maximum operational frequency will be limited .
### Prevention 
To prevent this we can perform voltage drop analysis for both dynamic and static conditions 
and identify the hotspot and fix the IR drop hotspots .
the solution for this is decoupling capacitor  cells . 
For more info [[Floor Planning#De-Coupling capacitors]]
