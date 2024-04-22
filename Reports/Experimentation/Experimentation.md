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
-Experimental Design: To test this constraint, the team each sensor to the head unit in different orders in order to assure the sensors were connecting and outputting the expected information.

-Results: In the set of 5 trials, the head unit was able to successfully connect to each sensor connected without losing connection to previously connected sensors. Below are pictures of the first series of connections with a table showing the results from the overall trials.
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/14df1e61-af69-41c0-bfb2-769c22c5c1d1)
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/42819db5-2d59-4744-a063-ff098fc8c9b5)
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/b761e1df-f9d8-4d3e-89c9-fd7bec91b468)
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/69105406-5f95-4ca5-ad64-93bb5625f5c2)
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/ca1c62af-7934-4898-b4a0-504f5f715793)
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/7c60aa3d-57aa-44e0-9885-e02d7672744a)

| Sensor Name | Sensor Connection to Head Unit | Number of Sensors Connected |
| :--: | :--: | :--: |
| **Order 1** | | |
| Fire Temperature | Yes | 1 |
| Mold Temperature | Yes | 2 |
| Mold Humidity | Yes | 3 |
| Flood | Yes | 4 |
| Gas Ammonia | Yes | 5 |
| Gas LPG & CO | Yes | 6 |
| **Order 2** | | |
| Gas LPG & CO | Yes | 1 |
| Gas Ammonia | Yes | 2 |
| Flood | Yes | 3 |
| Mold Humidity | Yes | 4 |
| Mold Temperature | Yes | 5 |
| Fire Temperature | Yes | 6 |
| **Order 3** | | |
| Flood | Yes | 1 |
| Fire Temperature | Yes | 2 |
| Mold Temperature | Yes | 3 |
| Mold Humidity | Yes | 4 |
| Gas Ammonia | Yes | 5 |
| Gas LPG & CO | Yes | 6 |
| **Order 4** | | |
| Mold Temperature | Yes | 1 |
| Mold Humidity | Yes | 2 |
| Gas LPG & CO | Yes | 3 |
| Gas Ammonia | Yes | 4 |
| Fire Temperature | Yes | 5 |
| Flood | Yes | 6 |
| **Order 5** | | |
| Fire Temperature | Yes | 1 |
| Flood | Yes | 2 |
| Gas LPG & CO | Yes | 3 |
| Gas Ammonia | Yes | 4 |
| Mold Temperature | Yes | 5 |
| Mold Humidity | Yes | 6 |

-Interpretation: The head unit is able to determine what sensor is sending data to it and differentiate it from other sensors. The sensor location had to be input into Home Assistant after the sensors were connected.


#### Constraint 2 - The head unit shall be able to display and log active and historical data from sensors.
-Experimental Design: After connecting the fire temperature sensor to the head unit, we checked the head unit for storage of previous data over the period of 3 and a half hours. 

-Results: The head unit was able to receive, store, and displat the information from the fire module over the tested 24 hour period.
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/be557d75-6423-4023-8399-ea7b5e531487)

The head unit was able to receive, store, and display information from the mold module over in the 8 hour period tested.
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/6160b027-3dab-4bd1-92df-c5a039619006)

The head unit was able to receive, store, and display the information from the flood module over the tested 8 hour period.
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/273ac1a9-5880-4668-9a7b-a1bb49a53e01)

The head unit was able to receive, store, and display information from the gas module during the 11 hour period tested. 
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/063fe0d6-4234-4e68-a1ab-feb2c135e64c)

The Head unit was successfully showing the active information being stored on the head unit.
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/9f2bc0da-3718-4e96-a646-21a5f45b8750)

-Interpretation: The head unit is able to store and display data for active and historical readings.


#### Constraint 3 - The head unit shall be able to detect if the fire module temperature is at 176&#176; Fahrenheit or higher and display a warning.
-Experimental Design: To test this constraint, the team used the fire temperature sensor and an ignited lighter next to it and recorded the data 5 times. This test shows whether or not the head unit is able to record the temperatures recorded by the sensor and give a warning if the temperature is at or above 176&deg;F.

