# About this Repo
This repo does contain different preconfigured `Marlin 2.0 Stable (2.0.9.3)` fimrware versions for the TwoTrees Sapphire Plus 3D-Printer. This is a non-offical project. There are several different revisions of this printer out there, so I did multiple branches for different printer configurations. The Sapphire Pro (New Name: SP-3) and newer revisions of the printer (e.g. SP-5) are not supported yet, since tested information is missing for me. If you've got a Printer: Please feel free to do a pull-request, when your firmware is working.

<img align="center" width=1200 src="/readMeImgs/Interface.jpg" />

## Precompiled firmwares
Precompiled fimrwares can be found on the [Releases pages](https://github.com/RolfZuckowskiUltras/TwoTrees_Sapphire_RawMarlin/releases). In future, I'm probably not going to share compiled firmwares for the BL-Touch-Version, since those require further tuning after the installation. So you're betther off to fork of your own repo with your finetuned values.

## Supported Machines
There are 3 major known versions of the Sapphire Plus. The third gen seems to be also known as SP-5.
- 1st-Gen: Belt-Synced-Z-Drive, just one Endstop.
- 2nd-Gen: Dual independend driven Z-Axis.
- 3rd-Gen: Belt-Synced Z-Drive but two Endstops, TMC2225 Drivers, SD-Card on the Left.

_If you've got a running SP-5 / 3rd-Gen: Please feel free to make a Pull-Request with your tested configuration._

All machines are using the MKS Robin Nano V1.X, although the v3 is available as of now. In case of a silent upgrade by TwoTrees or yourself, you have to modify the configuration according to the [repository of MKS](https://github.com/makerbase-mks/Mks-Robin-Nano-Marlin2.0-Firmware#more-information-about-the-robin-nano-v2x).

### Belt-Sync vs Dual-Z
The most easiest way to make clear what version you have, is to switch off the printer and turn one of both Z-Axis-Spindles by hand.
- In case the other side is also turing, you've got a Belt-Synced-Model (BS)
- In case the other side does not turn and you have two Z-Endtstops on your machine, you've got a DualZ-Model (DD)

# Sapphire Plus-Repos
Branch Name |Z-Axis Type|Driver Z-Axis|Driver Else|Hotend|BL-Touch|Firmware Tested?
--------|---|---|---|---|---|-------
[`Modified_Sapphire_Plus_DualZ_Hemera_BLT`](https://github.com/RolfZuckowskiUltras/TwoTrees_Sapphire_RawMarlin/tree/Modified_Sapphire_Plus_DualZ_Hemera_BLT) |DD|TMC2208|TMC2209|E3D Hemera|Yes|✓
[`Stock_Sapphire_Plus_DualZ`](https://github.com/RolfZuckowskiUltras/TwoTrees_Sapphire_RawMarlin/tree/Stock_Sapphire_Plus_DualZ)               |DD|A4988|TMC2208|Stock|No|✗, but Specs known working
[`Stock_Sapphire_Plus_DualZ_Hemera`](https://github.com/RolfZuckowskiUltras/TwoTrees_Sapphire_RawMarlin/tree/Stock_Sapphire_Plus_DualZ_Hemera)        |DD|A4988|TMC2208|E3D Hemera|no|✗, but Specs known working
[`Stock_Sapphire_Plus_DualZ_Hemera_BLT`](https://github.com/RolfZuckowskiUltras/TwoTrees_Sapphire_RawMarlin/tree/Stock_Sapphire_Plus_DualZ_Hemera_BLT)    |DD|A4988|TMC2208|E3D Hemera|Yes|✗, but Specs known working
[`Stock_Sapphire_Plus_SyncedZ`](https://github.com/RolfZuckowskiUltras/TwoTrees_Sapphire_RawMarlin/tree/Stock_Sapphire_Plus_SyncedZ)             |BS|A4988|TMC2208|Stock|No|✗, but Specs known working
[`Stock_Sapphire_Plus_SyncedZ_Hemera`](https://github.com/RolfZuckowskiUltras/TwoTrees_Sapphire_RawMarlin/tree/Stock_Sapphire_Plus_SyncedZ_Hemera)      |BS|A4988|TMC2208|E3D Hemera|No|✗, but Specs known working
[`Stock_Sapphire_Plus_SyncedZ_Hemera_BLT`](https://github.com/RolfZuckowskiUltras/TwoTrees_Sapphire_RawMarlin/tree/Stock_Sapphire_Plus_SyncedZ_Hemera_BLT)  |BS|A4988|TMC2208|E3D Hemera|Yes|✗, but Specs known working

# Upgrading your Machine
## Better Extruder/E3D-Hemera
When upgrading the Extruder/Hotend, I would recommed just getting a E3D Hemera. Works fine and seems to be the most cost-efficient part without pirated design 😃.
There are two mounts for different Cooling-Fan models. [This one is for a EBM-Pabst-Fan](https://www.thingiverse.com/thing:4578322). [This one for a generic one](https://www.thingiverse.com/thing:4435761). Both are verified working.

## Automatic Bed-Leveling with BL-Touch or 3D-Touch sensors.
This one is a little bit more complicated, since the MKS Manual asks you to use the Z-Max plug on the Mainboad, which is obviously used for the second Endstop at the Dual-Z-Models. No Problem! I've got you. I'm going to show you, how to connect the BL-Touch, but the finetuning has to be done by yourself. But there are plenty good YouTube tutorial out there, so go for that. My configuration was done with the Hemera-Mount, you can find above, if you may want to take this as orientation.

<img align="center" width=600 src="/readMeImgs/blt_action.gif" />

### Connecting the BL-Touch
We're using Plug for the second filament sensor, which is very unlikely to be used. This Pin is internally called `PE6`. You can find internal name of the pins in the [pinout of the MKS Robin Nano V1.X](https://github.com/RolfZuckowskiUltras/TwoTrees_Sapphire_RawMarlin/blob/Stock_Sapphire_Plus_DualZ_Hemera_BLT/readMeImgs/MKS_Robin_Nano_Pin.png). Just connect it, like in the picture below and you're fine.

<img align="center" width=800 src="/readMeImgs/BLT-Wiring.PNG" />


# Some other Information about Marlin 2.0, you're probably not interrested in...

Marlin 2.0 takes this popular RepRap firmware to the next level by adding support for much faster 32-bit and ARM-based boards while improving support for 8-bit AVR boards. Read about Marlin's decision to use a "Hardware Abstraction Layer" below.

Download earlier versions of Marlin on the [Releases page](https://github.com/MarlinFirmware/Marlin/releases).

## Example Configurations

Before building Marlin you'll need to configure it for your specific hardware. Your vendor should have already provided source code with configurations for the installed firmware, but if you ever decide to upgrade you'll need updated configuration files. Marlin users have contributed dozens of tested example configurations to get you started. Visit the [MarlinFirmware/Configurations](https://github.com/MarlinFirmware/Configurations) repository to find the right configuration for your hardware.

## Building Marlin 2.0

To build Marlin 2.0 you'll need [Arduino IDE 1.8.8 or newer](https://www.arduino.cc/en/main/software) or [PlatformIO](http://docs.platformio.org/en/latest/ide.html#platformio-ide). Detailed build and install instructions are posted at:

  - [Installing Marlin (Arduino)](http://marlinfw.org/docs/basics/install_arduino.html)
  - [Installing Marlin (VSCode)](http://marlinfw.org/docs/basics/install_platformio_vscode.html).

## Marlin Support

The Issue Queue is reserved for Bug Reports and Feature Requests. To get help with configuration and troubleshooting, please use the following resources:

- [Marlin Documentation](http://marlinfw.org) - Official Marlin documentation
- [Marlin Discord](https://discord.gg/n5NJ59y) - Discuss issues with Marlin users and developers
- Facebook Group ["Marlin Firmware"](https://www.facebook.com/groups/1049718498464482/)
- RepRap.org [Marlin Forum](http://forums.reprap.org/list.php?415)
- Facebook Group ["Marlin Firmware for 3D Printers"](https://www.facebook.com/groups/3Dtechtalk/)
- [Marlin Configuration](https://www.youtube.com/results?search_query=marlin+configuration) on YouTube

## Contributors

Marlin is constantly improving thanks to a huge number of contributors from all over the world bringing their specialties and talents. Huge thanks are due to [all the contributors](https://github.com/MarlinFirmware/Marlin/graphs/contributors) who regularly patch up bugs, help direct traffic, and basically keep Marlin from falling apart. Marlin's continued existence would not be possible without them.

## Administration

Regular users can open and close their own issues, but only the administrators can do project-related things like add labels, merge changes, set milestones, and kick trolls. The current Marlin admin team consists of:

 - Scott Lahteine [[@thinkyhead](https://github.com/thinkyhead)] - USA - Project Maintainer &nbsp; [![Donate](https://api.flattr.com/button/flattr-badge-large.png)](http://www.thinkyhead.com/donate-to-marlin)
 - Roxanne Neufeld [[@Roxy-3D](https://github.com/Roxy-3D)] - USA
 - Keith Bennett [[@thisiskeithb](https://github.com/thisiskeithb)] - USA
 - Victor Oliveira [[@rhapsodyv](https://github.com/rhapsodyv)] - Brazil
 - Chris Pepper [[@p3p](https://github.com/p3p)] - UK
 - Jason Smith [[@sjasonsmith](https://github.com/sjasonsmith)] - USA
 - Luu Lac [[@shitcreek](https://github.com/shitcreek)] - USA
 - Bob Kuhn [[@Bob-the-Kuhn](https://github.com/Bob-the-Kuhn)] - USA
 - Erik van der Zalm [[@ErikZalm](https://github.com/ErikZalm)] - Netherlands &nbsp; [![Flattr Erik](https://api.flattr.com/button/flattr-badge-large.png)](https://flattr.com/submit/auto?user_id=ErikZalm&url=https://github.com/MarlinFirmware/Marlin&title=Marlin&language=&tags=github&category=software)

## License

Marlin is published under the [GPL license](/LICENSE) because we believe in open development. The GPL comes with both rights and obligations. Whether you use Marlin firmware as the driver for your open or closed-source product, you must keep Marlin open, and you must provide your compatible Marlin source code to end users upon request. The most straightforward way to comply with the Marlin license is to make a fork of Marlin on Github, perform your modifications, and direct users to your modified fork.

While we can't prevent the use of this code in products (3D printers, CNC, etc.) that are closed source or crippled by a patent, we would prefer that you choose another firmware or, better yet, make your own.
