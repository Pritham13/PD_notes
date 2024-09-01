# Interconnect Layers

## Wiring Layers
- Metal layers making interconnections
- Parallel to wafer surface

## Via Layers
- Connects wiring layers
- Perpendicular to wafer layers
- Cannot change the thickness of the interconnection
- They have uniform thickness

## Dielectric Separation
- Metal layers are separated by dielectrics
  - Generally SiO₂
    - ![image for reference](Imgs/interconnect_layers.png)
  - Low K materials can be used
    - Height for the wiring layers is fixed for a single layer
    - Two layers may have different wire heights
      - Example: Layer 1 has height \( h_1 \) for all wires in Layer 1 and Layer 2 has height \( h_2 \) for all wires in Layer 2
  - Generally, metal height increases from the bottom to the top of an IC

# Interconnect Parasitics

## General Points
- Wires have some resistance and capacitance
- At high frequencies, the resistance of interconnects tends to increase
- **Skin Effect**
  - Current tends to flow on the conductor's surface
  - Effect is more pronounced in wider and thicker top metal layers
  - Affects clock lines that operate at high frequencies

## Capacitances
- Caused by the dielectrics present
- Electric potential of the interconnect layers during circuit operation
- Electric field and the stored charges in the surrounding dielectric material change

### Factors Influencing Capacitance
- Depends on geometry, environment, and properties of the surrounding dielectrics

### Components of Capacitance
1. **Overlap Capacitance**
   - Due to overlap between two conductors
2. **Lateral Capacitance**
   - Parallel edges of non-overlapping conductors in the same plane
3. **Fringe Capacitance**
   - Between two conductors in different planes due to the electric fields originating from sidewalls