# Mold Module Signoff

## Subsystem Function
The function of the mold module subsystem is to detect if mold is likely to grow within the surrounding environment of the sensor. The SHT30 Temperature and Humidity Sensor will gather temperature and humdity levels and send its respective data to an ESP32-H2 micro-controller. The mold module will send data to the ESP32-H2 every hour to allow for computations of the peak and average values.
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/104484972/3401a3b6-74a1-49af-a090-dfe94abc742c)


## Constraints
| No. | Constraints | Origin |
| --- | ----------- | ------ |
|  1  | Shall be able to detect temperature ranges between 55&deg; F - 85&deg; F and humidity levels exceeding 50% RH. | Project Team |
|  2  | Shall be able to communicate through I2C protocol and send data every hour to its local ESP32-H2 transmitter. | Project Team |
|  3  | Shall be protected and not exposed to harsh environmental conditions to prevent any damage to the sensor. | All External Stakeholders, Ethics, & Team Supervisor |
|  4  | Shall give precise readings to properly evaluate and determine if mold like conditions are present. | Project Team |

<sup>1</sup> The humidity and temperature sensors must be able to detect the specified levels because mold like conditions are highly probable when in those ranges. The highest probability of mold occurs when the temperature is 80&deg; F and the relative humidity level is 95% [3]. Other mold like conditions arise when temperatures are between 55&deg; F - 85&deg; F and humidity levels exceeding 50% RH.

<sup>2</sup> The sensor must be able to communicate to the ESP32-H2 microcontroller through I2C protocol because they are both compatible with I2C. Also, sending the sensor readings every hour will allow for lower power consumption and preserved storage space because the microcontroller can be put in sleep mode while not receiving data, and mold like conditions take longer periods of time to form.

<sup>3</sup> The sensors are expected to have a long life-time because they will not be easily accessable for repair inside of a wall. To ensure that they will have a longer life-time, the sensor will be protected in a way that harsh environmental conditions will not cause damage.

<sup>4</sup> In order for the sensor module to 

## Buildable Schematic
![SHT30 functional block diagram](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/104484972/f956cbd5-82c0-45e2-a615-ddc1c76373ab)

The picture above is a functional block diagram of the SHT30-DIS humidity and temperature sensor. The SHT30 has relative humidity and temperature sensors on board that send their readings to an analog to digital converter. The data is then passed on to be processed and linearized and also interfaced to provide digital output in the form of I2C communication [1].

![SHT30 typical application circuit](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/104484972/83353a31-a4a4-4d47-a92d-57a60be18f95)

The picture above is the typical application circuit for the SHT30-DIS humidity and temperature sensor [1]. The buildable schematic of the SHT30 hooked up to the ESP32-H2 will be shown below. The only pins required to be hooked up to the ESP32-H2 are the VDD (power), VSS (ground), SDA (Serial data), and SCL (Serial clock) pins. The remaining pins will be floating, with the necessary pins being configured in the code of the ESP32-H2 to allow for appropriate communication.

## Analysis


## Bill of Materials (BOM)
| Device | Quantity | Price Per Unit | Total Price |
| ------ | -------- | -------------- | ----------- |
| SHT30 Temperature and Humidity Sensor | 1 | $13.41 | $13.41 |

## References
[1] Sensirion, “NRESET - Adafruit Industries,” Datasheet SHT3x-DIS Humidity and Temperature Sensor, https://cdn-shop.adafruit.com/product-files/5064/5064_Sensirion_Humidity_Sensors_SHT3x_Datasheet_digital.pdf (accessed Oct. 31, 2023).

[2] A. Industries, “SHT30 temperature and humidity sensor - wired enclosed shell,” adafruit industries blog RSS, https://www.adafruit.com/product/5064?gad_source=1&amp;gclid=Cj0KCQjwqP2pBhDMARIsAJQ0CzqlgH_Vrp7xm4fY1QcRbdX0pUI5kT-38Ae2RRNolKE7GWGYOe8_RYYaAsEoEALw_wcB (accessed Oct. 31, 2023).

[3] Adam, “Mold Chart for Temperature and Humidity Monitors,” Stetten home services, https://energyhandyman.com/knowledge-library/mold-chart-for-temperature-and-humidity-monitors/ (accessed Sep. 28, 2023).
