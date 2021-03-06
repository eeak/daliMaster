# simple.ino

Simple program that set one lamp with a direct arc command and query its actual level to confirm the right receiving of the message. Open the Serial monitor, set baudrate to 115000 and see the output. Remember to change *DALISA* and *LEVEL* definitions according with your setup.

Note the use of those methods:

* **DALIMASTER::regClean()**


Read 0x01 LW14 command register just to reset LW14 status register bits of incoming messages.
* **DALIMASTER::waitForBus(TIMEOUT)**


Wait for bit *LW14_STATUS_BUS_BUSY* and bit *LW14_STATUS_BUS_ERROR* of *0x00 LW14 STATUS REGISTER* to be '0'.
* **DALIMASTER::waitForTel1(TIMEOUT)**


Wait for bit *LW14_STATUS_VALID_REPLY* and bit *LW14_STATUS_1_BYTE_TELEGRAM* of *0x01 LW14 COMMAND REGISTER* to be '1'. After that, a new message is available into 0x01 LW14 command register.
