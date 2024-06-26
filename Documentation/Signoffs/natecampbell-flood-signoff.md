# Flood Module Signoff

## Subsystem Function
The function of the flood subsystem is to detect the presence and level of water acting as an indicator of water damage within a home.
![watrer](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143025461/3825dc07-0522-412c-885b-1b09cc66138c)


#### Sensor Operation
![Alt Text](https://lastminuteengineers.com/wp-content/uploads/arduino/Water-Level-Sensor-Working.gif) [1]

The figure above shows how the water sensor's conductivity improves as it gets submerged in more water, lowering the resistance. When the sensor is exposed to less water, its conductivity decreases, thus resulting in higher resistance [1]. This sensor produces an output voltage that corresponds to its resistance, allowing the sensor to be calibrated to formulate a water level equation.




## Constraints
| No. | Constraints                                                                                    | Origin                              |
| --- | ---------------------------------------------------------------------------------------------- | ----------------------------------- |
|  1  | Sensor shall be able to detect if at least one inch of water is present in a room. | Project Team & Broader Implications |
|  2  | Sensors shall be able to detect water levels at various depths.| Project Team |
|  3  | Sensor shall send data to headunit in seconds if water is detected.| Project Team |
|  4  | Sensor shall be placed in areas flooding is most likely to occur. | Project Team |
|  5  | Sensor shall not be placed in areas where condensation can't easily form. | Broader Implications |


<sup>1</sup> 1-inch of water can cause thousands of dollars of damage [2]. Being able to detect a minimum of this depth would be essential in determining if a home has significant water damage. 

<sup>2</sup> Flood zones next to rivers and streams can average upwards of 3 feet in depth [3]. Being able to detect more than one inch of water could be valuable in determining how much water damage was done in a house.

<sup>3</sup> Knowing if water has touched the sensor could be a good indicator that a flood or leak has occurred. Being able to quickly send this data would be valuable in preventing a flood or leak from becoming catastrophic.

<sup>4</sup> Placing the sensors in the majority of the rooms and near the home's entrance will provide more accurate detection that water is present.

<sup>5</sup> Sensors placed in high condensation areas could lead to false positives, so preventing this is necessary.



## Buildable Schematic
#### Sensor Dimensions from Manufacturer
<img width="409" alt="Screenshot 2023-11-01 at 3 46 38 PM" src="https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143025461/6a6d9546-a1f0-43ea-845c-3c8a9a9523bb">
[4]

The figure shown above is the dimensions of 4965 water sensor.

#### Third-Party Buildable Schematic

<img width="727" alt="Screenshot 2023-11-01 at 5 41 44 PM" src="https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143025461/ac856427-aae6-4f39-89dd-7e41b464e54c">

The datasheet for the water sensor claims that it outputs an analog signal [4]. When fully submerged the analog value will be 3.3 volts because that is what is supplied by the esp-32.  Because of this it will need to be connected to the appropiate pin to process this data. According to the manufacturer, the GPIO1 pin on the ESP32 has a 12 bit analog to digital converter [5]. This will convert the output voltage from the sensor into a digital value of 0 to 4095 due to the 12 bits output from the converter. The sensor itself has 42 mm of sensing element that when divided by 4096 values equals about 10 micrometers per step. 

## Analysis
<sup>1</sup> The sensor itself has 42 mm or about 1.65 inches of measurable length. It could be placed at the bottom of a wall and measure a 1 inch depth easily.

<sup>2</sup> To measure depths beyond 1.65 inches, sensors can be placed at different heights on a wall. Knowing what height the sensor is at a coefficient can be derived to plug into the depth equation after calibrating the sensor.

<sup>3</sup> The sensor will be connected to the communication module powered by an ESP32 microcontroller. As stated in the communication sign-off, the microcontroller has a transmission rate of 250 Kbps and sends two packets of data at a time. The sensor will will output a max value of 4095 or 12 bits when converted. Even with the PAN ID and data type as mentioned in the communication module, one sensor reading will not take up the full 128 bits in the two-packet transmission. Since the ESP32 can send at a 250 Kbps rate, one reading will take less than a second to reach the head unit.

<sup>4</sup> Floodwater can enter a house through doors, windows, cracks in the foundation, sewer systems, and flood vents [6]. Placing the sensors near these areas could provide a more accurate response that flood damage has occurred. Placing multiple sensors at various heights in these locations can also provide the depth of water in the house. Assuming the home is level, the water from a flood will pool throughout the house, so placing a sensor at the base of every room will provide a more detailed view of where the water is in the house.

<sup>5</sup> Sensors that are placed in areas such as a bathroom where condensation is likely to occur will have to be placed with extra consideration to avoid false positives. Placing the sensors right outside the door of a bathroom or in a floor vent could prevent this condensation from building up while still allowing the system to detect if a flood has occurred in that room.

## Noise
<img width="757" alt="Screenshot 2024-02-06 at 12 18 05 PM" src="https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143025461/e617af58-481e-44cb-b73e-2fe445e65dac">

The figure above shows a simulation of the sensor. It features noise from the wall mutually inducted with the sensor to simulate a wall wire running alongside the sensor along with noise from the power supply of the sensor.

The mutual inductance was found by using the formula and specifications below[7]:
```math
d= 3×0.0254 = 0.0762 m
```

```math
rw​= 0.03205×0.0254 = 0.000814 m
```

```math
l= 6×0.0254 = 0.1524 m
```

```math
k = \frac{2 \times 4\pi \times 10^{-7} \times 0.1524}{3.14} \ln\left(\frac{0.0762}{0.000814}\right)^{-1} \text{ H/m}
```

```math
k = 1.3024 \times 10^{-9} \text{ H/m}
```
The winding values for the indcutors were chosen based on a help file from Keysight illustrating how to impose noise[8].

The ripple for the power supply was found in the datasheet for the power supply[9].

The 250 ohm resistor was chosen as that is what was measured from a similiar water sensor with resistance values from 250-750. The 250 ohm reading provides the simulation with more noise giving the worst case scenario. 

<img width="544" alt="Screenshot 2024-02-06 at 12 43 32 PM" src="https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143025461/fe900648-e8fc-4b46-bc87-c7d765c9497b">

The image above shows the noise before the filter being close to 200 mV.

<img width="710" alt="Screenshot 2024-02-06 at 12 49 51 PM" src="https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143025461/0698dde2-2796-49ad-95f7-fda999a9b38f">

<img width="548" alt="Screenshot 2024-02-06 at 12 50 26 PM" src="https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143025461/aeb16a26-3b61-4320-ac1d-9fdd753e29bb">

After filtering the noise is reduced to approximately 0.0008 volts. The RC values were chosen based on the filtering values for 60 Hz [10].

As for the resolution, testing the sensor yielded the output voltage to be .45 volts with miniscule submergence in water and .85 volts when fully submerged. This gives .4 volts of range. Because the ESP-32 operates on a 3.3 volts, the resolution will need to scaled down to use the .4 volt range. this can be found by 

3.3/4096= 0.00081 volts per step in normal 3.3 volt range

.4/.00081 ≈ 494 steps in the .4 volt range

.4/42 = 0.0095 volts per mm

494/42 = 11.76 steps per mm, due to the sensor having 42 mm of sensing element

.0095/11.76 ≈ 0.0008 volts per step

The effective noise reduction achieved by the filter will allow for better sensor accuracy, bringing the noise down to approximately 0.0008 volts, which is roughly equivalent to the 0.0008 volts per step. This single step of noise corresponds to an inaccuracy of about 0.085 mm (or 0.003 inches). Because floods are usually several inches and multiple sensors would be placed in the home at various heights, 0.003 inches is negligible to the accuracy of the sensor.

## Bill of Materials (BOM)
| DEVICE | Quantity | Price Per Unit | Total Price | Overall Total |
| ------ | -------- | -------------- | ----------- | ----- |
| 4965 Water Sensor | 1 | $1.95 | $1.95 | $1.95 |

## References
[1] Last Minute Engineers, “In-depth: How water level sensor works and interface it with Arduino,” Last Minute Engineers, https://lastminuteengineers.com/water-level-sensor-arduino-tutorial/ (accessed Nov. 1, 2023). 

[2] “The cost of flooding,” | Flood Damage Cost Calculator, https://www.floodsmart.gov/cost-flooding#:~:text=Just%201%20inch%20of%20water,a%20flood%20could%20cost%20you.&amp;text=Estimates%20based%20on%20national%20FEMA%20flood%20loss%20tables%20of%20cash%20value%20loss. (accessed Nov. 1, 2023). 

[3] “Zone ao,” FEMA.gov, https://www.fema.gov/glossary/zona-ao#:~:text=River%20or%20stream%20flood%20hazard,from%201%20to%203%20feet. (accessed Nov. 1, 2023). 

[4] 123 model (1) - adafruit industries, https://cdn-shop.adafruit.com/product-files/4965/Datasheet.pdf (accessed Nov. 1, 2023). 

[5] “Esp32-H2-DevKitM-1,” esp, https://docs.espressif.com/projects/espressif-esp-dev-kits/en/latest/esp32h2/esp32-h2-devkitm-1/user_guide.html (accessed Nov. 9, 2023). 

[6] “What are the effects of a flood on your home?,” PuroClean, https://www.puroclean.com/blog/effects-of-a-flood-home/ (accessed Nov. 2, 2023). 

[7] “Parallel wire inductance calculator - engineering calculators & tools,” All About Circuits, https://www.allaboutcircuits.com/tools/parallel-wire-inductance-calculator/ (accessed Feb. 6, 2024). 

[8] “How can noise be superimposed on the output of a DC power supply?,” How can noise be superimposed on the output of a dc power supply? - Technical Support Knowledge Center Open, https://edadocs.software.keysight.com/kkbopen/how-can-noise-be-superimposed-on-the-output-of-a-dc-power-supply-589744645.html (accessed Feb. 6, 2024).

[9] Raspberry pi 15W USB-C power supply, https://datasheets.raspberrypi.com/power-supply/15w-usb-c-power-supply-product-brief.pdf (accessed Feb. 6, 2024).

[10] “Low pass/high pass filter calculator,” RC, RL, LC Passive Filter Calculator | DigiKey Electronics, https://www.digikey.com/en/resources/conversion-calculators/conversion-calculator-low-pass-and-high-pass-filter?utm_adgroup=&utm_source=google&utm_medium=cpc&utm_campaign=PMax_DK%2BProduct_Product+Categories+-+Top+15&utm_term=&utm_content=&utm_id=go_cmp-19646629144_adg-_ad-__dev-c_ext-_prd-_sig-Cj0KCQiAzoeuBhDqARIsAMdH14GOfln4oUhfKv9-p9uDzAoSUsxbda0ytGGlZlNq9cnYGRHXUEetfCUaAvf_EALw_wcB&gad_source=1&gclid=Cj0KCQiAzoeuBhDqARIsAMdH14GOfln4oUhfKv9-p9uDzAoSUsxbda0ytGGlZlNq9cnYGRHXUEetfCUaAvf_EALw_wcB (accessed Feb. 6, 2024). 
