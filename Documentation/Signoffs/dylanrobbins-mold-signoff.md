# Mold Module Signoff

## Subsystem Function
The function of the mold module subsystem is to detect if mold is likely to grow within the surrounding environment of the sensor. The SHT30 Temperature and Humidity Sensor will gather temperature and humdity levels and send its respective data to an ESP32-H2 micro-controller. The mold module will send data to the ESP32-H2 every hour to allow for computations of the peak and average values.

![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/104484972/3401a3b6-74a1-49af-a090-dfe94abc742c)


## Constraints
| No. | Constraints | Origin |
| --- | ----------- | ------ |
|  1  | Shall be able to detect temperature ranges between 55&deg; F - 85&deg; F and humidity levels exceeding 50% RH. | Project Team |
|  2  | Shall be able to communicate through I2C protocol and send data once every hour to its local ESP32-H2 transmitter, then enter sleep mode until the next hour. | Project Team |
|  3  | Shall be protected and not exposed to harsh environmental conditions to prevent any damage to the sensor. | All External Stakeholders, Ethics, & Team Supervisor |
|  4  | Shall give precise temperature and humidity readings within 0.5&deg; F and 2% RH of the actual values, rounding to the nearest whole number to properly evaluate and determine if mold like conditions are present. | Project Team |

<sup>1</sup> The humidity and temperature sensors must be able to detect the specified levels because mold like conditions are highly probable when in those ranges. The highest probability of mold occurs when the temperature is 80&deg; F and the relative humidity level is 95% [3]. Other mold like conditions arise when temperatures are between 55&deg; F - 85&deg; F and humidity levels exceeding 50% RH.

<sup>2</sup> The sensor must be able to communicate to the ESP32-H2 microcontroller through I2C protocol because they are both compatible with I2C. Also, sending the sensor readings every hour will allow for lower power consumption and preserved storage space because the microcontroller can be put in sleep mode while not receiving data, and mold like conditions take longer periods of time to form.

<sup>3</sup> The sensors are expected to have a long life-time because they will not be easily accessable for repair inside of a wall. To ensure that they will have a longer life-time, the sensor will be protected in a way that harsh environmental conditions will not cause damage.

<sup>4</sup> In order for the sensor module to accurately determine if mold like conditions are present, the sensor must record precise measurements. The percent error of the readings must be very low so that the data is as accurate as possible. A slight error in the readings could possibly cause the system to display no active mold conditions when there actually is.

## Buildable Schematic
![SHT30 functional block diagram](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/104484972/f956cbd5-82c0-45e2-a615-ddc1c76373ab)

The picture above is a functional block diagram of the SHT30-DIS humidity and temperature sensor. The SHT30 has relative humidity and temperature sensors on board that send their readings to an analog to digital converter. The data is then passed on to be processed and linearized and also interfaced to provide digital output in the form of I2C communication [1].

![SHT30 typical application circuit](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/104484972/83353a31-a4a4-4d47-a92d-57a60be18f95)

The picture above is the typical application circuit for the SHT30-DIS humidity and temperature sensor [1]. The buildable schematic of the SHT30 hooked up to the ESP32-H2 will be shown below. The only pins required to be hooked up to the ESP32-H2 are the VDD (power), VSS (ground), SDA (Serial data), and SCL (Serial clock) pins. The remaining pins will be floating, with the necessary pins being configured in the code of the ESP32-H2 to allow for appropriate communication.

![Mold Module Schematic](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/104484972/72dc5b90-b7a2-4e37-96ee-ff3282232189)

The picture above is the third party buildable schematic for the mold module. The nRESET, ALERT, ADDR, and R pins can be left unconnected because the sensor will still be able to have full functionality. For this design, these pins are unnecessary for physical hook ups because they can each operate with their default settings through I2C communication. According to the datasheet, any GPIO pin can support I2C peripherals [2]. Therefore, SCL and SDA can be connected to the GPIO 1 and GPIO 2 pins and coded to be supported by the I2C protocol.

## Analysis
<sup>1</sup> According to the SHT30-DIS datasheet, the sensor can detect relative humidity levels from 0% - 100% RH and can detect temperature values between -40&deg; C - 125&deg; C [1]. Given these ranges, the SHT30-DIS will have no problem detecting the ranges of values that are probable to cause mold like conditions.

