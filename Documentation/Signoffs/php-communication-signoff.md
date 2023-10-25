# Communication Module Signoff

## Subsystem Function
The function of the communication subsystem is to act as a transmitter for each of the sensor modules and a receiver for the head unit. The function of the transmitter is to send the sensor name, data type, sensor number, and sensor data. The function of the receiver is to receive all of the data from the sensor modules and make the received information available for the processor. 

![TransmitterCommunication](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/cfb66cac-4edb-49bc-8843-ddd06d3072f7)

![RecieverCommunication](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/8ede150c-271b-4bfd-8071-dab157138e04)


## Constraints
| No. | Constraints                                                                                    | Origin                              |
| --- | ---------------------------------------------------------------------------------------------- | ----------------------------------- |
|  1  | Sensors shall not be placed more than 200 feet away from the receiver where they cannot wirelessly communicate with the system. | Project Team & Broader Implications |
|  2  | System shall not require an internet connection to work and communicate with the head unit and sensors | Home Owners, Insurance Agencies, & Team Supervisor |
|  3  | Sensor communication shall send the sensor name, number, data type, and raw data to the head unit. | Project Team |

<sup>1</sup> In order for the system to work properly all of the sensors have to be able to communicate with the head unit. If a sensor is not able to communicate with the head unit, then the recorded data is unobtainable by the homeowner. This can be accomplished with a mesh network.

<sup>2</sup> In order for the system to not require an internet connection, the system will be designed to work on a Personal Area Network (PAN). In order to achieve this, the ZigBee communication protocol will be used.

<sup>3</sup> This is needed because the head unit needs to know the sensor information to be able to organize the data of each sensor. 


## Buildable Schematic
#### Head Unit Reciever
![Reciever](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/86660aec-523b-4ed7-8e32-47fd15c300dd)

The picture shown above is the XB24CAWIT-001, the schematic shows an in-depth design of the receiver.
#### Sensor Module Transmitters
 ![Transmitter](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/7f7b898d-26be-4da4-8958-8dd662d6b1b3)
 
The picture shown above is the ESP32-H2, the schematic shows an in-depth design of the transmitter.

#### Third-Party Buildable Schematic

 ![CommunicationSchematic](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/209c1588-a54b-4fe9-bb34-3c8f18ce0dce)

## Analysis
#### Connectivity
The ESP32-H2 is able to communicate via ZigBee protocols [1]. ZigBee protocols allow for the formation of a mesh network, allowing the system the work for any size house [2]. The ESP32-H2 has a built-in 2.4 GHz receiver and transmitter that will form a mesh network to ensure that all sensors will be able to communicate with the head unit [1].

The XB24 is also able to communicate via ZigBee protocols [3]. This ZigBee module allows direct connectivity to a Raspberry Pi or related board. It will also allow the system to extend its range up to 200ft indoors, giving it the ability to reach the sensors in a house [3].


## Bill of Materials (BOM)
| DEVICE | Quantity | Price Per Unit | Total Price | Overall Total |
| ------ | -------- | -------------- | ----------- | ----- |
| ESP32-H2-DEVKITM-1-N4 | 4 | $10.00 | $40.00 | |
| XB24CAWIT-001 | 1 | $29.33 | $29.33 | |
| USB C to USB C Cable [1ft 2-Pack] | 3 | $6.99 | $20.97 | $90.30 |

## References
[1] Espressif Systems, “ESP32-H2 - Espressif Systems,” Adafruit, https://www.espressif.com/sites/default/files/documentation/esp32-h2_datasheet_en.pdf (accessed Oct. 24, 2023). 

[2] “Discover ZigBee protocol 3.0,” Discover Zigbee Protocol 3.0 | Digi International, https://www.digi.com/solutions/by-technology/zigbee-wireless-standard (accessed Oct. 24, 2023). 

[3] “Digi xbee S2C 802.15.4 RF modules Datasheet,” IIoT Devices and Services for M2M Networking, https://www.digi.com/resources/library/data-sheets/ds_xbee-s2c-802-15-4?view=fullscreen (accessed Oct. 24, 2023). 
