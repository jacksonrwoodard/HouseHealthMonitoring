# Mold Module Signoff

## Subsystem Function
The function of the mold module subsystem is to detect if mold is likely to grow within the surrounding environment of the sensor. The SHT30 Temperature and Humidity Sensor will gather temperature and humdity levels and send its respective data to an ESP32-H2 micro-controller. The mold module will send data to the ESP32-H2 every hour to allow for computations of the peak and average values.
![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/104484972/3401a3b6-74a1-49af-a090-dfe94abc742c)


## Constraints
| No. | Constraints | Origin |
| --- | ----------- | ------ |
|  1  | Shall be able to detect temperature ranges between 55&deg; F - 85&deg; F and humidity levels exceeding 50% RH to send to head unit. | Project Team |
|  2  | 

## Buildable Schematic
![SHT30 functional block diagram](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/104484972/f956cbd5-82c0-45e2-a615-ddc1c76373ab)


## Analysis

## Bill of Materials (BOM)
| Device | Quantity | Price Per Unit | Total Price |
| ------ | -------- | -------------- | ----------- |
| SHT30 Temperature and Humidity Sensor | 1 | $13.41 | $13.41 |

## References
[1] Sensirion, “NRESET - Adafruit Industries,” Datasheet SHT3x-DIS Humidity and Temperature Sensor, https://cdn-shop.adafruit.com/product-files/5064/5064_Sensirion_Humidity_Sensors_SHT3x_Datasheet_digital.pdf (accessed Oct. 31, 2023).

[2] A. Industries, “SHT30 temperature and humidity sensor - wired enclosed shell,” adafruit industries blog RSS, https://www.adafruit.com/product/5064?gad_source=1&amp;gclid=Cj0KCQjwqP2pBhDMARIsAJQ0CzqlgH_Vrp7xm4fY1QcRbdX0pUI5kT-38Ae2RRNolKE7GWGYOe8_RYYaAsEoEALw_wcB (accessed Oct. 31, 2023). 
