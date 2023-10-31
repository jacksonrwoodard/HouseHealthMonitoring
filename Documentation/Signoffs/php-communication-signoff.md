# Communication Module Signoff

## Subsystem Function
The function of the communication subsystem is to act as a transmitter for each of the sensor modules and a receiver for the head unit. The function of the transmitter is to send the sensor name, data type, sensor number, and sensor data. The function of the receiver is to receive all of the data from the sensor modules and make the received information available for the processor. 

![TransmitterCommunication](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/cfb66cac-4edb-49bc-8843-ddd06d3072f7)

![RecieverCommunication](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/8ede150c-271b-4bfd-8071-dab157138e04)


## Constraints
| No. | Constraints                                                                                    | Origin                              |
| --- | ---------------------------------------------------------------------------------------------- | ----------------------------------- |
|  1  | System shall not require an internet connection to work and communicate with the head unit and sensors | Home Owners, Insurance Agencies, & Team Supervisor |
|  2  | At least one sensor shall be placed within 200ft of the head unit. | Project Team & Broader Implications & Standards |
|  3  | Sensors shall be within 32ft from each other for every sensor outside of 200ft of the head unit. | Project Team & Broader Implications & Standards |
|  4  | Sensor communication shall send the sensor name, number, data type, and raw data to the head unit. | Project Team |
|  5  | Sensor modules shall not send more than 64 bits (1 packet) of data per data request when transmitting information to the head unit. | Project Team & Standards|
|  6  | The head unit shall, at minimum, receive data every 24 hours, when the data from the sensor reaches the specific limit for each sensor, or when the user requests the data. | Project Team |

<sup>1</sup> In order for the system to not require an internet connection, the system will be designed to work on a Personal Area Network (PAN). In order to achieve this, the Zigbee communication protocol will be used.

<sup>2</sup> In order for the system to work properly all of the sensors have to be able to communicate with the head unit. At least one sensor has to be within 200ft of the head unit because the XB24's maximum range allows for 200ft of indoor communication. Indoor means through the interior walls of a house.

<sup>3</sup> The sensors have to be placed within 32ft of each other for the minimum transmission and reception range of the Zigbee-compliant devices.

<sup>4</sup> The head unit needs to know the sensor information to be able to organize the data of each sensor. Knowing this allows the information to be more easily displayed to the user.

<sup>5</sup> This is the maximum amount of data that Zigbee can send per data request from the head unit. This is also necessary to preserve storage and power consumption. It will also prevent overflow and loss of information.

<sup>6</sup> In order to save power, the system is designed to only send data to the head unit at least once every 24 hours. The ESP32-H2 will store the data received from the sensor and send the stored data to the head unit when requested or when the data has reached the specific limit that causes a threat. The user will have the option to request for the data and if the data is requested the ESP32 will send the data over to the head unit for the user to see. With this constraint, power will be saved significantly allowing the system to have the ability to work off of battery power for a minimum of two weeks.

## Buildable Schematic
#### Head Unit Reciever from Manufacturer
![Reciever](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/86660aec-523b-4ed7-8e32-47fd15c300dd)

The picture shown above is the XB24CAWIT-001, the schematic shows an in-depth design of the receiver.
#### Sensor Module Transmitters from Manufacturer
 ![Transmitter](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/7f7b898d-26be-4da4-8958-8dd662d6b1b3)
 
The picture shown above is the ESP32-H2, the schematic shows an in-depth design of the transmitter.

#### Third-Party Buildable Schematic

![CommunicationSchematic](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/c7b3f395-ec80-4f64-8f86-e75e936cf3f9)


## Analysis

<sup>1</sup> The ESP32-H2 is able to communicate via Zigbee protocols [1]. Zigbee protocols allow for the formation of a mesh network, allowing the system the work for any size house without an existing internet connection [2]. The ESP32-H2 has a built-in 2.4 GHz receiver and transmitter that will form a mesh network to ensure that all sensors will be able to communicate with the head unit [1]. Zigbee is designed to create a personal area network (PAN), which would not require the system to have to connect to an internet connection [3]. Zigbee devices are either preconfigured with a PAN ID to join, or they can discover nearby networks and select a PAN ID network to join [3]. This allows any Zigbee device to connect to each other as long as the PAN ID is in a discoverable range. 

