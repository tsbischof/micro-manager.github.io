---
autogenerated: true
title: NikonTI
layout: page
---

## Nikon Ti motorized microscope

<table>
<tr>
<td markdown="1">

**Summary:**

</td>
<td markdown="1">

Adapter for Nikon Ti motorized microscopes

</td>
</tr>
<tr>
<td markdown="1">

**Author:**

</td>
<td markdown="1">

Nico Stuurman and Roy Wollman  
Karl Hoover (additional accessory devices, Matlab compatibility)  
Mark Tsuchida

</td>
</tr>
<tr>
<td markdown="1">

**Maintainer:**

</td>
<td markdown="1">

Mark Tsuchida

</td>
</tr>
<tr>
<td markdown="1">

**License:**

</td>
<td markdown="1">

Source code cannot be made available

</td>
</tr>
<tr>
<td markdown="1">

**Platforms:**

</td>
<td markdown="1">

Windows 32-bit and 64-bit (uses driver supplied by Nikon)

</td>
</tr>
<tr>
<td markdown="1" valign='top'>

**Devices:**

</td>
<td markdown="1">

Microscope hub (TIScope), nosepiece (TINosePiece), condenser turret
(TICondenserCassette), shutters (TIDiaShutter, TIEpiShutter and
TIAuxShutter), optical path (TILightPath), reflector turrets
(TIFilterBlock1 and -2), filter wheels (TIExcitationFilterWheel and
TIBarrierFilterWheel), focus (TIZDrive), PerfectFocus (TIPFSStatus and
TIPFSOffset), XY stage (TIXYDrive), halogen lamp (TIDiaLamp), TIRF
attachment (TITIRF)

</td>
</tr>
<tr>
<td markdown="1" width=20%>

**Since version**

</td>
<td markdown="1">

1.2.18; major update in 1.4.15

</td>
</tr>
<tr>
<td markdown="1">

<b>Peripheral device discovery:</b>

</td>
<td markdown="1">

Supported

</td>
</tr>
</table>

This adapter communicates to all the devices on the Ti microscope
through the TIScope hub device. Thus, to use any of these devices, you
will need to first add the TIScope device.

## Installation

{% include Note text="Do not plug the Ti microscope into a USB 3 port (usually colored blue). The scope may not report its status correctly to the PC after manual operations (observed at least with firmware 5.00, driver 4.3.2.622 or 4.4.1.714). Use a USB 2 port." %}