-Results: The team expected the results to display a warning if a temperature of 176&deg;F or higher is reached. Shown below is the head unit's logging of the temperatures when a lighter is present.

![FireSensor176Plus](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/770fc938-6d27-4a5d-9564-22a9b3c843a6)
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/1c6bad16-9970-44c6-8a34-311e8319ce5f)
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/48f8fc2a-1d03-4137-8043-49f4b7aa249e)

-Interpretation: The head unit was able to read and display readings of 176&deg;F and higher with a warning for potential fire.

#### Constraint 4 - The head unit shall be able to receive data from the water module to display a warning if water is present and the total water depth.
-Experimental Design: To test this constraint the team placed the water sensor in a cup of water to see if the head unit recorded the depth of the water with a warning that water is present. This experiment was repeated seven times.

![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/830fe1e1-5f4d-4333-be36-6bbfe9cc3b3b)
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/389ce137-f493-4c38-9243-771fe374d8a8)
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/9149d1a2-404a-4087-9cec-376a757accc2)


-Interpretation: The head unit was able to detect if water was present, show its depth, and give a warning that water was present.

#### Constraint 5 - The head unit shall be able to receive data and follow OSHA standards for ammonia, propane, and carbon oxides.
-Experimental Design: For this experiment, the sensors would sense the gases and the data would be sent to the ESP32-H2 ADC and from there Preserve Home Pro coded the microcontrollers to make sure the gas levels stayed under those levels specified in the constraint previously for the eight hour window.

-Results: Due to the necesity of dangerous gases in order to fully test this functionality, Preserve Home Pro did not test this feature.

-Interpretation: Based on the sensor datasheets, Preserve Home Pro would be able to code the sensor's in order to work together and be able to maintain that data information so that constraint can be met. 


#### Constraint 6 - The head unit shall be able to interpret, from the received data, that mold could form if the humidity levels exceed 50% and temperatures range between 55&#176; and 85&#176; Fahrenheit for a minimum of two days.
-Experimental Design: For this experiment, the team used a steam gun to raise the temperature and humidity next to the mold module 5 times to see if the head unit will be able to flag that the humidity over 50 % and a temperature over 55&#176 Fahrenheit. 

-Results: The head unit read the raises in temperature and humidity and output a warning that mold is possible. 
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/c16fb8f3-1d48-43f1-b005-234c495aec53)
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/d58d4922-1078-4800-b338-97941bbef565)

-Interpretation: The head unit is able to determine if the values from the mold module are conducive for the growth of mold. 


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

-Results: The head unit was able to connect and display independent data from each module. Below shows all sensors connected to the head unit. 
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/eaf93e98-8745-4588-ba06-3c4b716b8ac3)


-Interpretation: The head unit is able to determine what sensor is sending data to it and differentiate it from other sensors. The sensor location had to be input into Home Assistant after the sensors were connected.

#### Constraint 5 - ESP32 shall be able to send a minimum of 128 bits (2 packets) at a transmission rate of at most 250 Kbps on a 2.4 GHz frequency.
-Experimental Design: This constraint is a Zigbee requirement for communication of sensors in a Zigbee Mesh Network. 

-Results: All sensor modules and the head unit use Zigbee certified transmitters and receivers.

-Interpretation: The system is able to correctly communicate using Zigbee communication. 

#### Constraint 6 - The head unit shall, at minimum, receive data every 24 hours, when the data from the sensor reaches a critical level, or when the user requests the data.
-Experimental Design: The team tested this constraint by monitoring the sensor readings over periods of time ranging from 8 to 24 hours to make sure each sensor updates at least once in the period tested. 

-Results: The head unit was able to receive and store information from the fire more than once within the minimum 24 hour period
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/be557d75-6423-4023-8399-ea7b5e531487)