<sup>2</sup> The SHT30-DIS requires an I2C, 2 wire connection, communication protocol to communicate with any micro-controller [1]. The ESP32-H2 has many advanced peripherals, but it most importantly has two I2C bus interfaces that can be accessed on any GPIO pin [4]. Therefore, the ESP32-H2 can support I2C communication protocols and communicate with the SHT30 if the SDA (Serial data) and SCL (Serial Clock) pins are properly connected to the ESP32-H2. Since the SHT30 and ESP32-H2 are compatible with each other, the sensor can send its data to the microcontroller for computation and storage. The SHT30 is reliably capable of sending data across the SDA line at 400 kHz, but the I2C fast mode standards must be met. In I2C communication, one bit is transmitted each clock cycle and there are 400,000 clock cycles per second, so the SHT30 can transmit 400,000 bps to the ESP32-H2. Therefore, if 32 bits of data are being transmitted to the ESP32-H2 every hour, 16 bits for the temperature value and 16 bits for the humidity level, the SHT30 can transmit this data in 0.08 ms, and the ESP32-H2 can go into sleep mode until it is woken up in another hour. This will help with lower power consumption and preserve storage space.

Transmission Time = Number of Bits / Transmission Rate

Transmission Time = (32 bits) / (400,000 bps)

Transmission Time = 0.08 ms

<sup>3</sup> According to all external stakeholders and team supervisor, the system shall not be of visual hindrance to the home owner and require little to no maintenance during its lifespan. The design team is proposing to design the system to last up to 30 years. Therefore, the sensor shall not be exposed to any harsh environmental conditions that might damage it. The SHT30-DIS is designed and produced inside of an enclosed case much like weather-proof mesh sensor [2]. This will ensure that nothing, such as rodents or debris, will damage the sensor while still maintaining a stable, accurate reading of temperature and humidity levels. All of the external connections to the ESP32-H2 will also be within an enclosed case.

<sup>4</sup> To ensure that the mold module is reading and computing accurate numbers to determine if mold like conditions are met, the SHT30 must have low accuracy tolerances. According to the datasheet, the humidity sensor has a typical tolerance of +/- 2% RH and the temperature sensor has a typical tolerance of +/- 0.2&deg; C when levels are between 0&deg; C to 65&deg; C [1]. This sensor is more precise, more accurate, works in a bigger range of temperature/humidity, and is less expensive compared to other humdity and temperature senors, such as the DHT22/AM2302 [4]. With more accurate readings, the ESP32-H2 will be able to compute more accurate peak and average values to better trace mold conditions.

## Bill of Materials (BOM)
| Device | Quantity | Price Per Unit | Total Price |
| ------ | -------- | -------------- | ----------- |
| SHT30 Temperature and Humidity Sensor | 1 | $13.41 | $13.41 |

## References
[1] Sensirion, “NRESET - Adafruit Industries,” Datasheet SHT3x-DIS Humidity and Temperature Sensor, https://cdn-shop.adafruit.com/product-files/5064/5064_Sensirion_Humidity_Sensors_SHT3x_Datasheet_digital.pdf (accessed Oct. 31, 2023).

[2] A. Industries, “SHT30 temperature and humidity sensor - wired enclosed shell,” adafruit industries blog RSS, https://www.adafruit.com/product/5064?gad_source=1&amp;gclid=Cj0KCQjwqP2pBhDMARIsAJQ0CzqlgH_Vrp7xm4fY1QcRbdX0pUI5kT-38Ae2RRNolKE7GWGYOe8_RYYaAsEoEALw_wcB (accessed Oct. 31, 2023).

[3] Adam, “Mold Chart for Temperature and Humidity Monitors,” Stetten home services, https://energyhandyman.com/knowledge-library/mold-chart-for-temperature-and-humidity-monitors/ (accessed Sep. 28, 2023).

[4] Espressif Systems, “ESP32-H2 - Espressif Systems,” Adafruit, https://www.espressif.com/sites/default/files/documentation/esp32-h2_datasheet_en.pdf (accessed Oct. 24, 2023).
