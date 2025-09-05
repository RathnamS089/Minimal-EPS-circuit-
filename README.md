
# Minimal CubeSat EPS Circuit Simulation-RathnamS245805102

My Minimal CubeSat EPS Circuit Simulation
This repository holds my submission for the Power Challenge: a circuit model of a minimal Electrical Power Subsystem (EPS) for a CubeSat. My goal with this project was to simulate the charge and discharge cycle of a satellite's battery over a simplified orbit, showing how a real satellite manages its power.

My Approach
The core of the challenge was to model a 90-minute orbit with a 60-minute sun period and a 30-minute eclipse, all within the browser-based tool CircuitJS1.
My initial plan was to use the simulator's standard timed components, like a Piecewise Linear (PWL) source for the solar panels and timed switches for the different loads. However, I quickly ran into a major technical hurdle: the version of the simulator I was using didn't have these components.
Instead of giving up, I decided to build the necessary functions from scratch using fundamental electronic principles. This meant I had to,build my own Analog Timers: I designed and built custom timers using Resistor-Capacitor (RC) circuits. I made a very slow timer (with a 4MΩ resistor and a 980µF capacitor) to simulate the ~60-minute sunrise and a much faster one for the "short burst" load.use MOSFETs as Switches: I used N-Channel MOSFETs to act as efficient switches for the loads. I then used my custom RC timers and a simple DC voltage to control the gates, which let me turn the loads on and off with the specific timing profiles the project required.create a Controlled Solar Source: I used a Voltage-Controlled Current Source (VCCS) to act as the solar array. I connected its control input to my main "sunrise" timer, allowing it to turn on and provide power after the simulated eclipse.

While this approach was definitely more complex, it was a great challenge that resulted in a successful model. It also demonstrates a deeper understanding of how these systems can be built from the ground up.

Key Assumptions
The battery is modeled as an ideal 7.4V source with a 0.1Ω series resistor to show how the voltage might realistically drop under heavy use.
I assumed the solar panels provide about 6W of power when in the sun.
I modeled three distinct loads with power estimates based on their function:
OBC ("Always On"): ~0.5W (110Ω resistor)
Payload ("Sun-Only"): ~2W (27Ω resistor)
TT&C ("Short Burst"): ~4W (14Ω resistor)
I included a single 0.2Ω series resistor to represent overall power conversion and wiring losses in the system.

Tools I Used
Simulation: CircuitJS1 (Browser-based SPICE tool)
Version Control: Git & GitHub

Instructions to Run My Simulation
1)Navigate to the src/ directory and open the circuit text file.
2)Copy the entire block of text.
3)Go to the CircuitJS1 website.
4)Click File > Import From Text....
5)Paste the text into the window and click "OK". The complete circuit should load.
6)To see the results and my analysis, please check out the RESULTS.md file.