The head unit was able to receive and store information from the mold module more than once in the 8 hour period.
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/6160b027-3dab-4bd1-92df-c5a039619006)

The head unit was able to receive ans store information from the flood module more than once in the tested 8 hour period.
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/273ac1a9-5880-4668-9a7b-a1bb49a53e01)

The head unit was able to receive and store information from the gas module at least one time in the 11 hour period. 
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/063fe0d6-4234-4e68-a1ab-feb2c135e64c)


-Interpretation: The modules are able to communicate more often than the minimum specification of once every 24 hours.


### Flood
#### Constraint 1 and 2 - Sensor shall be able to detect if at least one inch of water is present in a room and Sensors shall be able to detect water levels at various depths.
-Experimental Design: To test these contrtaints, the sensor was measured with a ruler and marked at .5, 1, and 1.5 inches and put into a container of water that had a depth of 1.5 inches. 
![IMG_0071](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143025461/11550488-0c36-4eae-81e0-ade09d2bcd29)
![IMG_0072](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143025461/a2cb8d4e-ad85-43e8-bdf1-c5aa51d462ed)


-Results: <img width="1089" alt="Screenshot 2024-04-17 at 12 50 48 PM" src="https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143025461/71238f0a-0b4a-4670-85ac-e022e9c6d795">


-Interpretation: Originally the sensor was marked every quarter inch. This did not give the expected results as the readings were very inconsitent. The markings and code were changed to every half inch to provide more accurate readings of a half inch, one inch, and 1.5 inch. As shown in the results the water sensor can mearsure different depths roughly with 0, .5, 1, and 1.5 inches.

#### Constraint 3 - Sensor shall send data to headunit in seconds if water is detected.
-Experimental Design: To adhere to this constraint, the sensor was coded to send data every two seconds.

-Results:<img width="1127" alt="Screenshot 2024-04-16 at 12 15 03 PM" src="https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143025461/ab7a69d4-0743-40cf-ba07-35ea9c23bcbd">


-Interpretation: In its current state the sensor checks for changes every two seconds. As shown from the chart there is updates every two seconds as water levels change followed by a periods of no change when the sensor is dry.

#### Constraint 4 - Sensor shall be placed in areas flooding is most likely to occur.
-Experimental Design: For this experimentation, Preserve Home Pro does not have access to a house specifically. As stated in previous signoffs, floodwater can enter a house through doors, windows, cracks in the foundation, sewer systems, and flood vents. 

-Results: https://github.com/jacksonrwoodard/HouseHealthMonitoring/blob/main/Documentation/Signoffs/natecampbell-flood-signoff.md

-Interpretation: Multiple flood sensors could be placed at various heights on doors, windows, cracks in the foundation, sewer systems, and flood vents to more accurately detect if a flood occured. 

#### Constraint 5 - Sensor shall not be placed in areas where condensation can't easily form.
-Experimental Design: For this experimentation, Preserve Home Pro does not have access to a house specifically. As stated in previous signoffs, areas of high condensation in a home like a bathroom could result in false positives. This was tested by steaming water over the sensor with a shirt steamer. 

![IMG_0059](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143025461/b4c7118d-77a0-46e4-a284-86abc785a09f)


-Results:
<img width="316" alt="Screenshot 2024-04-17 at 2 05 13 PM" src="https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143025461/358e2ffb-f7d4-4c14-aa64-895994729d9d">

 

-Interpretation: As expected, the condesation on the sensor resulted in false positives. The sensor would be placed in normally dry places to ensure more accurate results.


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

-Results: As previously mentioned, since there are dangerous gases involved, Preserve Home Pro did not test this feature.

-Interpretation: Based on the sensor datasheets, Preserve Home Pro would be able to code the sensor's in order to work together and be able to maintain that data information so that constraint can be met. 

#### Constraint 3 - The Gas module shall send data to headunit every second if the targeted gases are detected.

