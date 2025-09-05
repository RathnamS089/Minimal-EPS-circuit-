
# Project Results: A CubeSat's Day in Orbit

I'm excited to present the results from my simulation of a CubeSat's Electrical Power Subsystem (EPS). After designing the circuit and overcoming some interesting challenges with the software's limitations, I was able to successfully model the critical charge/discharge cycle that a real satellite experiences on every orbit.

## The Heartbeat of the Battery: Key Waveforms

The waveform below is the key result of this entire project. It captures the "heartbeat" of the battery over a simulated orbit, showing exactly how it responds to sunlight and darkness.


`![EPS Waveforms](./figures/waveforms.png)`

Here’s what each line in the graph represents:
* **Green Line:** The **Battery Voltage ($V_{batt}$)**. As you can see, it holds nice and steady around the 7.4V mark, which is exactly what you'd want for a stable power bus.
* **Yellow Line:** The **Battery Current ($I_{batt}$)**. This is where the main story is told. A negative current means the battery is draining, and a positive current means it's charging back up.
* **White Line (if enabled):** This is our **State of Charge (SOC) Proxy**, giving us a visual sense of the battery's energy level rising and falling.

## Decoding the Model: Element-to-Function Mapping

To understand my circuit diagram, here’s a quick guide that maps each part of my model to its real-world function on an actual CubeSat. This was a key part of the challenge: demonstrating what each block means.

| My Circuit Component | Real-World EPS Function |
| :--- | :--- |
| VCCS controlled by a 4MΩ/980µF RC Timer | The Solar Panel Array and its smart MPPT Controller, which I simulated to turn on after a delay to mimic the satellite emerging from an eclipse. |
| 7.4V Voltage Source + 0.1Ω Series Resistor | The satellite's main power source: a 2-Cell Li-ion Battery Pack. The tiny resistor is crucial for modeling the real-world voltage droop under heavy load. |
| 110Ω Resistor + MOSFET (controlled by 5V DC)| The essential "Always On" loads, like the On-Board Computer (OBC) and housekeeping systems that keep the satellite alive  |
| 27Ω Resistor + MOSFET (controlled by Main Timer)| A "Sun-Only" Payload, like a camera or science instrument, that we only turn on when there's plenty of solar power available . |
| 14Ω Resistor + MOSFET (controlled by Fast Timer)| The "Short Burst" TT&C Radio. This simulates the high-power transmitter firing for a short period to send data back to Earth. |

## The Story in the Data: Explanation of Observed Behavior

The simulation brings the power system's story to life, showing how the CubeSat manages its energy to survive its journey through sunlight and shadow.

My simulation begins with the satellite in Earth's shadow—the **eclipse phase** of its 90-minute orbit. As you can see from the initial part of the waveform, the solar array is offline, providing zero power. At this point, the battery is the sole source of life, steadily powering the essential On-Board Computer. This is clearly shown by the steady, negative battery current ($I_{batt}$), which indicates the battery is **discharging**.

The most exciting moment in the simulation happens around the 60-minute mark. This is the **"sunrise event."** My custom-built RC timer crosses its voltage threshold, activating the VCCS. The power dynamics of the entire satellite instantly change. The battery current immediately flips from negative to positive. This beautiful reversal shows the solar panels not only taking over the job of powering the constant OBC load and the newly activated "Sun-Only" payload, but also sending the excess energy back into the battery. This begins the crucial **charging phase**, preparing the satellite for its next trip through the darkness. The simulation clearly demonstrates this fundamental balancing act of the EPS: surviving on stored energy in the eclipse and harvesting solar energy to power the mission and recharge for the next cycle.
