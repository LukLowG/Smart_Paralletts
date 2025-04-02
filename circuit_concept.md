# Electronics
This file shows the basic thoughts for the Wiring and Arduino setup

## Overview
Each half-bridge load cell (like the one from your AliExpress link) has:

- 3 wires: Red (Excitation+), Black (Excitation−), and White (Signal)
- Inside: 2 strain gauges connected as half a Wheatstone bridge

To make a full bridge, you wire 4 of these load cells together.

Full-Bridge Wiring (4 Half-Bridge Load Cells → 1 Full Wheatstone Bridge)
- Excitation+ (E+): Red wires of two opposite cells (top-left and bottom-right)
- Excitation− (E−): Black wires of the other two opposite cells (top-right and bottom-left)
- Signal+ (S+): White wire from one E+ cell
- Signal− (S−): White wire from one E− cell

This forms the Wheatstone bridge and connects to one HX711 module.
Te HX711 module is necessary to amplify the small signal fluctuations and make them readble for the arduino.

The wiring will be adpoted from this scheme: https://circuitjournal.com/50kg-load-cells-with-HX711 \
![Bildschirmfoto vom 2025-04-02 21-52-20](https://github.com/user-attachments/assets/989b4048-e165-4443-a974-f595ca65845e)

Each Cell is rated for 50 kg and can safely handle 120% (60 kg). \
With 4 cells per parallett and 8 in total this sums up to 200 kg per parallet and 400 kg in total. \
The accuracy is ±0.05% from the maximum value, i.e. ±25g \
This is considered small enough for a human with bodyweight 75 kg (0,03%).
