# Fire Module Signoff

## Subsystem Function
The function of the fire module subsystem is to detect if a fire has ever occurred in a specific room in a house. The system will work by using an IR Temperature Sensor that is installed on the ceiling of a room that will be pointed toward the ground to detect room temperature to determine if a minimum of 176&deg; Fahrenheit has occurred. If the temperature has reached a critical temperature level, a signal will be sent from the transmitter (ESP32-H2) to the head unit warning the homeowner of a potential fire.

![firemodule](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/e768ff15-9812-4a0a-b979-6f65d493c14f)

## Constraints
| No. | Constraints | Origin |
| --- | ----------- | ------ |
|  1  | Shall be able to detect the minimum temperature of 176&deg; Fahrenheit. | Project Team |
|  2  | Shall send sensor data to the ESP32 every second. | Project Team |
|  3  | Shall send temperature data to the head unit if 176&deg; Fahrenheit has been reached. | Project Team |
|  4  | Shall not be a distraction to the homeowner. | All External Stakeholders, Ethics, & Team Supervisor |

<sup>1</sup> In order to determine if a fire has occurred in a room, the temperature sensor needs to be able to detect if the temperature has reached a minimum of 176&deg; Fahrenheit. This is because drywall in a house begins to deteriorate at 176&deg; Fahrenheit [1]. 

<sup>2</sup> In order to actively monitor the temperature of a room, the ESP32 will need to read the data of the sensor every second. If the temperature is recorded every second, the system will be able to detect if a fire has formed and warn the homeowner.

<sup>3</sup> If the ESP32 reads in the data from the temperature sensor and the temperature is 176&deg; Fahrenheit or higher, the ESP32 needs to send the data to the head unit so the head unit can warn the homeowner.

<sup>4</sup> One of the objectives of this system is for it to not be a distraction to the homeowner. According to homeowners, they do not want a system that is a distraction to their everyday lives.

## Buildable Schematic

![BlockDiagram](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/af28eb34-ada7-40e6-9d11-8862e578e8f3)

The picture shown above is the detailed block diagram of the MLX90614 IR Temperature Sensor. The MLX90614 is controlled by an internal state machine that controls the measurements and calculations of the object and ambient temperatures and does the post-processing to output the data [2].

#### Third-Party Buildable Schematic

![FireModule](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/d180af4c-1e48-4b2a-a8f1-ce3f089e9a83)

According to the datasheet, the temperature sensor uses an I2C communication protocol for the data output pins (SDA/PWM & SCL/Vz) [2]. The ESP32-H2 can interpret data that uses the I2C communication protocol, and every GPIO pin on the ESP32-H2 supports the I2C communication protocol [3]. The SDA/PWM pin is used to read and send data, and the SCL/Vz pin is used for the clock signal [2].

## Analysis

<sup>1</sup> Drywall will begin to have thermal damage at temperatures of 176&deg; Fahrenheit [1]. The MLX90614ESF-BAA temperature sensor is an infrared temperature sensor that has the capability to measure object temperatures from -70&deg; Fahrenheit to 716&deg; Fahrenheit [2]. So, this sensor will be able to detect the necessary 176&deg; Fahrenheit. 

The MLX90614 has a built-in ADC, as shown in the block diagram above, that converts the analog data to digital data before sending the data to the microcontroller [2]. Both the SDA/PWM and the SCL/Vz pins will be plugged into a 12-bit I2C-compatible pin on the ESP32-H2 which will allow for communication with the ESP32-H2. Both pins on the temperature sensor will output less than 12 bits, so the information will be able to be sent and interpreted properly [2][3]. 

<sup>2</sup> The ESP32-H2 is a microcontroller that can be coded to read how often it pulls data from the connected sensor [3]. Having enough storage to hold the data would not be a problem for the ESP32, as proved in the communication module.

<sup>3</sup> The ESP32-H2 can be coded to send the data to the head unit if 176&deg; Fahrenheit is read from the sensor [4]. The way the fire module is designed, it will send the data to the ESP32 every second, as stated above, and once the temperature value of 176&deg; Fahrenheit or higher is received, the ESP32 will send the data to the head unit.

<sup>4</sup> The fire module is going to be designed in a way that will not be too noticeable to a homeowner. The entire module will be put inside an enclosure that will be mounted on the top side of a ceiling panel so it will not be noticeable. The sensor will be placed at the bottom of the enclosure with a hole in the ceiling panel allowing the sensor to measure the temperature of a room.

## Bill of Materials (BOM)
| DEVICE | Quantity | Price Per Unit | Total Price |
| ------ | -------- | -------------- | ----------- |
|  HiLetgo GY-906 MLX90614ESF | 1 | $15.99 | $15.99 |

## References

[1] N. P. Team, “At what temperature will drywall ignite?,” NCERT POINT, https://www.ncertpoint.com/2022/01/at-what-temperature-will-drywall-ignite.html (accessed Oct. 24, 2023).

[2] DigiKey, “MLX90614ESF-BAA-000-SP Melexis Technologies NV - DigiKey,” Melexis Technologies NV MLX90614ESF-BAA-000-SP, https://www.digikey.com/en/products/detail/melexis-technologies-nv/MLX90614ESF-BAA-000-SP/5414793 (accessed Oct. 24, 2023). 

[3] Espressif Systems, “ESP32-H2 - Espressif Systems,” Adafruit, https://www.espressif.com/sites/default/files/documentation/esp32-h2_datasheet_en.pdf (accessed Oct. 24, 2023).

[4] Hiletgo GY-906 MLX90614ESF non-contact infrared temperature sensor ..., https://www.amazon.com/HiLetgo-MLX90614ESF-Non-contact-Infrared-Temperature/dp/B071VF2RWM (accessed Oct. 31, 2023). 
