# wireshark-zigbee-profiles
Wireshark profiles (column rules, packet colorization rules, default link key) for the Zigbee protocol.

## Light Mode

![light-mode](https://github.com/user-attachments/assets/87725e63-f6db-485c-83a1-6d9769d76383)

## Dark Mode

![dark-mode](https://github.com/user-attachments/assets/c958fed3-a275-487c-a9f4-24f78979b681)

## How do I add these profiles to Wireshark?

Youtube demo:

[![Add Wireshark Profiles Video Link](https://img.youtube.com/vi/MIKIllyMhKM/0.jpg)](https://www.youtube.com/watch?v=MIKIllyMhKM)

## What Wireshark version + OS are supported?

I have personally tested Windows and Wireshark 4.4.x, but I would imagine that this works on Windows / Linux / MacOS and on any Wireshark 3.x or 4.x release.

## What rules do these profiles add?

### Columns
* No. --> Packet Number
* Length --> Packet Length
* Time --> Relative time at which packet was seen in the capture
* Time Delta --> Time elapsed between this packet and the previous packet
* Info --> Specific info about the packet at its deepest internal layer
* RSSI --> Received signal strength indicator (support depends on sniffer capabilities)
* LQI --> Link Quality Indicator, linearly-scaled RSSI based on manufacturer-specific scaling variables (support depends on sniffer capabilities)
* Channel --> 802.15.4 Channel from 11 - 26
* PAN Src --> Personal Area Network (PAN) Source address. Can be useful for Beacon frames, and Zigbee Interpan frames
* PAN Dst --> Personal Area Network (PAN) Destination address. Most Zigbee packets have a PAN Dst, this just indicates which PAN they are currently operating in.
* MAC Src --> Medium Access Control (MAC) Layer Source address of the packet. This address always represents the current device which a packet is being sent from.
* MAC Dst --> Medium Access Control (MAC) Layer Destination address of the packet. This address always represents the current device which a packet is destined to (current hop).
* MAC Seq --> Medium Access Control (MAC) Sequence number of the packet.
* NWK Src --> Zigbee Network Source address of the packet. If this packet is being relayed through the Zigbee mesh, the address may be different from the current MAC source address.
* NWK Dst --> Zigbee Network Destination address of the packet. If this packet is being relayed through the Zigbee mesh, the address may be different from the current MAC destination address.
* NWK Seq --> Zigbee Network Sequence number of the packet.
* APS Counter --> Application Support Sub-layer (APS) packet counter. Can be useful for tracing APS Acknowledgements and APS retries.
* Sec --> Indicates if the current packet is using Network security and/or APS security, in the format (NWK T/F, APS T/F)
* Extended Source --> 8-byte extended source address of the packet. May be derived from MAC or NWK layer depending on the layers available in the packet.
* UTC Time --> If supported by sniffer hardware, captures the UTC Time the packet was captured.

### Packet Colorization

Color rules added for:
* Zigbee MAC
* Zigbee NWK
* Zigbee APS
* Zigbee ZDO
* Zigbee ZCL

Light mode and Dark mode are slightly different in order to provide good contrast to each scheme.

### Default key

The default trust-center link key 'ZigBeeAlliance09' (5A:69:67:42:65:65:41:6C:6C:69:61:6E:63:65:30:39) is included.

### What hardware do I need to sniff Zigbee traffic?

There are lots of different Zigbee dongles that can support this. I have personally tested [TI dongles](https://e2e.ti.com/support/wireless-connectivity/zigbee-thread-group/zigbee-and-thread/f/zigbee-thread-forum/699648/faq-zigbee-packet-sniffing-solutions) and [nRF52 dongles](https://docs.nordicsemi.com/bundle/ug_sniffer_802154/page/UG/sniffer_802154/intro_802154.html)

Here are some additional resources on Zigbee sniffing from [zigbee2mqtt](https://www.zigbee2mqtt.io/advanced/zigbee/04_sniff_zigbee_traffic.html)
