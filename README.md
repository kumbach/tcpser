This is yet another fork of Jim Brain's tcpser serial to IP modem emulation program.

The original source code can be found here:
http://www.jbrain.com/pub/linux/serial/

My changes are based upon FozzTexx's code which also includes changes by geneb.

This fork is mainly to add a simple protocol to send connect and disconnect messages to the client.
The purpose of doing so is to provide a simple technique that BBS programs running in the Vice emulator
can use to detect when a call is answered or disconnected. Vice does not set the carrier detect or ring signals
based on tcpser's connection status. BBS programs will have to be modified to detect the connect
and disconnect messages coming from tcpser and respond accordingly.

When the -P argument is passed into tcpser, tcpser will send the following to the client for these Hayes modem responses:

MODEM RESPONSE | SENT TO CLIENT
-------------- | ------------------------
RING | 0xff, 0x01
CONNECT | 0xff, 0x02
NO CARRIER | oxff, 0x03

Kevin Umbach <kumbach@gmail.com>

