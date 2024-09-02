P -> Process
V -> Voltage
T -> temperature
![[Pasted image 20240901202310.png]]

the term corner refers to an imaginary four corner box . Each corners i.e extreme limits specifies some sort of performance boundary condition for the design under consideration. Process corners represent the extremes of silicon fabrication process parameter variations for a fabricated circuit. Mixed name corners like fast-slow and slow-fast and are refereed to as skew corners.. When the parameters of a transistor are set in such a way that the transistor operates fast then it is known as a fast corner. A single circuit will perform differently in each of the process corners. A single process corner may show slightly different performance for a given circuit from one wafer-lot to another wafer-lot. The testing of the circuit performance at each corner is termed as "characterization". This word is used frequently with Standard Cells. Two-letter designation (TT,FF,SS etc) points  to N-Channel MOSFET (NMOS) corner and P-Channel (PMOS) corner for a  CMOS structure respectively.

## FEOL
Common FEOL corners are FF,SS,FS,SF,TT

## BEOL corners 
C -Worst, C Best, Cc Worst, RC Best, Rc Worst
## Basic nomenclature
![[Pasted image 20240901202941.png]]
 
• NMOS can be slow, typical, fast (S, T, F).
• PMOS can be slow, typical, fast (S, T, F).
• Temperature can be hot, typical, cold (S, T, F).
• Vdd can be high, typical, low (F, T, S).

### Example 

Process corners are used to describe different combinations of NMOS and PMOS characteristics, temperature, and supply voltage. The elaborate process corner labels help in understanding the variations in a design's performance. Here are some example labels and their detailed descriptions:

- **TTTT**: Typical NMOS, Typical PMOS, Room Temperature, Nominal Supply
- **SSSS**: Slow NMOS, Slow PMOS, Hot Temperature, Low Supply
- **FSSS**: Fast NMOS, Slow PMOS, Hot Temperature, Low Supply

### Elaboration and Nomenclature Mapping

Using the basic nomenclature, we can construct more elaborate process corner labels. The labels are generally constructed based on the following parameters:

- **NMOS**: Fast (F), Typical (T), Slow (S)
- **PMOS**: Fast (F), Typical (T), Slow (S)
- **Temperature**: Room (R), Hot (H)
- **Supply Voltage**: Nominal (N), Low (L)

### Variations and Combinations

The variation of specific Figures of Merit (FOM) of any design under consideration are observed across all permutations and combinations of:

- **NMOS**
- **PMOS**
- **Temperature (T)**
- **Supply Voltage (V)**

The permutations and combinations become more complex when considering BEOL (Back End Of Line) RC corners.

### BEOL (RC) Corners

When BEOL RC corners are included, the permutations and combinations expand further, adding complexity to the analysis of design performance.