-Experimental Design: On the Home Assistant UI, the user can click on the sensor and watch how fast it updates. The sensor is meant to send data every second to the head unit and looking Home Assistant UI, it is possible to prove this. The history can be looked at for previous data times.

-Results: The team expected this to work properly because it was edited easily in the code. Shown below is a picture of what the Home Assistant UI looks like when it shows that the sensor is updating, as well as a chart showing the history of the gas sensors proving that it sends the data every second consistly.
| Trial # | Expected Result | Actual Result |
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

-Experimental Design: For this experimentation, Preserve Home Pro does not have access to a house specifically. But going over other manufacturer datasheets of their sensors that are installed in homes, the team ensures that it would be able to implement this feature seamlessly. This would be informed to the home owner.

-Results: The results will be other manufacturer datasheets showing the installation process of their sensors that abide by NFPA regulations and to inform the user.

![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143034071/7c41e556-74b8-44a9-abcc-0559341d26b4)
Figure 4. Manufacturer information regarding to where the sensor should be installed.

-Interpretation: Based on the other manufacturer's installation process, the team believes it would not be a problem to follow this process that will meet our constraint.

#### Constraint 5 - The Gas module shall be placed as close as possible to potential gas leak spots.

-Experimental Design: For this experimentation, Preserve Home Pro does not have access to a house specifically. Also, due to the use of dangerous gases Preserve Home Pro could not test this. But going over other manufacturer suggestions of their sensors that are installed in homes, the team ensures that it would be able to implement this feature seamlessly. 

-Results: Since the team would be dealing with dangerous gases, the team did not test this experiment.

-Interpretation: Although, the team could not physically test this experimentation, there should not be an issue with placing these sensor near gas used appliances that would have a high chance of a gas leak.

#### Constraint 6 - The Gas module shall be orientated to where the target gas vapours tend to rise or fall.

-Experimental Design: For this experimentation, Preserve Home Pro does not have access to a house specifically. Also, due to the use of dangerous gases this would not be safe for us to test. But going over other suggestions of similar use of sensors that are installed in homes, the team ensures that it would be able to implement this feature seamlessly.

-Results: Since the team would be dealing with those dangerous gases this could not be tested. But with other manufacturer information regarding the placement of other sensors this can be implemented.

-Interpretation: This can easily be done by looking at other people's implementation or installation of their sensor's.

#### Constraint 7 - The Gas module shall not be placed near entrances/disturbances or fresh air vents where concentrations can be diluted.

-Experimental Design: For this experimentation, Preserve Home Pro placed the sesnors next to an air vent for testing purposes. 

-Results: The team noticed a change in ppm when the sensor was introduced to fresh air that would push away the targeted gases that would cause insufficient and inaccurate ppm measurements.
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143034071/de82e3dd-6289-4e0a-8421-cf7ef7df8f6e)
Figure 5. Gas sensors next to fresh air vent for disturbance testing

-Interpretation: The homeowners would be advised to not place the sensors next to air disturbances that would affect the data measurements.

#### Constraint 8 - The Gas module shall not be placed in bathrooms, garages, kitchens, furnace rooms, extremely dusty or dirty areas.

-Experimental Design: For this experimentation, Preserve Home Pro swept up dust and dirt and then introduced those elements to the sensors to see if there would be a disturbance in measurements taken.

-Results: The team noticed when the elements was introduced to the sensors that it messed data measurements and provided serious inaccurate measurements.
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143034071/63688f76-be46-4691-bda2-7f5b45456b6f)
Figure 6. Dirt and dust that was going to swept into the sensors for constraint purposes.

-Interpretation: The homeowners would be advised to not place the sensor in these areas due to the fact it would cause inaccurate measurements.

#### Constraint 9/10 - The Gas module shall not be placed in areas of the house enviroment where it is colder than -10°C or hotter than 50°C and where humidity is more than 95%.

-Experimental Design: For this experimentation, Preserve Home Pro tested this by just having the sensors connected in the range where it would be a viable working environment.

