# Flood Module Signoff

## Subsystem Function
The function of the flood subsystem is to detect the presence and level of water acting as an indicator of water damage within a home.
![watrer](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143025461/3825dc07-0522-412c-885b-1b09cc66138c)


#### Sensor Operation
![Alt Text](https://lastminuteengineers.com/wp-content/uploads/arduino/Water-Level-Sensor-Working.gif) [1]

The figure above shows how the water sensor's conductivity improves as it gets submerged in more water lowering the resistance. When the sensor is exposed to less water its conductivity decreases, thus resulting in higher resistance [1]. This sensor produces an output voltage that corresponds to its resistance, gauging this the sensor can be calibrated to formulate a water level equation.





## Constraints
| No. | Constraints                                                                                    | Origin                              |
| --- | ---------------------------------------------------------------------------------------------- | ----------------------------------- |
|  1  | Sensor shall be able to detect if at least one inch of water is present in a room. | Project Team & Broader Implications & Standards |
|  2  | Sensors shall be able to detect water levels at various depths.| Project Team & Broader Implications & Standards |

<sup>1</sup> 1-inch of water can cause thousands of dollars of damage [2]. Being able to detect a minimum of this depth would be essential in determining if a home has significant water damage. 

<sup>2</sup> Flood zones next to rivers and streams can average upwards of 3 feet in depth [3]. Being able to detect more than one inch of water could be valuable in determining how much water damage was done in a house.



## Buildable Schematic
#### Sensor Dimensions from Manufacturer
<img width="409" alt="Screenshot 2023-11-01 at 3 46 38 PM" src="https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143025461/6a6d9546-a1f0-43ea-845c-3c8a9a9523bb">

The picture shown above is the dimensions of 4965 water sensor.
#### Third-Party Buildable Schematic

<img width="727" alt="Screenshot 2023-11-01 at 5 41 44 PM" src="https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143025461/ac856427-aae6-4f39-89dd-7e41b464e54c">

## Analysis
<sup>1</sup> The sensor itself has 42 mm or about 1.65 inches of measurable length. It could be placed at the bottom of a wall and measure a 1 inch depth easily.

<sup>2</sup> To measure depths beyond 1.65 inches, sensors can be placed at different heights on a wall. Knowing what height the sensor is at a coefficient can be derived to plug into the depth equation after calibrating the sensor.

## Bill of Materials (BOM)
| DEVICE | Quantity | Price Per Unit | Total Price | Overall Total |
| ------ | -------- | -------------- | ----------- | ----- |
| 4965 Water Sensor | 1 | $1.95 | $1.95 | |

## References
[1] Last Minute Engineers, “In-depth: How water level sensor works and interface it with Arduino,” Last Minute Engineers, https://lastminuteengineers.com/water-level-sensor-arduino-tutorial/ (accessed Nov. 1, 2023). 

[2] “The cost of flooding,” | Flood Damage Cost Calculator, https://www.floodsmart.gov/cost-flooding#:~:text=Just%201%20inch%20of%20water,a%20flood%20could%20cost%20you.&amp;text=Estimates%20based%20on%20national%20FEMA%20flood%20loss%20tables%20of%20cash%20value%20loss. (accessed Nov. 1, 2023). 

[3] “Zone ao,” FEMA.gov, https://www.fema.gov/glossary/zona-ao#:~:text=River%20or%20stream%20flood%20hazard,from%201%20to%203%20feet. (accessed Nov. 1, 2023). 
