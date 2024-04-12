# Experimental Analysis Report

## Introduction
The purpose of this report is to show the experimentation, results, and interpretation of results for each module. These results will then be compared to our constraints and measures of success in ordere to determine if each module has been implemented successfully. Each set of constraint is seperated by their associated module. 

Click to go to [Head Unit](#head-unit) experimentation.

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
-Experimental Design

-Results

-Interpretation


#### Constraint 2 - The head unit shall be able to display and log active and historical data from sensors.
-Experimental Design

-Results

-Interpretation


#### Constraint 3 - The head unit shall be able to detect if the fire module temperature is at 176&#176; Fahrenheit or higher and display a warning.
-Experimental Design

-Results

-Interpretation


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
-Experimental Design

-Results

-Interpretation


#### Constraint 2 - At least one sensor shall be placed within 200ft of the head unit.
-Experimental Design

-Results

-Interpretation

#### Constraint 3 - Sensors shall be within 32ft from each other for every sensor outside of 200ft of the head unit.
-Experimental Design

-Results

-Interpretation

#### Constraint 4 - Sensor communication shall send the sensor name, number, data type, and raw data to the head unit.
-Experimental Design

-Results

-Interpretation

#### Constraint 5 - ESP32 shall be able to send a minimum of 128 bits (2 packets) at a transmission rate of at most 250 Kbps on a 2.4 GHz frequency.
-Experimental Design

-Results

-Interpretation

#### Constraint 6 - The head unit shall, at minimum, receive data every 24 hours, when the data from the sensor reaches a critical level, or when the user requests the data.
-Experimental Design

-Results

-Interpretation


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
-Experimental Design

-Results

-Interpretation

#### Constraint 2 - Head unit shall receive data from the gas module and follow OSHA standards for ammonia, propane, and carbon oxides.
-Experimental Design

-Results

-Interpretation

#### Constraint 3 - The Gas module shall send data to headunit every second if the targeted gases are detected.
-Experimental Design

-Results

-Interpretation

#### Constraint 4 - The Gas module shall be installed in a central location outside each sleeping area or in the immediate vicinity of the bedrooms, at the maximum of 20 feet.
-Experimental Design

-Results

-Interpretation

#### Constraint 5 - The Gas module shall be placed as close as possible to potential gas leak spots.
-Experimental Design

-Results

-Interpretation

#### Constraint 6 - The Gas module shall be orientated to where the target gas vapours tend to rise or fall.
-Experimental Design

-Results

-Interpretation

#### Constraint 7 - The Gas module shall not be placed near entrances/disturbances or fresh air vents where concentrations can be diluted.
-Experimental Design

-Results

-Interpretation

#### Constraint 8 - The Gas module shall not be placed in bathrooms, garages, kitchens, furnace rooms, extremely dusty or dirty areas.
-Experimental Design

-Results

-Interpretation

#### Constraint 9 - The Gas module shall not be placed in areas of the house enviroment where it is colder than -10°C or hotter than 50°C.
-Experimental Design

-Results

-Interpretation

#### Constraint 10 - The Gas module shall not be placed in areas of the house enviroment where the humidity is more than 95%.
-Experimental Design

-Results

-Interpretation

#### Constraint 11 - The Gas module shall be protected from unwanted variation of sensor readings due to noise.
-Experimental Design

-Results

-Interpretation


### Fire
#### Constraint 1 - Shall be able to detect the minimum temperature of 176&deg; Fahrenheit.
-Experimental Design: To test this constraint, the team used the working temperature sensor and out a lighter next to it and recorded the data.

-Results: The team expected the results to display a minimum of 176&deg;F, and it did. Shown below is a chart showing the five trails showing what was expected to see vs. what the actual sensor outputted.
| Trail # | Expected Result | Actual Result |
| ------- | --------------- | ------------- |
| 1 | 176&deg;F | 212.2&deg;F |
| 2 | 176&deg;F | 240.6&deg;F |
| 3 | 176&deg;F | 216.3&deg;F |
| 4 | 176&deg;F | 187.9&deg;F |
| 5 | 176&deg;F | 257.5&deg;F |

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

-Interpretation: Based on the picture and chart shown above, it is easy to see that the sensor can send the data every second consistly.

#### Constraint 3 -  Shall send temperature data to the head unit if 176&deg; Fahrenheit has been reached.
-Experimental Design: This constraint ties into the two contraints above. The sensor is sending data to the headunit every second, so it will send data to the temperature when 176&deg;F has been reached. For testing purposes, the team ran the same test that was done for testing if the sensor can detect 176&deg;F. So, the flame of a lighter is put next to the temperature sensor to make the temperature raise to 176&deg;F, and then the data is sent to the headunit.

-Results: The expected results for this is that it will work with no issues. The results are the same as the first constraint and are shown below in the chart. 
| Trail # | Expected Result | Actual Result |
| ------- | --------------- | ------------- |
| 1 | 176&deg;F | |
| 2 | 176&deg;F | |
| 3 | 176&deg;F | |
| 4 | 176&deg;F | |
| 5 | 176&deg;F | |

-Interpretation

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