-Results: Though the team could not test the bounds of those conditions where they are lower or greater than the specified range the sensors worked as intended for the right working environment range.
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143034071/e1730d43-05ca-4983-9150-6df635dfe060)
Figure 7. This is the work enviroment that the sensors would need in order to work properly.

-Interpretation: Although the team does not physically test this with those ranges mentioned in the results section, the team suspects that with proper home construction there would not be an issue keeping that environment for the sensors.

#### Constraint 11 - The Gas module shall be protected from unwanted variation of sensor readings due to noise.

-Experimental Design: A RC filter was constructed for our gas sensor's that would need to be implemented in order to mitigate noise on sensor readings in order to provide proper data readings. The Filter works good and filters enough noise out so there can not be a increment in even one ppm. 

-Results: With a LTspice simulation, there are the noise simulations that would be in effect of our sensor that shows the implied noise environment.
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143034071/57ffeafd-37cb-4d78-ba44-9a27c2e58d8a)
Figure 8. LTspice noise simulation for RC Filter

-Interpretation: Since the filter was implemented into our sensor's this allows proper data readings that shows accurate ppm measurements.

### Fire
#### Constraint 1 - Shall be able to detect the minimum temperature of 176&deg; Fahrenheit.
-Experimental Design: To test this constraint, the team used the MLX90614 temperature sensor and compared the temperature values to the PID Temperature Controller and recorded the data in a graph. The team is getting the temperature value of 176&deg;F on the PID Temperature Controller by putting the flame of a lighter on it and getting the tempature value up to 176&deg;F and then measuring the value with the MLX90614.

-Results: The team expected the results to display a minimum of 176&deg;F, and it did. As you can see in the graph the temperature values are accurate when the temperature is lower but when it raises to 176&deg;F, there is a large amount of error.

![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/e86141c0-3f38-4aab-bee5-ecfc0be1386f)

-Interpretation: Based on the graph above, you can see that the MLX90614 cannot accurately read 176&deg;F. When the temperature values are lower, the values are similar, but when the temperature raises they are inaccurate. This could be because of placement errors, the way the light is reflecting off of the PID Temperature Controller, or because the MLX90614 has a broken flim over it. This is the way it came in the box. According to the data sheet, the MLX90614 should only have a +-7.2&deg;F error when at the range of 176&deg;, and this is not the case.

#### Constraint 2 - Shall send sensor data to the ESP32 every second.
-Experimental Design: On the Home Assistant UI, the user can click on the sensor and watch how fast it updates. The sensor is meant to send data every second to the head unit and looking Home Assistant UI, it is possible to prove this.

-Results: The team expected this to work properly because it is something that is edited easily in the code. Shown below is a picture of what the Home Assistant UI looks like when it shows that the sensor is updating, a chart showing the five trials, and a graph of how often the data is sent proving that it sends the data every second consistly.
| Trial # | Expected Result | Actual Result |
| - | - | - |
| 1 | 1 second | 1 second |
| 2 | 1 second | 1 second |
| 3 | 1 second | 1 second |
| 4 | 1 second | 1 second |
| 5 | 1 second | 1 second |

![FireSensorGraph](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/58f22206-3f49-448e-a030-1c51d61aa819)

![FireSensorUpdating](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/a5da7ddc-2e81-49a3-8e74-082f62505235)

-Interpretation: Based on the graph and chart shown above, it is easy to see that the sensor can send the data every second consistly. If you look at the x axis on the graph you can see that Home Assistant is recieving the data every second as expected.

#### Constraint 3 -  Shall send temperature data to the head unit if 176&deg; Fahrenheit has been reached.
-Experimental Design: This constraint ties into the two contraints above. The sensor is sending data to the headunit every second, so it will send data to the temperature when 176&deg;F has been reached. For testing purposes, the team ran the same test that was done for testing if the sensor can detect 176&deg;F.

-Results: The expected results for this is that it will work with no issues. In the graph you can see that the temperature does reach above 176&deg;F and saved in Home Assistant. In the other figure you can see what the output is on the Home Assistant UI.

