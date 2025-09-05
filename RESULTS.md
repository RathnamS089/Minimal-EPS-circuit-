# Project Results: A CubeSat's Day in Orbit

I'm excited to share the results from my simulation of a CubeSat's Electrical Power Subsystem (EPS). After designing the circuit and tackling some challenges with the software's limitations, I successfully modeled the important charge/discharge cycle that a real satellite goes through during each orbit.

## The Heartbeat of the Battery: Key Waveforms

The waveform below is the main result of this project. It captures the "heartbeat" of the battery over a simulated orbit, showing how it responds to sunlight and darkness.

`![EPS Waveforms](./figures/waveforms.png)`

Here’s what each line in the graph represents:
* **Green Line:** The **Battery Voltage ($V_{batt}$)**. It stays steady around the 7.4V mark, which is ideal for a stable power supply.
* **Yellow Line:** The **Battery Current ($I_{batt}$)**. This tells the main story. A negative current means the battery is draining, while a positive current means it is charging.
* **White Line (if enabled):** This is our **State of Charge (SOC) Proxy**, visually indicating how the battery's energy level rises and falls.

## Decoding the Model: Element-to-Function Mapping

To understand my circuit diagram, here’s a quick guide that links each part of my model to its real-world function on an actual CubeSat. This was a key part of the challenge: explaining what each block means.

| My Circuit Component | Real-World EPS Function |
| :--- | :--- |
| VCCS controlled by a 4MΩ/980µF RC Timer | The Solar Panel Array and its smart MPPT Controller, which I simulated to turn on after a delay to mimic the satellite emerging from an eclipse. |
| 7.4V Voltage Source + 0.1Ω Series Resistor | The satellite's main power source: a 2-Cell Li-ion Battery Pack. The small resistor is important for modeling the real-world voltage drop under heavy load. |
| 110Ω Resistor + MOSFET (controlled by 5V DC)| The essential "Always On" loads, like the On-Board Computer (OBC) and housekeeping systems that keep the satellite functioning. |
| 27Ω Resistor + MOSFET (controlled by Main Timer)| A "Sun-Only" Payload, such as a camera or science instrument, that we only activate when there’s enough solar power. |
| 14Ω Resistor + MOSFET (controlled by Fast Timer)| The "Short Burst" TT&C Radio. This simulates the high-power transmitter operating briefly to send data back to Earth. |

## The Story in the Data: Explanation of Observed Behavior

The simulation illustrates the power system's story, showing how the CubeSat manages its energy to navigate through sunlight and shadow.

My simulation starts with the satellite in Earth's shadow—the **eclipse phase** of its 90-minute orbit. From the initial part of the waveform, it's clear that the solar array is offline, providing no power. At this point, the battery is the only source of power, steadily running the essential On-Board Computer. This is shown by the steady, negative battery current ($I_{batt}$), indicating the battery is **discharging**.

The most exciting part of the simulation occurs around the 60-minute mark, known as the **"sunrise event."** My custom-built RC timer crosses its voltage threshold, activating the VCCS. The power dynamics of the entire satellite change instantly. The battery current flips from negative to positive. This shift shows the solar panels not only taking on the OBC load and the newly activated "Sun-Only" payload but also sending excess energy back into the battery. This starts the important **charging phase**, preparing the satellite for its next journey through darkness. The simulation demonstrates this crucial balancing act of the EPS: relying on stored energy during the eclipse and harvesting solar energy to power the mission and recharge for the next cycle.
