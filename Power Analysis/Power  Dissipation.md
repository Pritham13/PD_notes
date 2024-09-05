
## Contents

1. [[#Dynamic Power dissipation]]
    - [[#Switching power]]
    - [[#Switching power]]
2. [[#Static power dissipation]]
3. [[#Total power Dissipation]]

### Dynamic Power dissipation
power dissipation when computation occurs
#### Switching power
![](Pasted%20image%2020240901114758.png)
taking the above circuit as example , if the input at the inverter makes a transition the same is reflected at the output . The inverter has to drive all the gates that are connected to it , and the gates have some input capacitance and the inverter itself has some output capacitance during the transition the inverter has to charge /discharge the capacitances of the gates which leads to some power dissipation this is called as switching power dissipation .

![250](Pasted%20image%2020240901115626.png)
#### Short circuit power
![300](Pasted%20image%2020240901115802.png)
in the above circuit if the input transition is too slow both the PMOS and NMOS will be turned on together and there will be a short circuit momentarily and this will cause a loss in power
### Static power dissipation
power dissipation that occurs when the circuit is on but not performing active computation
![](Pasted%20image%2020240901115936.png)

consider the above figure note that when the input is 0 there is leakage current through the NMOS and the current flows through the NMOS and there is power dissipation
**reasons for Static power dissipation are**
- Subthreshold current
- Gate leakage current
- Junction Leakage 

## Total power Dissipation
The total power dissipation in a digital circuit is given by the equation:

$$
P_{tot} = C_L V_{DD}^2 \alpha f_{clk} + V_{DD} I_{SC} + V_{DD} I_{leak}
$$

where:

- $V_{DD}$ = supply voltage
- $C_L$ = load capacitance
- $f_{clk}$ = frequency of the clock in the circuit
- $\alpha$ = activity factor of the signal
- $I_{SC}$ = short-circuit current
- $I_{leak}$ = leakage current

The equation includes:

1. **Switching Power Dissipation**: $$C_L V_{DD}^2 \alpha f_{clk}$$  
   - This term accounts for the dynamic power consumption due to charging and discharging of the capacitive load during switching.

2. **Short-Circuit Power Dissipation**: $$V_{DD} I_{SC} $$ 
   - This term accounts for the power loss due to the short-circuit current that flows directly from $$V_{DD} $$to ground during the switching transition when both PMOS and NMOS transistors are momentarily on.

3. **Static Power Dissipation**: $$ V_{DD} I_{leak}$$  
   - This term represents the power dissipation due to leakage currents in the circuit when transistors are off.