![FireSensorGraph](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/58f22206-3f49-448e-a030-1c51d61aa819)
![FireSensor176Plus](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/770fc938-6d27-4a5d-9564-22a9b3c843a6)

-Interpretation: As shown above in the graph, you can see that the sensor sends the data over the head unit when it reaches 176&deg;F and is displayed to the user to see. So this works correctly.

#### Constraint 4 - Shall not be a distraction to the homeowner.
-Experimental Design: The team did research on how to professionally measure a distraction, and we found on the NHTSA website that taking a poll is an effective way to test if something is a distraction. The team asked 10 people if this device would be a distractiion to them if it was in their house are the results are shown below.

-Results: The expected results were that the device would not be a distraction because it was so small and hardly visable unless someone was directly looking for it. Below is the results of the poll.
| Person # | Expected Result | Actual Result |
| - | - | - |
| 1 | No | No |
| 2 | No | No |
| 3 | No | No |
| 4 | No | No |
| 5 | No | No |
| 6 | No | Yes |
| 7 | No | No |
| 8 | No | No |
| 9 | No | No |
| 10 | No | No |


-Interpretation: Based on the results shown above, it is clear to say that out of 10 people surveyed, the device is not a distraction. The one person that said that it was a distraction, said the reason why it is a distraction is because it is visiable and would be noticable on the ceiling on their home.

-Source: https://www-nrd.nhtsa.dot.gov/departments/Human%20Factors/driver-distraction/Topics03.htm


### Mold
#### Constraint 1 - Shall be able to detect temperature ranges between 55&deg; F - 85&deg; F and humidity levels exceeding 50% RH.
-Experimental Design: For this experiment, the temperature and humidity sensor was tested in various environments. First, the sensor was placed in a lunch box, with an ice pack, to prove that temperature will read down to 55&deg;F. Then, the sensor was taken out of the lunch box and a flame from a lighter was ignited to prove that temperature will read up to 85&deg;F. Next, the humidity reading was tested by running a steamer underneath the sensor to prove that the sensor will read relative humidity levels exceeding 50% RH.

-Results: The results calculated were as expected and prove that the system will detect temperature values between 55&deg;F – 85&deg;F and humidity levels exceeding 50% RH.

![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/104484972/823975ed-fa66-41b1-a8f1-c6b87684f833)

Figure 1. Temperature reading showing 55&deg;F - 85&deg;F<br>

![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/104484972/2f3500b2-f190-4583-a601-13244622a7c5)

Figure 2. Exact reading of 55&deg;F<br>

![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/104484972/d5c22478-881f-469b-9a75-c6a84598ce1d)

Figure 3. Relative Humidity test<br>

![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/104484972/1e328134-48f6-44cd-82bf-1513137c99b6)

Figure 4. Temperature readings from Humidity test<br>


-Interpretation: Figure 1 does a great job of showing the range of temperature values the sensor can detect. The degress in Fahrenheit is shown in respect to time as the sensor is placed in different conditions. The graph shows the temperature reading of approximately 55&deg;F and gradually increasing to a value greater than 85&deg;F due to the flame. Figure 2 proves that the sensor can detect temperature values as low as 55&deg;F. The screenshot captures the exact moment the sensor measured 55&deg;F. Figure 3 shows the test results from the sensor being placed near a steamer. The graph shows 5 trials of this and how the humidity rises and lowers to the desired relative humidity level. Figure 4 shows the test results of the temperature values as the sensor is placed near a steamer. The 5 trials show that the temperature will increase to the desired level when the steamer gets hot.<br>

#### Constraint 2 - Shall be able to communicate through I2C protocol and send data once every hour to its local ESP32-H2 transmitter, then enter sleep mode until the next hour.
-Experimental Design: In the designed code, the team has the temperature and humidity sensor updating every 2 seconds as long as there is an update in one of the values. However, if the sensor does not pick up on new readings, the sensor will enter sleep mode and will not send new data to the head unit until a new reading has been detected. This will help preserve power for the head unit to operate at an ideal performance. The sensor has a wired connection to the ESP32-H2 microcontroller, following I2C protocol, as there is a SDA and SCL wire connected from the sensor to the microcontroller.

