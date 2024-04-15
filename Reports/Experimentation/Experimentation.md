# Experimental Analysis Report

## Introduction
The purpose of this report is to show the experimentation, results, and interpretation of results for each module. These results will then be compared to our constraints and measures of success in ordere to determine if each module has been implemented successfully. Each set of constraint is seperated by their associated module. 

Click to go to [Head Unit](#head-unit) experimentation. <br/>
Click to go to [Communication](#communication) experimentation. <br/>
Click to go to [Flood](#flood) experimentation. <br/>
Click to go to [Gas](#gas) experimentation. <br/>
Click to go to [Fire](#fire) experimentation. <br/>
Click to go to [Mold](#mold) experimentation. <br/>
Click to go to [Power](#power) experimentation. <br/>

## Specifications and Constraints

### Table of Constraints
| **No.** | **Constraints** | **Origin** |
| :--: | :-- | :--: |
|  |  |  |
| -- | **Head Unit** | -- |
|  |  |  |
|  1  | The head unit shall know what sensor is sending data to it, the sensors location, and be able to differentiate from other sensors. | Team Supervisor & Project Team |
|  2  | The head unit shall be able to display and log active and historical data from sensors. | Project Team & Team Supervisor |
|  3  | The head unit shall be able to detect if the fire module temperature is at 176&#176; Fahrenheit or higher and display a warning. | Project Team |
|  4  | The head unit shall be able to receive data from the water module to display a warning if water is present and the total water depth. | Project Team |
|  5  | The head unit shall be able to receive data and follow OSHA standards for ammonia, propane, and carbon oxides (50 ppm, 1000 ppm, and 50 ppm respectively over an eight hour window). | Standards & Project Team |
|  6  | The head unit shall be able to interpret, from the received data, that mold could form if the humidity levels exceed 50% and temperatures range between 55&#176; and 85&#176; Fahrenheit for a minimum of two days. | Project Team |
|  |  |  |
| -- |  **Communication**  |  --  |
|  |  |  |
|  1  | System shall not require an internet connection to work and communicate with the head unit and sensors. | Home Owners, Insurance Agencies, & Team Supervisor |
|  2  | At least one sensor shall be placed within 200ft of the head unit. | Project Team |
|  3  | Sensors shall be within 32ft from each other for every sensor outside of 200ft of the head unit. | Project Team |
|  4  | Sensor communication shall send the sensor name, number, data type, and raw data to the head unit. | Project Team |
|  5  | ESP32 shall be able to send a minimum of 128 bits (2 packets) at a transmission rate of at most 250 Kbps on a 2.4 GHz frequency. | Project Team & Standards|
|  6  | The head unit shall, at minimum, receive data every 24 hours, when the data from the sensor reaches a critical level, or when the user requests the data. | Project Team |
|  |  |  |
| -- |  **Flood**  |  --  |
|  |  |  |
|  1  | Sensor shall be able to detect if at least one inch of water is present in a room. | Project Team & Broader Implications |
|  2  | Sensors shall be able to detect water levels at various depths.| Project Team |
|  3  | Sensor shall send data to headunit in seconds if water is detected.| Project Team |
|  4  | Sensor shall be placed in areas flooding is most likely to occur. | Project Team |
|  5  | Sensor shall not be placed in areas where condensation can't easily form. | Broader Implications |
|  |  |  |
| -- |  **Gas**  |  --  |
|  |  |  |
|  1  | The Gas module shall be able to detect ammonia, propane, and carbon oxide. | Project  Team, Insurance Agencies|
|  2  | Head unit shall receive data from the gas module and follow OSHA standards for ammonia, propane, and carbon oxides (50 ppm, 1000 ppm, and 50 ppm respectively over an eight-hour window).| OSHA |
|  3  | The Gas module shall send data to headunit every second if the targeted gases are detected. | Project Team |
|  4  | The Gas module shall be installed in a central location outside each sleeping area or in the immediate vicinity of the bedrooms, at the maximum of 20 feet. | NFPA |
|  5  | The Gas module shall be placed as close as possible to potential gas leak spots. | Project Team, Existing Products |
|  6  | The Gas module shall be orientated to where the target gas vapours tend to rise or fall. | Project Team, Existing Produts |
|  7  | The Gas module shall not be placed near entrances/disturbances or fresh air vents where concentrations can be diluted. | Project Team, Existing Products |
|  8  | The Gas module shall not be placed in bathrooms, garages, kitchens, furnace rooms, extremely dusty or dirty areas. | Project Team, Existing Products |
|  9  | The Gas module shall not be placed in areas of the house enviroment where it is colder than -10°C or hotter than 50°C. | Manufacturer |
|  10  | The Gas module shall not be placed in areas of the house enviroment where the humidity is more than 95%. | Manufacturer |
|  11  | The Gas module shall be protected from unwanted variation of sensor readings due to noise. | Project Team |
|  |  |  |
| -- |  **Fire**  |  --  |
|  |  |  |
|  1  | Shall be able to detect the minimum temperature of 176&deg; Fahrenheit. | Project Team |
|  2  | Shall send sensor data to the ESP32 every second. | Project Team |
|  3  | Shall send temperature data to the head unit if 176&deg; Fahrenheit has been reached. | Project Team |
|  4  | Shall not be a distraction to the homeowner. | All External Stakeholders, Ethics, & Team Supervisor |
|  |  |  |
| -- |  **Mold**  |  --  |
|  |  |  |
|  1  | Shall be able to detect temperature ranges between 55&deg; F - 85&deg; F and humidity levels exceeding 50% RH. | Project Team |
|  2  | Shall be able to communicate through I2C protocol and send data once every hour to its local ESP32-H2 transmitter, then enter sleep mode until the next hour. | Project Team |
|  3  | Shall be protected and not exposed to harsh environmental conditions to prevent any damage to the sensor. | All External Stakeholders, Ethics, & Team Supervisor |
|  4  | Shall give precise temperature and humidity readings within 0.5&deg; F and 2% RH of the actual values, rounding to the nearest whole number to properly evaluate and determine if mold like conditions are present. | Project Team |
|  |  |  |
| -- |  **Power**  |  --  |
|  |  |  |
|  1  | System shall be primarily powered from the house's 120 Volt power supply. | Project Team |
|  2  | Shall have a backup power system that will allow the system to function in case of primary power outage for up to two continuous weeks. | Project Team & Team Supervisor |
|  3  | Shall fully function without regularly changing sensors or head unit batteries. | All External Stakeholders, & Team Supervisor |

## Experimental Results

### Head Unit
#### Constraint 1 - The head unit shall know what sensor is sending data to it, the sensors location, and be able to differentiate from other sensors.
-Experimental Design: To test this constraint, the team connected multiple sensor modules to the head unit and checked if the head unit was able to correctly label each module and output the sensor's data.

-Results: The head unit was able to connect and display independent data from each module.

-Interpretation: The head unit is able to determine what sensor is sending data to it and differentiate it from other sensors. The sensor location had to be input into Home Assistant after the sensors were connected.


#### Constraint 2 - The head unit shall be able to display and log active and historical data from sensors.
-Experimental Design: After connecting the fire temperature sensor to the head unit, we checked the head unit for storage of previous data.

-Results: The temperature sensor's data was successfully stored and can be viewed via graphs.

-Interpretation: The head unit is able to store data from sensors for long term logging. 


#### Constraint 3 - The head unit shall be able to detect if the fire module temperature is at 176&#176; Fahrenheit or higher and display a warning.
-Experimental Design: To test this constraint, the team used the working temperature sensor and out a lighter next to it and recorded the data.

-Results: The team expected the results to display a temperature of 176&deg;F. Shown below is a chart showing that had the head unit read out the fire module's reading and display a warning.
| Trail # | Expected Result | Actual Result |
| ------- | --------------- | ------------- |
| 1 | 176&deg;F | 212.2&deg;F |
| 2 | 176&deg;F | 240.6&deg;F |
| 3 | 176&deg;F | 216.3&deg;F |
| 4 | 176&deg;F | 187.9&deg;F |
| 5 | 176&deg;F | 257.5&deg;F |

![FireSensor176Plus](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/770fc938-6d27-4a5d-9564-22a9b3c843a6)

-Interpretation: The head unit was able to read and display readings of 176&deg;F and higher with a warning for potential fire.

#### Constraint 4 - The head unit shall be able to receive data from the water module to display a warning if water is present and the total water depth.
-Experimental Design

-Results

-Interpretation


#### Constraint 5 - The head unit shall be able to receive data and follow OSHA standards for ammonia, propane, and carbon oxides.
-Experimental Design

-Results

-Interpretation


#### Constraint 6 - The head unit shall be able to interpret, from the received data, that mold could form if the humidity levels exceed 50% and temperatures range between 55&#176; and 85&#176; Fahrenheit for a minimum of two days.
-Experimental Design

-Results

-Interpretation


### Communication
#### Constraint 1 - System shall not require an internet connection to work and communicate with the head unit and sensors.
-Experimental Design: The sensors and head unit communicate via Zigbee Communication.

-Results: The head unit and sensors successfully paired and transmit data using the Zigbee Communication Standard IEEE 802.15.4.

-Interpretation: The head unit and sensors are able to communicate and work without an internet connection.


#### Constraint 2 - At least one sensor shall be placed within 200ft of the head unit.
-Experimental Design: To test this the team took a sensor module into the hallway and walked 100 ft. down the hall and checking if the head unit is still receiving updates from the module.

-Results: The head unit and sensor module were able to continue communication through cynderblock walls and 100 ft. of range. 

-Interpretation: The head unit is able to communicate in a building through cynderblock walls and 100ft. of range effectively. 

#### Constraint 3 - Sensors shall be within 32ft from each other for every sensor outside of 200ft of the head unit.
-Experimental Design: Each module should be within 32ft so the Zigbee mesh can connect different modules together for communication with the head unit. 

-Results: When the sensor modules are within the 32 ft range of each other, they are able to establish the Zigbee mesh needed for communication of sensor modules to the head unit. 

-Interpretation: The Zigbee network is functioning as expected. 

#### Constraint 4 - Sensor communication shall send the sensor name, number, data type, and raw data to the head unit.
-Experimental Design: To test this constraint, the team connected multiple sensor modules to the head unit and checked if the head unit was able to correctly label each module and output the sensor's data.

-Results: The head unit was able to connect and display independent data from each module.

-Interpretation: The head unit is able to determine what sensor is sending data to it and differentiate it from other sensors. The sensor location had to be input into Home Assistant after the sensors were connected.

#### Constraint 5 - ESP32 shall be able to send a minimum of 128 bits (2 packets) at a transmission rate of at most 250 Kbps on a 2.4 GHz frequency.
-Experimental Design: This constraint is a Zigbee requirement for communication of sensors in a Zigbee Mesh Network. 

-Results: All sensor modules and the head unit use Zigbee certified transmitters and receivers.

-Interpretation: The system is able to correctly communicate using Zigbee communication. 

#### Constraint 6 - The head unit shall, at minimum, receive data every 24 hours, when the data from the sensor reaches a critical level, or when the user requests the data.
-Experimental Design: The team tested this constraint by increasing the send and receive times to every 2 seconds.

-Results: The head unit was able to receive and store information from the fire, gas, mold, and flood modules every 2 to 5 seconds.

-Interpretation: All modules are able to communicate much faster than the minimum 24 hours declared by this constraint.


### Flood
#### Constraint 1 - Sensor shall be able to detect if at least one inch of water is present in a room.
-Experimental Design

-Results

-Interpretation

#### Constraint 2 - Sensors shall be able to detect water levels at various depths.
-Experimental Design

-Results

-Interpretation

#### Constraint 3 - Sensor shall send data to headunit in seconds if water is detected.
-Experimental Design

-Results

-Interpretation

#### Constraint 4 - Sensor shall be placed in areas flooding is most likely to occur.
-Experimental Design

-Results

-Interpretation

#### Constraint 5 - Sensor shall not be placed in areas where condensation can't easily form.
-Experimental Design

-Results

-Interpretation


### Gas

#### Constraint 1 - The Gas module shall be able to detect ammonia, propane, and carbon oxide.

-Experimental Design: For testing this constraint, the team thought it would be best to use datasheets for test results. This is due to dangerous gases and not having a safe environment for these tests.

-Results:
For the SRAQ-GO14, the sensor's job was to be able to detect the presence of propane (LPG) and carbon monoxide (CO). The datasheet has a graph that shows the relationships between the different gases that are applied to the sensor.

![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143034071/d42b2aa7-2f19-4db5-bf25-cc4c39664bfb)
Figure 1. SRAQ-GO14 sensitivity curve

For the SRAQ-GO16, the sensor's job was to be able to detect the presence of ammonia (NH4). The datasheet has a graph that shows the relationships between the different gases that are applied to the sensor.

![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143034071/771da9c3-a208-4f04-9230-441933070bb4)
Figure 2. SRAQ-GO16 sensitivity curve

-Interpretation: Based on these datasheets, when the sensor's are properly calibrated and connected properly there would be no doubt that they could be able to detect the specified gases.

#### Constraint 2 - Head unit shall receive data from the gas module and follow OSHA standards for ammonia, propane, and carbon oxides.

-Experimental Design: For this experiment, the sensor's would sense the gases and the data would be sent to the ESP32-H2 ADC and from there Preserve Home Pro coded the microcontrollers to make sure the gas levels stayed under those levels specified in the constraint previously for the eight hour window.

-Results: As previously mentioned, since they are dangerous gases involved, Preserve Home Pro did not test this feature.

-Interpretation: Based on the sensor datasheets, Preserve Home Pro would be able to code the sensor's in order to work together and be able to maintain that data information so that constraint can be met. 

#### Constraint 3 - The Gas module shall send data to headunit every second if the targeted gases are detected.

-Experimental Design: On the Home Assistant UI, the user can click on the sensor and watch how fast it updates. The sensor is meant to send data every second to the head unit and looking Home Assistant UI, it is possible to prove this. The history can be looked at for previous data times.

-Results: The team expected this to work properly because it was edited easily in the code. Shown below is a picture of what the Home Assistant UI looks like when it shows that the sensor is updating, as well as a chart showing the history of the gas sensors proving that it sends the data every second consistly.
| Trail # | Expected Result | Actual Result |
| - | - | - |
| 1 | 1 second | 1 second |
| 2 | 1 second | 1 second |
| 3 | 1 second | 1 second |
| 4 | 1 second | 1 second |
| 5 | 1 second | 1 second |

![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143034071/64398029-9d7d-418c-a2b3-7a3dca8b6101)
Figure 3. Gas sensor history in home assistant user interface.

-Interpretation: Based on the history graph shown above, it is easy to see that the sensor can send the data every second.

#### Constraint 4 - The Gas module shall be installed in a central location outside each sleeping area or in the immediate vicinity of the bedrooms, at the maximum of 20 feet.

-Experimental Design: For this experimentation, Preserve Home Pro does not have access to a house specifically. But going over other manufacturer datasheets of their sensors that are installed in homes, the team ensures that it would be able to implement this feature seamlessly. 

-Results: The results will be other manufacturer datasheets showing the installation process of their sensors that abide by NFPA regulations.

![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143034071/7c41e556-74b8-44a9-abcc-0559341d26b4)
Figure 4. Manufacturer information regarding to where the sensor should be installed.

-Interpretation: Based on the other manufacturer's installation process, the team believes it would not be a problem to follow this process that will meet our constraint.

#### Constraint 5 - The Gas module shall be placed as close as possible to potential gas leak spots.

-Experimental Design: For this experimentation, Preserve Home Pro does not have access to a house specifically. But going over other manufacturer suggestions of their sensors that are installed in homes, the team ensures that it would be able to implement this feature seamlessly. 

-Results: Since the team does not have access to a household this can not be tested.

-Interpretation: Although, the team could not physically test this experimentation, there should not be an issue with placing these sensor near gas used appliances that would have a high chance of a gas leak.

#### Constraint 6 - The Gas module shall be orientated to where the target gas vapours tend to rise or fall.

-Experimental Design: For this experimentation, Preserve Home Pro does not have access to a house specifically. But going over other suggestions of similar use of sensors that are installed in homes, the team ensures that it would be able to implement this feature seamlessly.

-Results: Since the team does not have access to a household this can not be tested by the team. But with information regarding the placement of other sensors this can be implemented.

-Interpretation: This can easily be done by looking at other people's implementation or installation of their sensor's.

#### Constraint 7 - The Gas module shall not be placed near entrances/disturbances or fresh air vents where concentrations can be diluted.

-Experimental Design: For this experimentation, Preserve Home Pro does not have access to a house specifically. But going over other suggestions of similar use of sensors that are installed in homes, the team ensures that it would be able to implement this feature seamlessly.

-Results: Since the team does not have access to a household this can not be tested by the team. But with information regarding the placement of other sensors this can be implemented.

-Interpretation: This can easily be done by looking at other people's implementation or installation of their sensor's.

#### Constraint 8 - The Gas module shall not be placed in bathrooms, garages, kitchens, furnace rooms, extremely dusty or dirty areas.

-Experimental Design: For this experimentation, Preserve Home Pro does not have access to a house specifically. But going over other suggestions of similar use of sensors that are installed in homes, the team ensures that it would be able to implement this feature seamlessly.

-Results: Since the team does not have access to a household this can not be tested by the team. But with information regarding the placement of other sensors this can be implemented.
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143034071/0004803d-92df-47d4-b1b5-da91b61290a4)
Figure 5. This is snip of the NFPA recommendations of where to and not to place a CO sensor.

-Interpretation: Although the team does not physically have access to implement this feature, there would be no reason this could not be achieved by the team.

#### Constraint 9/10 - The Gas module shall not be placed in areas of the house enviroment where it is colder than -10°C or hotter than 50°C and where humidity is more than 95%.

-Experimental Design: For this experimentation, Preserve Home Pro does not have access to a house specifically. But going over the sensor datasheets this a requirement for the correct usage of them, the team ensures that it would be able to implement this feature seamlessly with proper home construction.

-Results: Since the team does not have access to a household this can not be tested by the team. But regarding to a proper home construction, these conditions should would not reached to harm the sensors.
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143034071/e1730d43-05ca-4983-9150-6df635dfe060)
Figure 6. This is the work enviroment that the sensors would need in order to work properly.

-Interpretation: Although the team does not physically have access to implement this feature, there would be no reason this could not be achieved by the team.

#### Constraint 11 - The Gas module shall be protected from unwanted variation of sensor readings due to noise.

-Experimental Design: A RC filter was constructed for our gas sensor's that would need to be implemented in order to mitigate noise on sensor readings in order to provide proper data readings. The Filter works good and filters enough noise out so there can not be a increment in even one ppm. 

-Results: With a LTspice simulation, there are the noise simulations that would be in effect of our sensor that shows the implied noise environment.
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143034071/57ffeafd-37cb-4d78-ba44-9a27c2e58d8a)
Figure 6. LTspice noise simulation for RC Filter

-Interpretation: Since the filter was implemented into our sensor's this allows proper data readings that shows accurate ppm measurements.


### Fire
#### Constraint 1 - Shall be able to detect the minimum temperature of 176&deg; Fahrenheit.
-Experimental Design: To test this constraint, the team used the working temperature sensor and out a lighter next to it and recorded the data.

-Results: The team expected the results to display a minimum of 176&deg;F, and it did. Shown below is a chart showing the five trials showing what was expected to see vs. what the actual sensor outputted.
| Trail # | Expected Result | Actual Result |
| ------- | --------------- | ------------- |
| 1 | 176&deg;F | 212.2&deg;F |
| 2 | 176&deg;F | 240.6&deg;F |
| 3 | 176&deg;F | 216.3&deg;F |
| 4 | 176&deg;F | 187.9&deg;F |
| 5 | 176&deg;F | 257.5&deg;F |

![FireSensor176Plus](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/770fc938-6d27-4a5d-9564-22a9b3c843a6)

-Interpretation: Based of the data provided above, it is safe to say that the temperature sensor can easily display 176&deg;F with no issues.

#### Constraint 2 - Shall send sensor data to the ESP32 every second.
-Experimental Design: On the Home Assistant UI, the user can click on the sensor and watch how fast it updates. The sensor is meant to send data every second to the head unit and looking Home Assistant UI, it is possible to prove this.

-Results: The team expected this to work properly because it is all something to is edited easily in the code. Shown below is a picture of what the Home Assistant UI looks like when it shows that the sensor is updating, as well as a chart showing the five trials proving that it sends the data every second consistly.
| Trail # | Expected Result | Actual Result |
| - | - | - |
| 1 | 1 second | 1 second |
| 2 | 1 second | 1 second |
| 3 | 1 second | 1 second |
| 4 | 1 second | 1 second |
| 5 | 1 second | 1 second |

![FireSensorUpdating](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/a5da7ddc-2e81-49a3-8e74-082f62505235)

-Interpretation: Based on the picture and chart shown above, it is easy to see that the sensor can send the data every second consistly.

#### Constraint 3 -  Shall send temperature data to the head unit if 176&deg; Fahrenheit has been reached.
-Experimental Design: This constraint ties into the two contraints above. The sensor is sending data to the headunit every second, so it will send data to the temperature when 176&deg;F has been reached. For testing purposes, the team ran the same test that was done for testing if the sensor can detect 176&deg;F. So, the flame of a lighter is put next to the temperature sensor to make the temperature raise to 176&deg;F, and then the data is sent to the headunit.

-Results: The expected results for this is that it will work with no issues. The results are the same as the first constraint and are shown below in the chart. Also, in the picture you can see that the temperature above 176&deg;F, is displayed on the head unit.
| Trail # | Expected Result | Actual Result |
| ------- | --------------- | ------------- |
| 1 | 176&deg;F | 212.4&deg;F |
| 2 | 176&deg;F | 252.5&deg;F |
| 3 | 176&deg;F | 201.2&deg;F |
| 4 | 176&deg;F | 192.5&deg;F |
| 5 | 176&deg;F | 232.4&deg;F |

![FireSensor176Plus](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/770fc938-6d27-4a5d-9564-22a9b3c843a6)

-Interpretation: As shown above in the chart, you can see that the sensor sends the data over the head unit when it reaches 176&deg;F. These results can also be proved by looking at the first two constraints becuase they both have to do with the temperature being 176&deg;F or higher and sending the data to the headunit.

#### Constraint 4 - Shall not be a distraction to the homeowner.
-Experimental Design

-Results

-Interpretation


### Mold
#### Constraint 1 - Shall be able to detect temperature ranges between 55&deg; F - 85&deg; F and humidity levels exceeding 50% RH.
-Experimental Design

-Results

-Interpretation

#### Constraint 2 - Shall be able to communicate through I2C protocol and send data once every hour to its local ESP32-H2 transmitter, then enter sleep mode until the next hour.
-Experimental Design

-Results

-Interpretation

#### Constraint 3 - Shall be protected and not exposed to harsh environmental conditions to prevent any damage to the sensor.
-Experimental Design

-Results

-Interpretation

#### Constraint 4 - Shall give precise temperature and humidity readings within 0.5&deg; F and 2% RH of the actual values, rounding to the nearest whole number to properly evaluate and determine if mold like conditions are present.
-Experimental Design

-Results

-Interpretation


### Power
#### Constraint 1 - System shall be primarily powered from the house's 120 Volt power supply.
-Experimental Design

-Results

-Interpretation

#### Constraint 2 - Shall have a backup power system that will allow the system to function in case of primary power outage for up to two continuous weeks.
-Experimental Design

-Results

-Interpretation

#### Constraint 3 - Shall fully function without regularly changing sensors or head unit batteries.
-Experimental Design

-Results

-Interpretation
