# Head Unit Signoff

## Subsystem Function
The function of the head unit is to display active and historical data about each sensor that is used in the entire system. The head unit will be able to determine the differences between each sensor and catergorize the sensors together based on what room they are placed in. It will also be able to detect if the data from the sensor has reached the specified limit for each sensor and display a warning and start a timer if necessary. 

## Subsystem Constraints
| No. | Constraints | Origin |
| --- | ----------- | ------ |
|  1  | The head unit shall know what sensor is sending data to it, the sensors location, and be able to differentiate from other sensors. | Team Supervisor & Project Team |
|  2  | The head unit shall be able to display and log active and historical data from sensors. | Project Team & Team Supervisor |
|  3  | The head unit shall be able to detect if the fire module temperature is at 176&#176; Fahrenheit or higher and display a warning. | Project Team |
|  4  | The head unit shall be able to receive data from the water module to display a warning if water is present and the total water depth. | Project Team |
|  5  | The head unit shall be able to receive data and follow OSHA standards for ammonia, propane, and carbon oxides (50 ppm, 1000 ppm, and 50 ppm respectively over an eight hour window). | Standards & Project Team |
|  6  | The head unit shall be able to interpret, from the received data, that mold could form if the humidity levels exceed 50% and temperatures range between 55&#176; and 85&#176; Fahrenheit for a minimum of two days. | Project Team |

<sup>1</sup> The head unit needs to know what sensor is sending data to it, the sensors location, and be able to differentiate from other sensors. This allows us to identify which sensor is detecting an issue to let the homeowner know where an issue has occurred and what type of issue has occurred. 

<sup>2</sup> The head unit is responsible for displaying all logged data from the sensor modules. The historical data is important for showing that the house has not had any issues like mold buildup, fire, water buildup, or gas leaks. If an issue has occured then the system should be able to show how long there is a type of issue. This information is can be used to prove the value of a house.

<sup>3</sup> The head unit checks if temperatures have been at 176&#176; Fahrenheit or higher, since 176&#176; Farhenheit is the ignition temperature of drywall [1]. 

<sup>4</sup> The head unit checks if water is detecte and what the level of water is acting as an indicator of water damage within a home. Water can cause damages like mold growth, vermine infestations, and even weakend foundations [2].

<sup>5</sup> The head unit needs to know if ammonia, propane, and carbon oxides are present. These gases can cause the poisoning of inhabitants or cause fires when present [3]. 

<sup>6</sup> The head unit is required to know if mold is accumulating by checking if the humidity levels exceed 50% and temperatures range between 55&#176; and 85&#176; Fahrenheit for a minimum of two days. The build up of mold can cause health issues to occupants in the house like trouble breathing or full allegic reactions as well as weaken the foundations of the house [4]. 

## System Schematic

![Head_Unit_Schematic_Design_V2](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/129080386/b23fee8a-9346-4b98-840e-78da58318e56)



## Analysis

<sup>1</sup> The head unit will know which sensor is detecting an issue to let the homeowner know where an issue has occurred and what type of issue has occurred. This information will be determined by using each module's PAN ID. For the head unit to be able to communicate with each module, a XB24 will be used. The Raspberry Pi 4 will be able to communicate with the XB24 using the RX and TX UART communication pins. The Raspberry’s RX pin, pin 16, is the receive pin that the Raspberry Pi 4 will use for the reception of data from the XB-24’s UART Data Out, pin 2. While, the Raspberry’s TX 1 pin 15 is the transmit pin that the Raspberry Pi 4 will use for the transmission of data to the XB-24’s UART Data In, pin 3. 

<sup>2</sup> The head unit needs to be able to compute, store and display data received from the modules. Computing the data is comparing the received values compared to a database of acceptable versus unacceptable values.
The data base of values is defined by specifications mentioned in each sensor module section. The Raspberry Pi 4 B has at minimum 2 GBs of RAM, which allows us to keep 16,000,000,000 bits of data at any given moment while powered on. This allows the head unit to hold onto an active library of checked information from 100 modules received every second with over a 24 hour period leaves 14,000,000,000 bits for holding the values of comparison. Additional storage is required since the Raspberry Pi 4 does not come with ROM storage. 32 gigabytes of sd storage would give us ample storage for holding information from 100 modules recorded every second for over a year. For the 30 year targert a 1 terabyte USB hard drive or solid state drive would still have over 1,900,000,000,000 bits remaining. Finally the data needs to be readable by the user, which can be solved easily by taking advantage of the RPI-Display Port output on the Raspberry Pi and its power out in order to power and use a touch screen display. Using a touch screen display allows the user to interact with the head unit and choose what information should be displayed. 

<sup>3</sup> 

<sup>4</sup> 

<sup>5</sup> 

<sup>6</sup> 

## Bill of Materials (BOM)

## References
[1] N. P. Team, “At what temperature will drywall ignite?,” NCERT POINT, https://www.ncertpoint.com/2022/01/at-what-temperature-will-drywall-ignite.html (accessed Oct. 24, 2023).

[2] Stueber, S. (2023, October 4). What are the common causes of water damage?. West Bend Insurance of Wisconsin. https://www.thesilverlining.com/westbendcares/blog/what-are-the-common-causes-of-water-damage (accessed Oct. 31, 2023).

[3] I. Maloca, J. Macan, V. Varnai, and R. Turk, “[household gas poisonings],” Arhiv za higijenu rada i toksikologiju, https://pubmed.ncbi.nlm.nih.gov/17265686/ (accessed Nov. 1, 2023).

[4] MediLexicon International. (n.d.). Mold in the home: How big A health problem is it?. Medical News Today. https://www.medicalnewstoday.com/articles/288651#mold-and-health (accessed Oct. 28, 2023).

