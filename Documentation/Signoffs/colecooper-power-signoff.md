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

## Simulations
![UPS Circuit Design (LTSpice)](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/c8c725cf-a400-472c-b269-5448f329e8d4)
![LTSpice Wall Power Vin](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/5074b587-caf4-4989-b81b-23e3357ab1a2)
![LTSpice Wall Power Vout](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/a686f230-e30d-4d95-8c55-f5097ead8871)

The three pictures shown above are the LTSpice simulations showing the voltage going into the voltage regualtor and the voltage going out of the voltage regulator when there is power in the house.

![UPS Circuit Design (LTSpice) 0V Wall Power](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/3c87b037-fc9f-4db5-8e65-c5ce64d6cd90)
![LTSpice Battery Power Vin](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/853a048f-0d6e-4936-a431-8755fdd66848)
![LTSpice Wall Power Vout](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/062e91d1-5f9b-4085-a865-3825cb048048)

The three pictures shown above are the LTSpice simulations showing the voltage going into the voltage regualtor and the voltage going out of the voltage regulator when there is no power in the house.

## Analysis
<sup>1</sup> The Raspberry Pi 4B and the ESP32 H2 DEVKITM-1 both use 5 volt power in for proper operation. The Raspberry Pi 4 power supply is a transformer that converts the 120V AC down to the needed 5V DC to make the microcontrollers work properly. 

<sup>2</sup> The team is creating a uninteruptable power supply (UPS) using diodes, a voltage regulator, a resistor, a 12.8V 9Ah battery, and a 120V AC to 15V DC transformer. The circuit diagram is shown above [1]. When running the ESP32-H2 and one sensor, the minimum amount of amp hours needed is 6216 mAh for two weeks. The battery that has been chosen operates at 9Ah which is greater than the 6.216 Ah (6216 mAh) needed, so the system will be able to operate for a minimum of two weeks with the chosen battery. The UPS is created to recharge the battery using the wall power from the house, so when the power is on the battery will be charging, and when the power is off the battery will be powering the ESP32 and the sensor.

<sup>3</sup> The 12.8V 9Ah battery has the power to let the system fully function without the need of standard wall power. The UPS will recharge the battery when the power is on, allowing the backup batteries for each subsystem to have a longer lifespan then a normal nonrechargeable battery. The 12.8V 9Ah battery is a lithium iron phosphate battery (LiFePO4), which is being used for longer life span, no maintenance, and improved discharge and charge effciency [2].


## Bill of Materials (BOM)
| DEVICE | PART NUMBER | Quantity | Price Per Unit | Total Price |
| ------ | ----------- | -------- | -------------- | ----------- |
| Raspberry Pi 4 Power Supply | SC0214 | 3 | $8.00 | $32.00 |
| 14.6V LiFePO4 Battery Charger | TP-30W-1462000 | 1 | $13.59 | $13.59 |
| 1N4001 Diode Pack | 1N4001 | 1 | $4.07 | $4.07 |
| 12.8V 9Ah LiFePO4 Lithium Battery | 3164-PSL-SC-1290F2-ND | 1 | $37.99 | $37.99 |
| L7805CV Voltage Regulator | L7805 | 1 | $8.59 | $8.59 |


## References
[1] J. Smith, “Create your own battery backup power supplies - projects,” All About Circuits, https://www.allaboutcircuits.com/projects/battery-backup-power-supplies/ (accessed Feb. 5, 2024).

[2] SuperB, “The lithium difference,” Benefits of Lithium Iron Phosphate batteries (LiFePO4), https://www.super-b.com/en/lithium-iron-phosphate-batteries/benefits-lithium-batteries#:~:text=Lithium%20iron%20phosphate%20battery%20advantages&text=Longer%20life%20span%2C%20no%20maintenance,you%20can%20make%20over%20time. (accessed Feb. 19, 2024). 
