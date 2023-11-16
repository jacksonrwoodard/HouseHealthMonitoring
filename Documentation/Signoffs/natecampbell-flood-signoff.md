# Flood Module Signoff

## Subsystem Function
The function of the flood subsystem is to detect the presence and level of water acting as an indicator of water damage within a home.
![watrer](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143025461/3825dc07-0522-412c-885b-1b09cc66138c)


#### Sensor Operation
![Alt Text](https://lastminuteengineers.com/wp-content/uploads/arduino/Water-Level-Sensor-Working.gif) [1]

The figure above shows how the water sensor's conductivity improves as it gets submerged in more water, lowering the resistance. When the sensor is exposed to less water, its conductivity decreases, thus resulting in higher resistance [1]. This sensor produces an output voltage that corresponds to its resistance, allowing the sensor to be calibrated to formulate a water level equation.




## Constraints
| No. | Constraints                                                                                    | Origin                              |
| --- | ---------------------------------------------------------------------------------------------- | ----------------------------------- |
|  1  | Sensor shall be able to detect if at least one inch of water is present in a room. | Project Team & Broader Implications |
|  2  | Sensors shall be able to detect water levels at various depths.| Project Team |
|  3  | Sensor shall send data to headunit in seconds if water is detected.| Project Team |
|  4  | Sensor shall be placed in areas flooding is most likely to occur. | Project Team |
|  5  | Sensor shall not be placed in areas where condensation can easily form. | Broader Implications |


<sup>1</sup> 1-inch of water can cause thousands of dollars of damage [2]. Being able to detect a minimum of this depth would be essential in determining if a home has significant water damage. 

<sup>2</sup> Flood zones next to rivers and streams can average upwards of 3 feet in depth [3]. Being able to detect more than one inch of water could be valuable in determining how much water damage was done in a house.

<sup>3</sup> Knowing if water has touched the sensor could be a good indicator that a flood or leak has occurred. Being able to quickly send this data would be valuable in preventing a flood or leak from becoming catastrophic.

<sup>4</sup> Placing the sensors in the majority of the rooms and near the home's entrance will provide more accurate detection that water is present.

<sup>5</sup> Sensors placed in high condensation areas could lead to false positives, so preventing this is necessary.



## Buildable Schematic
#### Sensor Dimensions from Manufacturer
<img width="409" alt="Screenshot 2023-11-01 at 3 46 38 PM" src="https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143025461/6a6d9546-a1f0-43ea-845c-3c8a9a9523bb">
[4]

The figure shown above is the dimensions of 4965 water sensor.

#### Third-Party Buildable Schematic

<img width="727" alt="Screenshot 2023-11-01 at 5 41 44 PM" src="https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143025461/ac856427-aae6-4f39-89dd-7e41b464e54c">

The datasheet for the water sensor claims that it outputs an analog signal [4]. When fully submerged the analog value can reach the mid 500s, or 10 bits. Because of this it will need to be connected to the appropiate pin to process this data. According to the manufacturer, the GPIO1 pin on the ESP32 has a 12 bit analog to digital converter [5]. This is more than enough to convert the analog signal from the water sensor into a digital value that the microcontroller can interpret.

## Analysis
<sup>1</sup> The sensor itself has 42 mm or about 1.65 inches of measurable length. It could be placed at the bottom of a wall and measure a 1 inch depth easily.

<sup>2</sup> To measure depths beyond 1.65 inches, sensors can be placed at different heights on a wall. Knowing what height the sensor is at a coefficient can be derived to plug into the depth equation after calibrating the sensor.

<sup>3</sup> The sensor will be connected to the communication module powered by an ESP32 microcontroller. As stated in the communication sign-off, the microcontroller has a transmission rate of 250 Kbps and sends two packets of data at a time. The sensor outputs an analog value that can reach the mid-500s when fully submerged. This analog value is equivalent to about 10 bits in binary. Even with the PAN ID and data type as mentioned in the communication module, one sensor reading will not take up the full 128 bits in the two-packet transmission. Since the ESP32 can send at a 250 Kbps rate, one reading will take less than a second to reach the head unit.

<sup>4</sup> Floodwater can enter a house through doors, windows, cracks in the foundation, sewer systems, and flood vents [6]. Placing the sensors near these areas could provide a more accurate response that flood damage has occurred. Placing multiple sensors at various heights in these locations can also provide the depth of water in the house. Assuming the home is level, the water from a flood will pool throughout the house, so placing a sensor at the base of every room will provide a more detailed view of where the water is in the house.

<sup>5</sup> Sensors that are placed in areas such as a bathroom where condensation is likely to occur will have to be placed with extra consideration to avoid false positives. Placing the sensors right outside the door of a bathroom or in a floor vent could prevent this condensation from building up while still allowing the system to detect if a flood has occurred in that room.

## Bill of Materials (BOM)
| DEVICE | Quantity | Price Per Unit | Total Price | Overall Total |
| ------ | -------- | -------------- | ----------- | ----- |
| 4965 Water Sensor | 1 | $1.95 | $1.95 | $1.95 |

## References
[1] Last Minute Engineers, “In-depth: How water level sensor works and interface it with Arduino,” Last Minute Engineers, https://lastminuteengineers.com/water-level-sensor-arduino-tutorial/ (accessed Nov. 1, 2023). 

[2] “The cost of flooding,” | Flood Damage Cost Calculator, https://www.floodsmart.gov/cost-flooding#:~:text=Just%201%20inch%20of%20water,a%20flood%20could%20cost%20you.&amp;text=Estimates%20based%20on%20national%20FEMA%20flood%20loss%20tables%20of%20cash%20value%20loss. (accessed Nov. 1, 2023). 

[3] “Zone ao,” FEMA.gov, https://www.fema.gov/glossary/zona-ao#:~:text=River%20or%20stream%20flood%20hazard,from%201%20to%203%20feet. (accessed Nov. 1, 2023). 

[4] 123 model (1) - adafruit industries, https://cdn-shop.adafruit.com/product-files/4965/Datasheet.pdf (accessed Nov. 1, 2023). 

[5] “Esp32-H2-DevKitM-1,” esp, https://docs.espressif.com/projects/espressif-esp-dev-kits/en/latest/esp32h2/esp32-h2-devkitm-1/user_guide.html (accessed Nov. 9, 2023). 

[6] “What are the effects of a flood on your home?,” PuroClean, https://www.puroclean.com/blog/effects-of-a-flood-home/ (accessed Nov. 2, 2023). 
