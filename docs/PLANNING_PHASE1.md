# Phase 1 Planning: Minimal Functional Prototype

## Phase 1 Goal

The main objective of this first development phase is to create a functional prototype that demonstrates AmiUX's ability to communicate information between AmigaOS 3.x (running in the Amiberry emulator) and a native Linux application.  The prototype will focus on basic window replication, showcasing simple bidirectional communication between both systems.

## Prototype Features

The Phase 1 functional prototype will implement the following essential features:

*   **Window Creation:** Replicate AmigaOS window creation on the Linux desktop. Initially, windows will have a basic style, without custom decorations or rounded borders; an exact copy of how they would appear in AmigaOS.
*   **Position and Size:** Control the position and size of replicated windows on Linux, corresponding to the position and size of the windows in AmigaOS.
*   **Window Content:** Display the graphical content of AmigaOS windows in the replicated Linux windows. In this first phase, the content will be displayed by simply copying pixel data from the AmigaOS buffer.
*   **Mouse Clicks:** Capture mouse clicks made in the replicated Linux windows and send the corresponding click coordinates to AmigaOS.  This will allow minimal interaction with the replicated windows.

## Simplified Architecture

The architecture for this phase consists of the following main components:

*   **OS3uae.library (primitive version):** A native AmigaOS library that will intercept calls to specific Intuition functions (`OpenWindowTagList()` and `CloseWindow()`). This library will be responsible for extracting the necessary information about the window (position and size) and sending that information through a communication mechanism to the Amiberry addon.
*   **Amiberry Addon:** An addon for Amiberry that will act as an intermediary between the `OS3uae.library` and the Linux application. This addon will be responsible for receiving window information from AmigaOS and sending it to the Linux application.  This component will also manage sending mouse click coordinates from the Linux application back to AmigaOS.
*   **Linux Application:**  A C++ application that will run the Linux desktop environment. This application will receive window information from the Amiberry addon.  With this information, it will create native Linux windows at the specified positions and sizes and display the graphical content from AmigaOS within those windows.  Additionally, this application will listen for mouse clicks within those windows and send the click coordinates back through the Amiberry addon to the AmigaOS system.  The Linux windows will be transparent and borderless to mimic the replicated content, with native window functions (open, close, minimize, resize, send to back... and mouse actions and right-click) handled separately.


## Technologies to Use

For prototype development, the following technologies are recommended:

*   **AmigaOS Side:**
    *   Language: C (for `OS3uae.library`)
    *   Environment: Amiberry with AmigaOS SDK
*   **Linux Side:**
    *   Language: C++
    *   Graphical Interface: SDL2 (for its simplicity and portability)
    *   Inter-process Communication: Sockets, pipes, or shared memory can be used. Initially, the simplest and easiest to implement option is recommended.

## Tasks for Contributors

To facilitate collaboration, the following specific tasks have been defined:

*   **`OS3uae.library` (primitive) Development:**
    *   Intercept calls to Intuition's `OpenWindowTagList()` and `CloseWindow()` to obtain information about window creation and closure.
    *   Extract the position, size, and content of the window's graphics buffer.
    *   Send the data through the Amiberry addon's communication mechanism to Linux (shared memory, pipes, sockets).

*   **Amiberry Addon Development:**
    *   Manage bidirectional communication with `OS3uae.library` and the Linux application.
    *   Receive window data from `OS3uae.library`.
    *   Send the data to the Linux application.
    *   Receive mouse click coordinates from the Linux application.
    *   Send mouse click coordinates to AmigaOS.

*   **Linux Application Development:**
    *   Create native windows on Linux, with the coordinates and sizes specified by `OS3uae.library`.
    *   Copy and display the graphical content received from AmigaOS in the Linux windows.
    *   Capture mouse click events within the Linux windows.
    *   Send the mouse click coordinates back through the Amiberry addon to AmigaOS.


## Expected Results

At the end of this phase, the following results are expected:

*   A functional prototype that replicates AmigaOS windows on the Linux desktop.
*   A GitHub repository with the source code for:
    *   The primitive `OS3uae.library`.
    *   The Amiberry addon.
    *   The Linux application.
*   A short demonstration video showing the prototype in action.