-Results:

![Sleep_mode](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/104484972/c37e5cc7-42b8-4917-b62a-4d57041c16aa)

| Trial | Time between update |
| - | - |
| 1 | 40 min |
| 2 | 56 min |
| 3 | 1 hour |
| 4 | 52 min |
| 5 | 1 hour |

-Interpretation: In the graph above, it is proven that the temperature and humidity sensor will enter sleep mode while a constant value is maintained. The graph shows a constant reading from both the temperature and humidity, and it will stay that way until a new value is detected. In the provided graph, the data is not updated for over 40 minutes. This is because the sensor has not detected a change in either value and it has entered sleep mode. The table above shows more trials of how long the sensor can stay in sleep mode before it is woken up with a new value detected. For each trial, the sensor is set in a stabilized environment to help maintain steady temperature and humidity.

#### Constraint 3 - Shall be protected and not exposed to harsh environmental conditions to prevent any damage to the sensor.
-Experimental Design: The SHT30 temperature and humidity sensor is a wired enclosed shell. The sensor is manufactured this way to protect the sensor from being exposed to harsh environments and prevent any damage. To experiment that the sensor will not take any damage when placed in a harsh environment, a flame was held up the sensor. While the encolser took a slgith hit and started melting, the sensor itself was not harmed and was able to record all the active data while exposed to this flame.

-Results:

![IMG_1108](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/104484972/1ea65f7b-9c70-4734-92da-f369a023b9d6)

![TEMP_GRAPH2](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/104484972/824a545c-ad09-48fe-82bc-f85bd8df8a1c)


-Interpretation: The picture above is the SHT30 temperature and humidity sensor in its enclosed shell. This allows the sensor to not be openly exposed to the harsh environments. You can see the slight burn of the plastic from the experiment, but the sensor remained unharmed. The graph shows the sensor actively reading the fluctuating values as the flame is applied to the sensor. The readings are skewed but the sensor was never harmed while being exposed to the flame. You can see the spike in temperature due to the flame present. According to the manufacturer, the SHT30 sensor was designed in comparison to the weather-proof mesh sensor. It is compared to this sensor because it was designed to withstand environments that most sensors would not be able to survive in. The link below is a reference to the manufacturer's website, stating that the SHT30 is widely compared to the weather-proof mesh sensor.
https://www.adafruit.com/product/5064?gad_source=1&amp;gclid=Cj0KCQjwqP2pBhDMARIsAJQ0CzqlgH_Vrp7xm4fY1QcRbdX0pUI5kT-38Ae2RRNolKE7GWGYOe8_RYYaAsEoEALw_wcB

#### Constraint 4 - Shall give precise temperature and humidity readings within 0.5&deg; F and 2% RH of the actual values, rounding to the nearest whole number to properly evaluate and determine if mold like conditions are present.
-Experimental Design: Testing of the sensor's precision has already been conducted by the manufacturer. Therefore, the team has taken the datasheet's words and graphs has proof that the sensor will detect at very precise measurements within our specs. To further test this constraint, The SHT30 and MLX90614 temperature sensors were measured and compared at specific time stamps. The recorded values are both sensors measuring room temperature.

-Results:

![humidity_accuracy](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/104484972/eea91364-3311-4ed3-98b2-fbb3c27e0abd)

![temperature_accuracy](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/104484972/274f6fd2-ae54-4f1f-bbfc-02a442d105ba)

![matching temp](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/104484972/9c35776b-8cb4-4ad3-98b9-477fbf8e2a19)

