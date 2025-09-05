
**AI Usage Report and Project Methodology

This document explains how I used AI tools to complete the Minimal EPS Circuit Challenge, following the submission guidelines. It includes the types of prompts I used, how I adjusted the AI's output, and a technical summary of the challenges we faced together.

AI Tool I Used

The main AI tool I used for this project was Google's Gemini, which I accessed through its web interface.

Prompts and Query Themes

My interaction with the AI was a continuous dialogue rather than a set of isolated questions. My prompts targeted several key areas throughout the project:

Initial Strategy and Scoping: I began with high-level prompts to break down the problem statement and create a clear plan, asking things like "What approach should I take for this problem?" and "Go through the files and update my readme.md."

Step-by-Step Implementation: The heart of the circuit construction was guided by sequential prompts, such as "How do I visualize the circuit?" or "How do I create power and ground buses?"

Live Debugging: A significant part of our interaction involved me uploading screenshots of my circuit and seeking help with specific simulator errors. My prompts were often simple and straightforward, like "Help me," "Is this right?" "Fix the bad connections," "Singular matrix," or "Why is my gate not connected?"

Conceptual Clarification: I asked the AI to clarify specific electronic concepts related to my circuit, such as "What is the threshold voltage for minimum power?" and "What's the difference between the PWL function and a normal VCCS source?"

Git/GitHub Workflow: I requested specific command-line instructions to set up my repository and fix a series of authentication and push errors.

Documentation: I prompted the AI to create and refine content for the final report files, including the README.md and RESULTS.md.

How AI Outputs Were Adapted

I used the AI's output as a real-time guide and a debugging partner.

Instructional Guidance: I followed the AI's step-by-step instructions to build the circuit from scratch to the final, complex model.

Troubleshooting: I leveraged the AI's analysis of my screenshots to pinpoint wiring errors, like floating nodes or short circuits, which I then fixed in the simulator.

Code Implementation: When wiring became too complex or error-prone, I had the AI generate a clear, error-free code block that I imported directly into CircuitJS1 as a reliable starting point.

Documentation: I used the markdown templates created by the AI as a base for my final report, customizing them with my specific data and narrative.

Technical Challenges and Collaborative Debugging

The central technical challenge of this project was a significant gap between the ideal components suggested in the project brief and those available in my version of CircuitJS1.

Initially, the AI recommended using standard PWL sources and timed switches, which was the most straightforward solution. However, through my own trial and error, I found that these components were not available. I communicated this to the AI by sharing screenshots of the simulator's menus. This feedback was critical.

This situation forced us to switch to a more complex solution. The AI proposed a new strategy based on fundamental electronic principles: building custom analog RC timers to generate control signals and using MOSFETs as electronic switches. The AI provided the theoretical background and initial calculations for the timer components, which I then implemented. This back-and-forth process, where I supplied real-world tool constraints and the AI contributed theory and calculations, was key to completing the functional circuit.

Critique of AI Output

Strengths: The AI's main strength was its ability to quickly adapt to a new, complex strategy after I provided feedback. It was great at giving structured, step-by-step instructions for both circuit construction and Git commands. It was also highly effective as a remote debugger, spotting subtle wiring errors in my screenshots.

Weaknesses: The AI's primary limitation was its initial lack of awareness of my specific software environment. Its first suggestions, while theoretically correct, were not applicable and led to some initial rework. This shows that for engineering tasks, the AI is a valuable tool, but it needs a human user to provide real-world context and correct its assumptions.

Non-AI Sources Used

Throughout the project, I supported the AI's guidance with my own research to better understand the underlying electronic concepts.

CircuitJS1 Documentation: Falstad Circuit Simulator - Used to learn about the basic interface and component behaviors.

RC Circuits: All About Circuits - RC Circuit Analysis - Used to verify the principles behind the analog timers we designed.

MOSFETs as Switches: SparkFun - Transistors - Used for a practical overview of how MOSFETs function as switches.

Git and GitHub: GitHub Skills - Used to better understand the Git workflow and commands suggested by the AI.

