# Power Module Signoff

## Subsystem Function
The power system allows the sensor modules to function properly on power from a house and in case of power outages. In order to safely and reliably maintain the funcion of the sensors, the use of an uninteruptable power supply (UPS) is also necessary.

## Constraints
| No. | Constraints | Origin |
| --- | ----------- | ------ |
|  1  | System shall be primarily powered from the house's 120 Volt power supply. | Project Team |
|  2  | Shall have a backup power system that will allow the system to function in case of primary power outage for up to two continuous weeks. | Project Team & Team Supervisor |
|  3  | Shall fully function without regularly changing sensors or head unit batteries. | All External Stakeholders, & Team Supervisor |

<sup>1</sup> The standard residential voltage is 120 V power in the United States. The power module will need to work with the North American standard in order for the sensor modules and head units to have reliable power access.

<sup>2</sup> The sensor modules should still be functional even when the primary power source is out. In the United States the year of 2021 had multiple record breaking power outages lasting up to two weeks. The modules should still be able to record information while the power is out. 

<sup>3</sup> The ESPs and sensors will be powered through the UPS while the main power source is out, to allow for minimal functionality, until it kicks back on. The UPS will include a charging circuit so that the same batteries can stay in place and be recharged.

## Buildable Schematic
 ![UPS Circuit Diagram](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/0be42f93-a2a2-449d-90c9-f369e8c9a1ef)

The power comes from the 15V 2A wall wart that goes through a diode to prevent the eletricity from the battery pack from feeding back into the wall power. The 1 kOhm resistor is used to reduce the amount of amperage that will go to the battery pack allowing for the battery to be charged slowly and not over charge the battery. The other diode is used to provide a low resistance path between the voltage regulator and the battery pack. This enables the ESP32 to be powered if the voltage drops too low. The voltage regulator is used to step down the voltage to output exactly 5V into the ESP32 [1].

## Analysis
<sup>1</sup> The Raspberry Pi 4B and the ESP32 H2 DEVKITM-1 both use 5 volt power in for proper operation. The Raspberry Pi 4 power supply is a transformer that converts the 120V AC down to the needed 5V DC to make the microcontrollers work properly. 

<sup>2</sup> The team is creating a uninteruptable power supply (UPS) using diodes, a voltage regulator, a resistor, a 12V 9Ah battery, and a 120V AC to 15V DC transformer. The circuit diagram is shown above [1]. When running the ESP32-H2 and one sensor, the minimum amount of amp hours needed is 6216 mAh for two weeks. The battery that has been chosen operates at 9Ah which is greater than the 6.216 Ah (6216 mAh) needed, so the system will be able to operate for a minimum of two weeks with the chosen battery. The UPS is created to recharge the battery using the wall power from the house, so when the power is on the battery will be charging, and when the power is off the battery will be powering the ESP32 and the sensor.

<sup>3</sup> The 12V 9Ah battery has the power to let the system fully function without the need of standard wall power. The UPS will recharge the battery when the power is on, allowing the backup batteries for each subsystem to have a longer lifespan then a normal nonrechargeable battery. The 12V 9Ah battery is a lead acid battery, which is being used for cheaper cost and high tolerances [2].


## Bill of Materials (BOM)
| DEVICE | Quantity | Price Per Unit | Total Price |
| ------ | -------- | -------------- | ----------- |
| Raspberry Pi 4 Power Supply | 3 | $8.00 | $32.00 |
| 15V 2A Power Supply | 1 | $11.99 | $11.99 |
| 1N4001 Diode | 1 | $4.07 | $4.07 |
| 12V 9Ah SLA Battery | 1 | $24.99 | $24.99 |
| L7805CV Voltage Regulator | 1 | $8.59 | $8.59 |


## References
[1] J. Smith, “Create your own battery backup power supplies - projects,” All About Circuits, https://www.allaboutcircuits.com/projects/battery-backup-power-supplies/ (accessed Feb. 5, 2024).

[2] Energy, H. (2022, October 18). What are the different types of UPS Batteries. Renewable Alternative Energy Solutions. https://www.hcienergy.com/blog/what-are-the-different-types-of-ups-batteries#:~:text=Lead-Acid%20batteries%20are%20known,like%20in%20large%20power%20applications 
