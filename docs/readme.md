ARCHITECTURE.md
```                                       +-----------------+
                                       |      User       |
                                       +--------+--------+
                                                |
                                                | GUI Interactions
                                                v
+-------------------+     Input Events           +---------------------+
|  AmiUX (Linux)   |---------------------------->| AmigaOS 3.x (Emulated) |
+--------+--------+     System Calls             +---------+----------+
        |                                             |
        | Rendering Instructions/Resources       |
        |                                             |  Calls to OS3uae.library
        v                                             v
+-----------------------+     Interface    +----------------------+
| Interface Manager    | <-------------- |    OS3uae.library    |
| (MUI5/SDL/Vulkan/Wayland)|                +--------+---------+
+---------+----------+                |
                                |  Host Resource Access
                                |  (Files, Network, Hardware)
                                v
                           +-----------+
                           |   Linux   |
                           +-----------+

+----------------------------------------+
|  PiStorm Mode (optional)             |
+----------------------------------------+
        |
        |  Video/Audio Output (Adapted)
        v
+-------------------+
|   Amiga Hardware  |
| (ECS/AGA/Paula)  |
+--------+--------+
        |
        |  Video/Audio Output
        v
     +---------+
     | Monitor |
     +---------+```
content_copy
download
Use code with caution.

Explanation of Components:

User: Interacts with the AmiUX graphical user interface.

AmiUX (Linux): The AmiUX environment running on Linux, which launches the emulator and interface manager.

AmigaOS 3.x (Emulated): The AmigaOS operating system running within the emulator.

Interface Manager (MUI5/SDL/Vulkan/Wayland): Renders the graphical interface using modern Linux APIs.

OS3uae.library: The library that bridges AmigaOS and Linux.

Linux: The host operating system providing resources and modern APIs.

Amiga Hardware (ECS/AGA/Paula) (Optional, PiStorm Mode): The original Amiga hardware, used for video and audio output in PiStorm mode.

Monitor: The display where the AmiUX interface is shown.

This diagram provides a visual representation of the AmiUX architecture. 
