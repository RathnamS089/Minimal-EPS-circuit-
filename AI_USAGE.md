
AI_USAGE.md (Humanized Version)
My Project Report & AI Usage
This document covers how I used AI as a tool to complete the Minimal EPS Circuit Challenge. I've detailed the kinds of questions I asked, how I used the AI's help, and a summary of the technical challenges we worked through together.

AI Tool I Used
For this project, my main partner was Google's Gemini, which I used through its web interface.

How I Worked With the AI
My process wasn't about asking one single question. Instead, it was a long conversation, like working with a remote partner. My prompts and questions generally fell into these categories:

Big Picture Planning: I started by asking for a high-level strategy to make sure I was on the right track ("How should my approach be?", "Can you help me tailor my README?").

Building the Circuit, Step-by-Step: I asked the AI to guide me through the construction process, one piece at a time ("Now how do I visualize the circuit?", "How do I create the power buses?").

"What Did I Do Wrong?" - Live Debugging: A lot of our time was spent debugging. I would build a section of the circuit, get an error like "bad connections" or "singular matrix," and upload a screenshot with a simple "help" or "is this right?".

"Why Does It Do That?" - Understanding Concepts: I asked the AI to explain specific concepts, like the difference between a PWL source and a VCCS, or what a MOSFET's threshold voltage meant for my circuit.

Getting Unstuck with Git: When I hit roadblocks with Git and GitHub, I asked for specific commands to fix errors with authentication and pushing my code.

Writing the Reports: I prompted the AI for templates for the final report files, which I then filled in and customized.

How I Used the AI's Help
I used the AI as an interactive guide and a debugging tool. My workflow was a loop:

I would follow the AI's step-by-step instructions to build a part of the model.

If I hit an error, I'd send a screenshot. The AI's analysis would help me find the exact wire I had misplaced or the component value I had entered incorrectly, and I would then manually fix it.

When things got really stuck, I had the AI generate a complete, error-free code block that I could import into the simulator to get a clean start on the next section.

Finally, I used the markdown templates it provided as a starting point for my reports, filling them in with my own data and observations.

The Story of Our Biggest Technical Challenge
The main challenge we faced was that my version of CircuitJS1 was missing the key components needed for an easy solution. The AI initially suggested using standard PWL sources and timed switches. When I tried to find them, I realized they weren't there.

This is where our collaboration was most important. I sent screenshots to the AI proving the components were missing, which corrected its initial assumptions. From there, we had to pivot. The AI proposed a completely new strategy: building the timed events from scratch using basic electronic principles. Together, we designed and calculated the values for analog RC timers to generate the control signals and used MOSFETs as switches. This entire, complex workaround was something we could only figure out by combining my real-world feedback with the AI's theoretical knowledge.

A Quick Critique of the AI
Its Strength: The AI's best feature was its ability to instantly change its entire strategy when I provided new information. It was great at giving clear, step-by-step instructions and was incredibly helpful for spotting tiny wiring errors in my screenshots and for navigating the confusing world of Git commands.

Its Weakness: The AI's main flaw was that it couldn't see my screen or know my software environment. Its initial advice was based on an ideal version of the tool, which led to some early frustration and rework. It really highlighted that the AI is a powerful assistant, but it needs a human user to provide real-world context and correct its course.

Other Resources I Used
Throughout the project, I used these sites to double-check the concepts the AI was explaining.

CircuitJS1 Documentation: Falstad Circuit Simulator - For getting familiar with the simulator's interface.

RC Circuits: All About Circuits - RC Circuit Analysis - To better understand the theory behind the analog timers I had to build.

MOSFETs as Switches: SparkFun - Transistors - For a practical guide on how MOSFETs work.

Git and GitHub: GitHub Skills - To help make sense of the Git workflow.
