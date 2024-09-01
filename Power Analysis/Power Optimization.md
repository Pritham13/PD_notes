Refer  [[Power  Dissipation#Total power Dissipation]] for Power dissipation formula
# Dynamic Voltage Frequency Scaling
- changes supply voltage and frequency dynamically to reduce power dissipation
This method is used in MicroProcessors 
Here is a summary of the provided content that you can use for your Obsidian notes:
### Key Concepts:
- **Dynamic Power Management:** 
  - **Objective:** Exploit variations in workload to save energy.
  - **Full Speed Utilization:** Only a few tasks or small time periods require the processor to run at full speed.
  - **Energy Saving:** For the remaining time, the processor can meet deadlines at lower speeds, significantly reducing energy consumption.

###  Example:
- **Task Parameters:**
  - Original Task Time: 10 ms
  - Original Frequency: 1.2 GHz
  - Original Voltage: 1.2 V

- **Reducing Clock Frequency and Voltage:**
  - New Frequency: 600 MHz (half of the original)
  - New Voltage: 0.6 V (half of the original)
  - New Task Time: 20 ms (double the original time)

- **Power and Energy Impact:**
  - **Switching Power Dissipation:** Reduced by 1/8 due to the relationship $$P_{\text{tot}} \propto V_{\text{DD}}^2 f_{\text{clk}} $$
  - **Energy Consumption:** Reduced by 1/4.

### Observations:
- Reducing the clock frequency and supply voltage significantly reduces both power dissipation and energy consumption while still completing the task within a longer but acceptable timeframe.

# Power gating
In this method we switch off power to a block this helps to reduce both static and dynamic power loss .

## Circuit elements
![[Pasted image 20240901122433.png|320]]
### Switch Cell
this is a HIGH Vt cell to reduce the Leakage current and sleep signal is used to give access to Vdd 
### Retention Cell
used to store state during sleep state
![[Pasted image 20240901122842.png|200]]
### Isolation Cell
used to make sure to avoid indeterministic state of the output driver during sleep state


# Clock Gating 
Used to reduce activity to reduce Power dissipation
Cuts off the clock to the Flip Flops when there is no data to capture , this saves power due to the internal power losses of the Flip Flops when the clocks change
![[Pasted image 20240901123554.png]]

If the above circuit is used for implementation of clock gating it will lead to a glitch 
![[Pasted image 20240901123642.png]]

this can cause timing violations that is why Integrated clock gater (ICG) is used
![[Pasted image 20240901123858.png]]

![[Pasted image 20240901123921.png]]

the latch makes sure the data is sampled properly

# Resizing
Reduce cells to reduce power dissipation we can use smaller cells in non critical paths and the load capacitances decreases resulting in lower power dissipation