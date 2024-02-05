# Power Module Signoff

## Subsystem Function
The power system allows the sensor modules to function properly on power from a house and in case of power outages. In order to safely and reliably maintain the funcion of the sensors, the use of an uninteruptable power supply (UPS) is also necessary.

## Constraints
| No. | Constraints | Origin |
| --- | ----------- | ------ |
|  1  | System shall be primarily powered from the house's 120 Volt power supply. | Project Team |
|  2  |  Shall have a backup power system that will allow the system to function in case of primary power outage for up to two continuous weeks. | Project Team & Team Supervisor |
|  3  | Shall fully function witout regularly changing sensors or head unit batteries. | All External Stakeholders, & Team Supervisor |

<sup>1</sup> The standard residential voltage is 120 V power in the United States. The power module will need to work with the North American standard in order for the sensor modules and head units to have reliable power access.

<sup>2</sup> The sensor modules should still be functional even when the primary power source is out. In the United States the year of 2021 had multiple record breaking power outages lasting up to two weeks. The modules should still be able to record information while the power is out. 

<sup>3</sup> The ESPs and sensors will be powered through the UPS while the main power source is out, to allow for minimal functionality, until it kicks back on. The UPS will include a charging circuit so that the same batteries can stay in place and be recharged.

## Buildable Schematic

![UPS Circuit Diagram](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/bc01d92c-44ac-4ca9-aafa-a11561d60d88)


## Analysis
<sup>1</sup>

<sup>2</sup> 

<sup>3</sup> 


## Bill of Materials (BOM)
| DEVICE | Quantity | Price Per Unit | Total Price |
| ------ | -------- | -------------- | ----------- |
| Raspberry Pi 4 Power Supply | 4 | $8.00 | $32.00 |


## References
[1] J. Smith, “Create your own battery backup power supplies - projects,” All About Circuits, https://www.allaboutcircuits.com/projects/battery-backup-power-supplies/ (accessed Feb. 5, 2024).
