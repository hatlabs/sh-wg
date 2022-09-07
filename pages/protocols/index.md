---
layout: default
title: Protocols and Data Formats
nav_order: 4000
---

# Protocols and data formats

## TCP and UDP

SH-wg supports data transmission both over TCP and UDP.
TCP and UDP are standard Internet data transmission protocols.
TCP is a connection-oriented protocol, meaning that a client such as a tablet or a phone must first establish a connection with the server (the SH-wg device) before any data can be transmitted.
Establishing and maintaining a connection requires some additional processing overhead, but also guarantees that the data is delivered reliably.
Additionally, the client device must know the hostname or the IP address of the server.

UDP is a connectionless protocol, meaning that devices can send data to each other without first establishing a connection.
No overhead is required to establish a connection, but data can be lost if the network is congested.
This is rarely a problem in local networks, however.
Additionally, UDP supports broadcasting, meaning that data can be sent to all devices on the same network without any additional overhead.
Listening devices just need to know the port number to listen to the traffic.
SH-wg utilizes this feature for transmitting data in the local network.

## Data Protocols

SH-wg is able to translate messages received over the NMEA 2000 network into NMEA 0183 sentences.
The NMEA 0183 sentences are by default broadcast over UDP and also transmitted over a TCP server.
The supported NMEA 2000 and NMEA 0183 sentences are listed in Section XXX.

[YDWG RAW](https://www.yachtd.com/downloads/ydwg02.pdf) is a open data protocol defined by Yacht Devices Ltd. for their YDWG-02 series of devices.
It transmits raw NMEA 2000 messages over TCP or UDP with a simple encoding.
SH-wg by default broadcasts the YDWG RAW protocol over UDP and serves it over TCP.
Bidirectional use (receiving messages over UDP) can be enabled in the configuration page.

[SeaSmart.Net](http://www.seasmart.net/pdf/SeaSmart_HTTP_Protocol_RevG_043012.pdf) is a data transmission protocol that encapsulates NMEA 2000 messages in NMEA 0183 sentences.
The protocol can be enabled in the device configuration page.
SeaSmart.Net uses the same ports as NMEA 0183.

The default ports for the different protocols are shown in the table below.

| Protocol | TCP Port | UDP Port |
|----------|:--------:|:--------:|
| NMEA 0183 & SeaSmart.Net | 2222 | 2000 |
| YDWG RAW | 2223 | 2002 |
