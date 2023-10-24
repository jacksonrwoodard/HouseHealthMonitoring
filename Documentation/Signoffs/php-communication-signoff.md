# Communication Module Signoff

## Subsytem Function
The function of the communcation subsystem is to act as a transmitter for each of the sensor modules and a reciever for the headunit. The function of the transmitter is to send the sensor name, data type, sensor number, and sensor data. The function of the reciever is to recieve all of the data from the sensor modules and make the recieved information avaliable for the processor. 

![TransmitterCommunication](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/cfb66cac-4edb-49bc-8843-ddd06d3072f7)

![RecieverCommunication](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/8ede150c-271b-4bfd-8071-dab157138e04)


## Constraints
| No. | Constraints                                                                                    | Origin                              |
| --- | ---------------------------------------------------------------------------------------------- | ----------------------------------- |
|  1  | Sensors shall not be placed in a way where they cannot wirelessly communicate with the system. | Project Team & Broader Implications |
|  2  | System shall not require an internet connection to work and communicaton with the head unit and sensors | Home Owners, Insurance Agencies, & Team Supervisor |
|  3  | Sensor communication shall send the sensor name, number, data type, and raw data to the head unit. | Project Team |

<sup>1</sup> In order for the system to work properly all of the sensors have to be able to communicate with the head unit. If a sensor is not able to communicate with the head unit, then the recorded data is unobtainable by the homeowner. This can be accomplished with a mesh network.

<sup>2</sup> In order for the system to not require an internet connection, the system will be designed to work on a Personal Area Network (PAN). In order to acheieve this, the ZigBee communication protocal will be used.

<sup>3</sup> This is needed because the head unit needs to know the sensor information to be able to organize the data of each sensor. 


## Buildable Schematic
#### Head Unit Reciever
![Reciever](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/86660aec-523b-4ed7-8e32-47fd15c300dd)

The picture shown above is the XB24CAWIT-001, the schematic shows an in-depth design of the reciever.
#### Sensor Module Transmitters
 ![Transmitter](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/7f7b898d-26be-4da4-8958-8dd662d6b1b3)
 
The picture shown above is the ESP32-H2, the schematic shows an in-depth design of the trasmitter.
 
## Analysis
#### Mesh Network


## Bill of Materials (BOM)
| DEVICE | Quantity | Price Per Unit | Total Price |
| ------ | -------- | -------------- | ----------- |
| ESP32-H2-DEVKITM-1-N4 | 4 | $10.00 | $40.00 |
| XB24CAWIT-001 | 1 | $29.33 | $29.33 |

## References

