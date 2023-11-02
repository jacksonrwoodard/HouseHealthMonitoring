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

## Analysis

<sup>1</sup> 

<sup>2</sup>

<sup>3</sup>

<sup>4</sup>

<sup>5</sup>

<sup>6</sup>

## Bill of Materials (BOM)

##References
[1] N. P. Team, “At what temperature will drywall ignite?,” NCERT POINT, https://www.ncertpoint.com/2022/01/at-what-temperature-will-drywall-ignite.html (accessed Oct. 24, 2023).
[2] Stueber, S. (2023, October 4). What are the common causes of water damage?. West Bend Insurance of Wisconsin. https://www.thesilverlining.com/westbendcares/blog/what-are-the-common-causes-of-water-damage (accessed Oct. 31, 2023).
[3] I. Maloca, J. Macan, V. Varnai, and R. Turk, “[household gas poisonings],” Arhiv za higijenu rada i toksikologiju, https://pubmed.ncbi.nlm.nih.gov/17265686/ (accessed Nov. 1, 2023).
[4] MediLexicon International. (n.d.). Mold in the home: How big A health problem is it?. Medical News Today. https://www.medicalnewstoday.com/articles/288651#mold-and-health (accessed Oct. 28, 2023).

