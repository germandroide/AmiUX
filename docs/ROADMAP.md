# AmiUX Roadmap

This document outlines the planned development stages and goals for the AmiUX project.

## Phase 1: Basic Functional Prototype (Proof of Concept)

**Goal:** Demonstrate the core functionality of AmiUX by creating a minimal working prototype.  This involves establishing bidirectional communication between AmigaOS 3.x (running in Amiberry) and a Linux application, replicating AmigaOS windows within the Linux desktop.

**Milestones:**

* **Primitive OS3uae.library:**  Develop a basic version of the OS3uae.library that intercepts window creation/update calls and transmits basic window information (position, size, and pixel data) to the Linux application.
* **Amiberry Addon:**  Create an addon for Amiberry that facilitates communication with the OS3uae.library and handles data transfer between the emulated environment and Linux.
* **Basic Linux Application:**  Develop a Linux application (using SDL/Vulkan/Wayland) that receives window data from Amiberry and renders replica AmigaOS windows on the Linux desktop.  Initial focus will be on accurately replicating the visual output. Basic input events (mouse clicks, keyboard input) should be forwarded back to Amiberry.

**Estimated Timeframe:** weeks


## Phase 2: Enhanced Library and GUI Integration

**Goal:**  Expand the functionality of the OS3uae.library and integrate advanced GUI features.  This involves adding support for more system functions, implementing modern GUI elements using MUI5, and introducing enhanced visual effects.

**Milestones:**

* **Extended OS3uae.library:** Add support for file system access, network communication, and other essential system functions.  Implement mechanisms for passing more complex data between AmigaOS and Linux.
* **MUI5 Integration:**  Design and implement AmigaOS window decorations and GUI elements using MUI5, rendered within the Linux application.
* **Enhanced Visual Effects:**  Introduce modern GUI effects like rounded window borders, transparencies, shadows, and animations, leveraging the capabilities of the Linux graphics stack.
* **Improved Input Handling:**  Refine input handling to support more complex mouse events and keyboard shortcuts.

**Estimated Timeframe:** weeks


## Phase 3: PiStorm Integration and Advanced Features

**Goal:**  Develop the PiStorm implementation and introduce advanced features like hardware acceleration, improved performance, and expanded compatibility.

**Milestones:**

* **PiStorm Implementation:**  Develop the necessary hardware and software components to run AmiUX on classic Amiga hardware using a PiStorm-compatible setup.  This involves adapting the OS3uae.library and the Linux application to interact with the original Amiga hardware.
* **Hardware Acceleration:**  Explore and implement hardware acceleration for graphics and other computationally intensive tasks, leveraging the capabilities of the ARM processor and the Linux graphics stack.
* **Performance Optimization:**  Optimize the performance of AmiUX across all supported platforms, focusing on minimizing emulation overhead and maximizing resource utilization.
* **Expanded Compatibility:**  Extend compatibility to support a wider range of AmigaOS 3.x software and hardware configurations.

**Estimated Timeframe:** months



## Long-Term Goals:

* **Community Growth:** Foster a vibrant and active community around AmiUX, encouraging contributions and collaboration.
* **Software Development:** Encourage the development of new software and tools for AmiUX, leveraging the combined power of AmigaOS and Linux.
* **Cross-Platform Support:**  Explore the possibility of porting AmiUX to other platforms beyond Linux.


This roadmap is a living document and will be updated as the project progresses.  We welcome feedback and suggestions from the community.
