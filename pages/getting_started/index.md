---
layout: default
title: Getting Started
nav_order: 2000
---

# Getting Started

## Physical installation: Mounting and connecting to N2K

Find a suitable location for installing the SH-wg device.
The following factors need to be considered:

- SH-wg must not be directly exposed to the elements.
  Installation in an instrument pod on the deck is fine but the device should be protected from direct rain or splash water.
- The device should be located close to the WiFi access point (if any) or to the client devices.
  The WiFi range in open air is up to 30m and the signal penetrates fiberglass well, but unnecessarily long distances may still cause communication problems.
- The device should not be placed in a metal enclosure; radio waves will not penetrate metal.
  Special attention to device placement and range should be paid with steel or aluminum boats.
- The device should be placed close to the NMEA 2000 network.
  The maximum allowed length of a drop cable is 6 m.

FIXME: Discuss SeaTalk NG drop cable!

FIXME: location for the following description?

NMEA 2000 networks come in many different variants. "Micro" cabling with micro connectors is the most common for smaller boats, and is expected in this manual.
Advanced installations may use mini or mid cables that have much larger diameter cables and heftier connectors.
These allow for longer network installations without an excessive voltage drop.
Furthermore, some vendor-specific variants exist as well.
Raymarine's SeaTalk NG is probably the most common one.
It uses proprietary connectors but is otherwise fully compatible with a standard NMEA 2000 network.

The figure below shows a schematic illustration of a typical NMEA 2000 network.

<img src="media/nmea2000-diagram.svg" width="80%" />

The figure components are:

<dl>
<dt>A</dt>
<dd>A display device such as a Multi-function Display (MFD).</dd>
<dt>B</dt>
<dd>A wind sensor.</dd>
<dt>C</dt>
<dd>A temperature sensor.</dd>
<dt>D</dt>
<dd>A SH-wg device.</dd>
<dt>1</dt>
<dd>N2K power cable. Every NMEA 2000 network segment must be connected to boat's 12 V power system.
   The power cable must be fused with a 3 A fuse.</dd>
<dt>2</dt>
<dd>Network male and female terminators.
   The network backbone must be terminated with 120 ohm resistors for proper network operation.</dd>
<dt>3</dt>
<dd>Drop cables are connected to the backbone using T-connectors.
   Special 4-way T-connectors are also available for connecting multiple devices to the backbone.</dd>
<dt>4</dt>
<dd>Backbone cables extend the backbone. The maximum length of the network, measured from terminator to terminator,
   should not exceed 100 m.</dd>
<dt>5</dt>
<dd>Drop cables connect individual devices to the backbone.
   The maximum length of the drop cable is 6 m.</dd>

</dl>

SH-wg can be connected either directly to a backbone T-connector or using a standard drop cable.

If you decide to mount the device permanently, take a photo of the bottom sticker for future reference.

The device can be mounted on a surface with screws.
Remove the lid temporarily and attach the device using two screws (3.5 mm or smaller) through the mounting holes.

<img src="media/SH-wg_line_drawing_screws.png" width="49%" />

A piece of two-sided tape can also be used to attach the device on a surface.

<img src="media/SH-wg_line_drawing_tape.png" width="49%" />

Alternative mounting methods include zip-ties or just leaving the device hanging from the network T-connector.

## WiFi setup

- captive portal
- client mode
- access point
- changing the settings

- describe the AP and client modes

SH-wg can be configured to create a WiFi access point of its own, or to connect as a client to an existing access point.
These two setups are described in the figures below.

<img src="media/wifi_access_point_mode.svg" width="49%" />
<img src="media/wifi_client_mode.svg" width="49%" />

On left, we have a device working in access point mode.
The client devices connect directly to this access point and communicate with it directly.
Client devices can also communicate with each other using the SH-wg as a switch, albeit with a limited performance.
No internet connectivity is provided to any of the devices.
The amount of clients is limited by the SH-wg to a maximum of 4. FIXME: Check the actual limit!

On right, we have a typical setup with a separate WiFi router device.
The router creates its own WiFi access point and all client devices connect to it.
Devices communicate with SH-wg using the router as a switch.
Internet connectivity can be optionally provided by the router.

### Common Steps

An unconfigured SH-wg will create its own WiFi access point, a so-called "captive portal".
The user can connect to the captive portal and set the WiFi configuration.

When the configuration portal is activated, the blue LED is blinking.
The device is visible on the computer's WiFi network listing:

<img src="media/wifi_selection.jpg" width="40%" />

