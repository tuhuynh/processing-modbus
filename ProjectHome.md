ModbusMaster is a class written in and for the Processing environment that enables you to communicate directly with a modbus RTU slave on any hardware serial port. Communication can take place simultaneously on multiple ports. All the communication is taken care of in the class and hides everything from the user.

Functions 1, 2, 3, 4, 15 & 16 are supported with broadcast functionality on function 15 and 16.

Communication is non blocking and you are able stop and start request packets easily.

Testing was done on a Lenovo X220 laptop with an FTDI (US232R-100-BST) USB to RS232 converter communicating with a GM7U LS Industrial PLC. The Duemilanove was also tested directly.

It must be noted in order to overcome the inter-character time out and the delays prevalent in the Processing/Java environment when using the serial library (RXTX-lib) the inter-character time out has been increased to 30ms diverging from the modbus standard. If needed the packet rate transfer from the FTDI chip can be increased by decreasing the latency-timer from 16ms to 1ms and the usb transfer size has to be decreased from 4096 to 256 bytes. This can be done from device manager in port settings.

The complete example code is well documented to easily get you started. The sketch will communicate with the SimpleModbusSlaveArduino sketch.<br>
The class I wrote is directly translated from my SimpleModbusMaster library obtainable from <a href='https://code.google.com/p/simple-modbus/'>https://code.google.com/p/simple-modbus/</a>

The library works with either RS232 or RS485. If RS485 communication is needed than a differential driver like the MAX487 is needed. RTS toggling is not implemented you will need to toggle the transmit/receive enable/disable pins externally. You can make such a circuit yourself that's full proof. I have included a drawing that implements two circuits. One is an auto baud auto Tx-Rx switcher circuit that accepts TTL232 signals. The other circuit incorporates a discrete RS232 to TTL232 level shifter that interfaces with the auto baud auto Tx-Rx switcher. It worked flawlessly at baud rates from 9600 to 115200.<br>
<br>
The library has been totally rewritten to enable USB to RS232 converters to work with out the inter-character delay problem. As mentioned to overcome this a buffer delay has been set to 30ms which steers away from the modbus standard.<br>
<br>
Note:<br>
Google has stopped the upload of new files. The latest libraries can be obtained <a href='https://drive.google.com/folderview?id=0B0B286tJkafVSENVcU1RQVBfSzg&usp=drive_web'>here</a>