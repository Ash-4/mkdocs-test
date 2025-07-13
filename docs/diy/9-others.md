# DIY-Other devices

We are unable to support you self building with devices other than those described in the earlier pages. In some cases we do know about devices that simply don't work or have so little market penetration that it is not worth the considerable effort required to develop, test and maintain software for them. 

DCC-EX is not a simple Arduino program, it requires precise access to the internals of each processor type.

We are unable to rely on third party libraries which are generally designed to be the only thing on your Arduino and do not play well in such a demanding scenario.

The following devices are NOT supported:

- Arduino UNO and Nano. We have supported them in the past but the increase in Command Station features has oustripped their miniscule memory capabilities.
- Mega Wifi. Some users have had success with this but we have had approximately 50% failure rate on these devices. Its just not worth it. 
- Arduino Giga. This has a very high cost and some strange WiFi limitations.
- Teensy (various models). These have been made to work in the past but without help we are unable to update or support them.
- ESP32. There are dozens of ESP32 versions and the vast majority of them will not be able to run DCC-EX. We can only support the explicitly recommended version.
- Nano Every.  Lack of demand. 
- UNO R4 WiFi. Useless and expensive.
- Pi Pico