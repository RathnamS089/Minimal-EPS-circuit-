
# Minimal CubeSat EPS Circuit Simulation-RathnamS245805102

This repository contains a circuit model of a minimal Electrical Power Subsystem (EPS) for a CubeSat, developed for the Power Challenge. The model simulates the charge and discharge behavior of the satellite's battery over a simplified orbital period. This demonstrates the main functions of a satellite power system.

Approach
The primary goal was to model a 90-minute orbit, which includes a 60-minute sun period and a 30-minute eclipse, using the browser-based tool CircuitJS1.

The initial plan was to use the simulator's built-in timed components, such as a Piecewise Linear (PWL) source for the solar array and timed switches for the loads. However, it was found that the available version of the simulator did not include these specific components.

To address this significant technical challenge, a new method was developed based on basic electronic principles:
1. Analog Timers: Custom, slow-acting analog timers were designed and built using Resistor-Capacitor (RC) circuits. A very slow timer (4MΩ resistor, 980µF capacitor) was created to simulate the ~60-minute sunrise event. A second, faster RC timer was built to simulate the "short burst" load.
2. MOSFET Switches: N-Channel MOSFETs served as efficient electronic switches. The gates of these MOSFETs were controlled by the custom RC timers or by a constant DC voltage. This allowed the loads to be turned on and off with the necessary timing profiles.
3. Controlled Solar Source: A Voltage-Controlled Current Source (VCCS) was used to model the solar array as a supply. Its output was controlled by the main "sunrise" RC timer, causing it to activate and provide power after the simulated eclipse period.

This workaround, while more complex, successfully models the needed charge/discharge behavior and shows a deeper understanding of how timed events can be created from basic electronic components.

 Assumptions

* The battery is modeled as an ideal 7.4V source in series with a 0.1Ω resistor to simulate internal resistance and voltage drop.
* Available solar power in the sun is about 6W at the EPS input.
* The three distinct loads are modeled with the following approximate power consumptions:
    * OBC ("Always On"): ~0.5W (110Ω resistor)
    * Payload ("Sun-Only"): ~2W (27Ω resistor)
    * TT&C ("Short Burst"): ~4W (14Ω resistor)
* Overall EPS conversion and wiring losses are represented by a single 0.2Ω series resistor.

 Tools Used

* Simulation: CircuitJS1 (Browser-based SPICE tool) 
* Version Control:** Git & GitHub 

 Instructions to Run

1.  Navigate to the `src/` directory and open the circuit text file.
2.  Copy the entire contents of the file.
3.  Go to the [CircuitJS1 website](https://www.falstad.com/circuit/circuitjs.html).
4.  Click `File` > `Import From Text...`.
5.  Paste the copied text into the window and click "OK". The complete circuit will load.
6.  To run the simulation and see the required waveforms, follow the analysis steps outlined in the `RESULTS.md` file.