| Trial | time | SHT30 temp | MLX90614 temp |
| - | - | - | - |
| 1 | 4:00 pm | 70.9&deg;F | 70.9&deg;F |
| 2 | 4:05 pm | 71.2&deg;F | 71.6&deg;F |
| 3 | 4:10 pm | 71.6&deg;F | 71.8&deg;F |
| 4 | 4:15 pm | 71.4&deg;F | 71.4&deg;F |
| 5 | 4:20 pm | 71.5&deg;F | 71.3&deg;F |

-Interpretation: The graphs provide evidence that the sensor will detect at precisions wihtin the constrained specs. The humidity detects within + or - 2% relative humidity of the actual value when between 10% RH and 90% RH, and the temperature detects within + or - 0.5&deg;F of the actual value when between -10&deg;F and 110&deg;F. Also, a screenshot of the detected temperature value from the SHT30 sensor and MLX90614 sensor is given to provide proof that the sensor is detecting at very close precision. The link to the SHT30 datasheet is provided here.
https://cdn-shop.adafruit.com/product-files/5064/5064_Sensirion_Humidity_Sensors_SHT3x_Datasheet_digital.pdf


### Power
#### Constraint 1 - System shall be primarily powered from the house's 120 Volt power supply.
-Experimental Design: This constraint was tested by hooking a 16.6 V transfomer to a wall outlet and running the power through the Uninterruptable Power Supply's (UPS) circuit. The team then measured the output voltages from the UPS to ensure that the power out was the expected value over a period of 2 hours. 

-Results: Over the period of 2 hours, the voltage was at worst 0.418 % lower than the expected 5 V output.
| Time | Expected Result | Actual Result |
| ------- | --------------- | ------------- |
| 3:30 PM | 5 V | 4.9791 V |
| 3:45 PM | 5 V | 4.9792 V |
| 4:00 PM | 5 V | 4.9792 V |
| 4:15 PM | 5 V | 4.9793 V |
| 4:30 PM | 5 V | 4.9792 V |
| 4:45 PM | 5 V | 4.9795 V |
| 5:00 PM | 5 V | 4.9793 V |
| 5:15 PM | 5 V | 4.9793 V |
| 5:30 PM | 5 V | 4.9792 V |

![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/4edb1917-299f-4efc-b9a2-8092775e3326)



-Interpretation: The voltage output of the UPS stays within the expected operating voltages of the sensor modules using 120 V wall power.

#### Constraint 2 - Shall have a backup power system that will allow the system to function in case of primary power outage for up to two continuous weeks.
-Experimental Design: To test this constraint, the team ran the mold module reporting every two seconds and measured the voltage of the battery every ten minutes over the course of an hour 3 times.

-Results: The battery drew 0.0598 V during the first trial, 0.0637 V during the second trial, and 0.06175 V during the third trial while the mold module was reporting every 2 seconds.

![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/27e0dbcc-cdba-4b48-b085-39ab5e4feb90)
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/f02d7f15-a2c8-4aaf-ae5c-93527cd89f6f)
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/3fe14ef8-1d5a-4131-84ab-bc94bae7d178)


-Interpretation: With the mold module reporting every 2 seconds drawing up to 45 mA with a normal draw of 30.5 mA, the UPS' battery can supply up to an average 22 hours of power. With the sensor reporting only once per hour, the battery will last up to 12 days. 


#### Constraint 3 - Shall fully function without regularly changing sensors or head unit batteries.
-Experimental Design: This constraint was tested by monitoring the continual functionality of the mold module over a 5 hour period.

-Results: The power mold module's humidity sensor was able to function on the UPS' power over a 3 day period. The battery used in the UPS is a LFP which is rated for at least 4000 cycles of charging and discharging with an estimated life of 10 years of service.
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/ffe78fec-c2aa-4b12-9e46-11349d786924)

-Interpretation: The UPS was able to maintain the mold module's power for the tested 6 day period. There were some drops in power due to the team shifting the mold module between power supplies to ensure accurate readings. This experiment shows that the UPS system can sustain the mold module for at least the tested period. 