This adapter uses the driver and API supplied by Nikon. The latest
version of Ti Setup Tool (which includes drivers for the Ti microscope
and TiControl, a control and configuration utility) can be downloaded
from the [Nikon
website](http://nikon.com/products/microscope-solutions/support/download/software/biological/index.htm#toc02).

The required Nikon driver and interface libraries (a.k.a. the
redistributable components of the Nikon Ti SDK) can also be installed
using our own installer:

<table>
<thead>
<tr class="header">
<th><p>SDK Version</p></th>
<th><p>32-bit Installer</p></th>
<th><p>32-bit Driver Version</p></th>
<th><p>64-bit Installer</p></th>
<th><p>64-bit Driver Version</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>4.2.3.572</p></td>
<td><p>N/A</p></td>
<td><p>2.0.2.1</p></td>
<td><p>N/A</p></td>
<td><p>2.0.2.1</p></td>
</tr>
<tr class="even">
<td><p>4.3.2.622</p></td>
<td><p>N/A</p></td>
<td><p>2.0.2.1</p></td>
<td><p>N/A</p></td>
<td><p>2.0.2.2</p></td>
</tr>
<tr class="odd">
<td><p>4.3.3.628</p></td>
<td><p>N/A</p></td>
<td><p>2.0.2.1</p></td>
<td><p>N/A</p></td>
<td><p>2.0.2.2</p></td>
</tr>
<tr class="even">
<td><p>4.4.1.672</p></td>
<td><p><a href="Media:TiSDKRedist32-4.4.1.672.zip" title="wikilink">32-bit 4.4.1.672</a><br />
(updated July 3, 2013)</p></td>
<td><p>2.0.2.1</p></td>
<td><p><a href="Media:TiSDKRedist64-4.4.1.672.zip" title="wikilink">64-bit 4.4.1.672</a><br />
(updated July 3, 2013)</p></td>
<td><p>2.0.5.1</p></td>
</tr>
<tr class="odd">
<td><p>4.4.1.714</p></td>
<td><p><a href="Media:TiSDKRedist32-4.4.1.714.zip" title="wikilink">32-bit 4.4.1.714</a><br />
(uploaded July 16, 2013)</p></td>
<td><p>2.0.5.1</p></td>
<td><p><a href="Media:TiSDKRedist64-4.4.1.714.zip" title="wikilink">64-bit 4.4.1.714</a><br />
(uploaded July 16, 2013)</p></td>
<td><p>2.0.5.1</p></td>
</tr>
</tbody>
</table>

After installing one of these, you might need to **tell Windows to use
the new driver** by opening the Windows **Device Manager**, finding the
Nikon Ti microscope (under Imaging Devices), and choosing Properties
from the right-click menu. Click **Update Driver** and tell Windows to
search C:\\Program Files\\Nikon\\Shared\\Drivers (or the appropriate
equivalent on your system). Note that the driver version number differs
from the SDK and library (DLL) version numbers (the main DLL is normally
installed at C:\\Program Files\\Nikon\\Shared\\Bin\\NikonTi.dll).

To **uninstall** any of these packages, go to the Programs and Features
control panel; the package should be listed with Micro-Manager as
Publisher and you can right-click to uninstall.

It is normally okay to install both Nikon's Ti Setup Tool and our
TiSDKRedist package. The newer DLLs and drivers will be used by both
Micro-Manager and TiControl. To revert to an older version of the driver
and DLLs, you will need to uninstall all the packages that include them
(our TiSDKRedist, Ti Setup Tool, NIS-Elements, etc.).

Another good way to be able to revert to a previous version is to create
a restore point in Windows before installing the new version. This can
be done on Windows 7 in Control Panel &gt; System &gt; Advanced system
settings &gt; System Protection (or search for "create a restore point"
in the Control Panel search box). This will allow you to undo the
installation (and all software installations/removals following that
point).

## Device-specific notes

{% include Note text="There has been a major update to the NikonTI device adapter in version 1.4.15 (nightly build of 20130719). The notes below apply to the new version, unless otherwise noted." %}

### Turret devices

In our experience, movement of the dichroic turret (Filter Block
Cassette) causes significant vibrations in the microscope. This results
in blurry images. To avoid this, add a delay (step 4 of the hardware
configuration wizard) to the FilterBlock device. A delay of 250 msec
seems to work well.

Note that for the turret devices in the NikonTI adapter, Delay is
measured starting when the movement has completed.

The ExtraDelayMs property defaults to the Delay set in the Hardware
Configuration Wizard, and allows you to experiment with different delays
without going through the Wizard. Unlike the Delay set in the Wizard,
the value is not automatically saved, though.

### Shutters

When the Delay is set to zero, the device is considered busy until the
driver reports back that the movement has completed. When Delay is
greater than zero, the report from the driver is ignored and a fixed
delay is used (measured from the *start* of the movement).

### Halogen lamp

With some versions of the Nikon drivers, the TIDiaLamp control may be
unstable (may cause Micro-Manager to crash). If you are having issues,
you might want to try and configure without the DiaLamp.

The TIDiaLamp device is a shutter device (although it will only make
sense to use it as a shutter when doing time-lapse imaging with an
extremely long interval).

There is a ComputerControl property, which needs to be On in order to
control the lamp. Lamp intensities set through manual control and
through computer control are independent of each other.

The Delay setting works similarly to the shutters, but also applies when
setting the Intensity.

### PerfectFocus (PFS)

The valid range for Position depends on the objective in use, even
though the apparent range is fixed. The units are *not* micrometers. For
historical reasons, the Position values used by Micro-Manager are 1/40
of the raw steps reported by the Nikon driver.

### Analyzer

The TIAnalyzer device is available when there is an analyzer in one of
the reflector turrets (Filter Block Cassettes), and simply rotates the
turret. We recommend using the TIFilterBlock devices instead.

### IntensiLight

It is possible to control the IntensiLight epi-fluorescence light source
shutter. If you want to control the IntensiLight with Micro-Manager, you
can either connect it directly to the computer, or you can attach it to
the Nikon Ti controller. In the latter case, you will need to go into
TiControl -&gt; setting, click on "Connection", select the left most
icon, set the connected shutter to IntensiLight and type to Epi (I had
mine attached to shutter 2). Now, you can control the shutter with the
Epi Shutter button on the microscope. You can now use the EpiShutter
Nikon Ti device in Micro-Manager to control the IntensiLight shutter.
Note that you will not be able to control the ND filters this way.

### Tube Lens

The manual tube lens switcher of the Nikon Ti is not encoded (the
computer has no way of knowing its state). You can encode the tube lens
switcher yourself following these instructions:
[Encoding\_the\_Nikon\_TI\_Eclipse\_tube\_lens](Encoding_the_Nikon_TI_Eclipse_tube_lens "wikilink").

## How to report problems

It is not unusual for bugs to depend on the version of Nikon software
(driver and libraries) and microscope firmware. When reporting problems
with the NikonTI adapter, please include, in addition to the
Micro-Manager and Windows version, the Nikon firmware, driver, and
software versions.

Version information is displayed in the Device/Property Browser, under
the TIScope device (check "Show read-only properties"). If you can't get
the device to load, the CoreLog (with debug logging enabled) may contain
the driver and software versions.

The driver version can also be checked in the Windows Device Manager
(The Ti microscope should be listed under Imaging Devices, if correctly
connected and installed).

The Nikon software version is typically the version of the file
C:\\Program Files\\Nikon\\Shared\\Bin\\NikonTi.dll.

{% include Listserv_Search text="Nikon" %}
