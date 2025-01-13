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
+---------+----------+          |
                                |  Host Resource Access
                                |  (Files, Network, Hardware)
                                v
                           +-----------+
                           |   Linux   |
                           +-----------+
-------------------------------------------------------------------------------------------
Pistorm can recieve rendered screen outputs from Amiberry from the ARM side extension board
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
     +---------+
```



Explanation of Components:
(Before yo need to install AmiUX app in Linux, Amiberry/FS-UAE and AmiUX.OS3 in the AmigaEmulator)
Pistorm is open to any ARM sbc like Raspberry, not only any concrete models
User: Interacts with the AmiUX graphical user interface.

AmiUX (Linux): The AmiUX environment running on Linux, which launches the emulator and interface manager.

AmigaOS 3.x (Emulated): The AmigaOS operating system running within the emulator.

Interface Manager (MUI5/SDL/Vulkan/Wayland): Renders the graphical interface using modern Linux APIs.

OS3uae.library: The library that bridges AmigaOS and Linux.

Linux: The host operating system providing resources and modern APIs.

Amiga Hardware (ECS/AGA/Paula) (Optional, PiStorm Mode): The original Amiga hardware, used for video and audio output in PiStorm mode.

Monitor: The display where the AmiUX interface is shown.

This diagram provides a visual representation of the AmiUX architecture. 

## Graphical User Interface

AmiUX will utilize MUI5 to provide a modern and responsive user interface while retaining the classic AmigaOS look and feel.  We plan to leverage the capabilities of modern Linux graphics libraries (SDL/Vulkan/Wayland) to enhance the visual experience with features like transparencies, rounded corners, and shadows.  The OS3uae.library will intercept MUI calls and transmit the necessary information to a dedicated Linux application responsible for rendering the GUI.

**References:**

* [MUI Dev Wiki](https://github.com/amiga-mui/muidev/wiki)
* [Zune (AROS Widget Toolkit)](https://en.wikipedia.org/wiki/Zune_(widget_toolkit))
* [Ambient (MorphOS Desktop Environment)](https://en.everybodywiki.com/Ambient_(desktop_environment))
* [AmigaOS.MUI.cpp.wrapper](https://github.com/tdolphin-org/AmigaOS.MUI.cpp.wrapper)