The network name is "Configure sh-wg-xxxxxxxxxxxx", the last 12 digits corresponding to the device unique identifier.
When conneting to the captive portal, you also need to provide a password to connect to the configuration portal. The password is "abcdabcd".
**NOTE:** This password is *only* used for connecting to the captive portal during the initial setup.

Once you have successfully connected to the configuration portal, you should be automatically presented with the WiFi configuration front page:

<img src="media/captive_portal_front_page.jpg" width="70%" />

### Configuring WiFi Client Mode

First, follow the steps in the "Common Steps" section above.

Click the "Configure WiFi" button.
You'll get a list of nearby WiFi networks.

<img src="media/wifi_configuration.jpg" width="70%" />

FIXME: Outdated image.

One of them should be the boat network you want to connect to.
Select that and enter the network password.
Press "save".

If the SH-wg is able to connect to the configured network, it will restart itself and the blue LED will stop blinking and turn on.
If the configuration failed, the blue LED will keep blinking and you must repeat the operation.

### Configuring WiFi Access Point

First, follow the steps in the "Common Steps" section above.

Click the "Configure WiFi" button.
Now, ignore the list of WiFi networks.
Instead, type in the desired WiFi Access Point name and password in the "Custom Access Point SSID" and "Custom Access Point Password" fields, respectively.

XXX Insert Figure XXX here.

Click "save".

FIXME: LED status indication?

### Changing WiFi Settings

Once the initial configuration has been performed, changing the WiFi settings can be performed in two ways.
First, you can reset the device to factory defaults by following the instructions in Section XXX and then completing the initial setup again.
Or, second, you can enter the device configuration page and update the settings there. This is described in Section XXX.

## Use Case: Transmit NMEA 2000 Data to Apps

<img src="media/nmea2000-to-apps.svg" width="80%" />

Transmitting boat device data to different wireless devices and apps is a common SH-wg use case.
The WiFi may be configured either as a client or as an access point.
In the default configuration, the device broadcasts NMEA 0183 sentences on UDP port 2000 and NMEA 2000 messages in YDWG RAW format on UDP port 2002.
Many apps such as Navionics Boating, iSailor or OpenCPN can receive NMEA 0183 data as is, so no SH-wg configuration changes are needed.
Some apps such as Boating pick up the transmissions automatically while others such as iSailor need to be configured to receive the data.

## Use Case: Wireless NMEA 2000 Bridge

<img src="media/nmea2000-to-nmea2000.svg" width="80%" />

Two SH-wg devices can be used to create a wireless NMEA 2000 bridge.
This setup is useful when the boat's NMEA 2000 network is not accessible from the desired location.
For example, there might be a device pod in sailing boat cockpit with existing power wiring but no NMEA 2000 network.
Or, on a motor boat, flybridge cable ducts might be insufficient for pulling new NMEA 2000 cabling.
In these cases, a wireless NMEA 2000 bridge can be used to connect two separate NMEA 2000 network segments.

Two devices are needed.
Let's call them device A and B.
Device A is connected to the existing NMEA 2000 network segment and configured as an access point.
Additionally, YDWG RAW transmitting must be enabled on device A.
A new NMEA 2000 network segment is created in the new location and device B is connected to it.
Device B is configured as a client to connect to the access point created by device A.
When setting up device B, it is useful to give it a unique hostname such as "sh-wg-b".
YDWG RAW transmitting needs to be enabled on device B as well.

At this point, devices should pick up and forward each other's NMEA 2000 messages.

A wireless bridge is not limited to two SH-wg devices.
Multiple devices can be used to connect multiple NMEA 2000 network segments.

## Use Case: Wireless Signal K Interface

<img src="media/nmea2000-to-sk.svg" width="80%" />

Signal K is an open data format and data exchange platform for marine use.
It allows sharing data between different devices and apps and enables exciting features such as advanced visualization, data logging and connectivity to other open software such as OpenCPN, a popular open source chartplotter application.

SH-wg can be used to connect a NMEA 2000 network to a Signal K server.
Configure the SH-wg device as a client to the WiFi network your Signal K server is connected to.
Then, enable YDWG RAW transmitting on the device.
Finally, connect the Signal K server to the data source.
Open the Signal K server web user interface and navigate to "Server" -> "Data Connections".
If the SH-wg device is connected to the same WiFi and transmitting, it should be automatically discovered as "YDWG-02-UDP".
This connection needs to be enabled. 
Select it by clicking on the item. Then, click the "Enable" checkbox and click "Apply".
Finally, restart the server by clicking "Restart" in the upper right corner.
You should now see "YDWG-02-UDP" in the "Connection activity" listing.