<sup>2</sup> The XB24 is able to communicate via Zigbee protocols [4]. This Zigbee module allows direct connectivity to an Arduino or related board. It will also allow the system to extend its range up to 200ft indoors, giving it the ability to reach the sensors in a house [4]. If a sensor is placed outside of the 200ft range, then a mesh network would be incorporated into that system.

<sup>3</sup> The ESP32-H2 has the capability to transmit data at a minimum of 32ft [5]. For a mesh network to be created, there must be a sensor within 200ft of the head unit and a sensor within 32ft of that sensor. So, as long as each sensor module is placed within 32ft of one another, a mesh network can be used [5]. 

<sup>4</sup> Each sensor module will have a unique 16-bit PAN ID allowing the information to be differentiated from one another [3]. The PAN ID will be sent to the head unit allowing it to act as an identifier to determine which sensor is sending data. The remaining 48 bits of the packet will be used for the data type and the raw data. All of the sensors being used will not require more than 24 bits to send the raw data, so with the amount of remaining bits, this would be possible. The data type will also not require more than 24 bits, so this would be possible. The data This information will be used for showing the live and stored data from the modules. 

<sup>5</sup> Each sensor's data type and read frequency will be coded to comply with Zigbee's 64-bit limit [3]. As stated above, each sensor will have a unique 16-bit PAN ID which will leave the packet with 48 remaining bits. The sensors that are being used will not require more than 48 bits to send the raw data and data type, so this would comply with Zigbee's 64-bit limit.

<sup>6</sup> In order to preserve power, the ESP32 will store the data that the sensors read and send the data to the head unit every 24 hours. The ESP32 will send the data to the head unit if the sensor data reaches the critical level that is specified in the code. The critical level will depend on each separate sensor module. The head unit will have the ability for the user to request the current data from the sensors. If the user requests the data, the ESP32 will send the data that is currently stored on the ESP32 to the head unit, showing the user the active data. The largest amount of data that any sensor module will use is 1 packet because each sensor has a unique 16-bit PAN ID and data reading will not need more than 48 bits with the sensors that are being used in the system. The ESP32 has 4MB ROM of storage allowing it to store the sensor module data for up to 24 hours [5]. There are 32,000,000 bits in 4MB, and at 64 bits per packet, each ESP can store 500,000 readings at a time. There are 86,400 seconds in 24 hours, so if the sensors were to store data every second in a 24-hour period, this would still be possible.



## Bill of Materials (BOM)
| DEVICE | Quantity | Price Per Unit | Total Price | Overall Total |
| ------ | -------- | -------------- | ----------- | ----- |
| ESP32-H2-DEVKITM-1-N4 | 4 | $10.00 | $40.00 | |
| XB24CAWIT-001 | 1 | $29.33 | $29.33 | |
| USB C to USB C Cable [1ft 2-Pack] | 3 | $6.99 | $20.97 | $90.30 |

## References
[1] Espressif Systems, “ESP32-H2 - Espressif Systems,” Adafruit, https://www.espressif.com/sites/default/files/documentation/esp32-h2_datasheet_en.pdf (accessed Oct. 24, 2023). 

[2] “Discover Zigbee protocol 3.0,” Discover Zigbee Protocol 3.0 | Digi International, https://www.digi.com/solutions/by-technology/zigbee-wireless-standard (accessed Oct. 24, 2023). 

[3] “PAN ID,” Pan Id, https://www.digi.com/resources/documentation/Digidocs/90002002/Concepts/c_zb_pan_id.htm?tocpath=Zigbee+networks%7CZigbee+networking+concepts%7CPAN+ID%7C_____0#:~:text=Zigbee%20networks%20are%20called%20personal,devices%20of%20the%20same%20network. (accessed Oct. 25, 2023). 

[4] “Digi xbee S2C 802.15.4 RF modules Datasheet,” IIoT Devices and Services for M2M Networking, https://www.digi.com/resources/library/data-sheets/ds_xbee-s2c-802-15-4?view=fullscreen (accessed Oct. 24, 2023). 

[5] Reolink, “Zigbee range: You must know the truth,” Reolink, https://reolink.com/blog/zigbee-range/ (accessed Oct. 25, 2023). 


