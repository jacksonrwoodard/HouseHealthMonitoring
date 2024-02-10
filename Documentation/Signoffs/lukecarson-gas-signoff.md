# Gas Module Signoff

## Subsystem Function
The gas module detects three gases that can be found in homes: propane, carbon monoxide, and ammonia. The module collects data on gas concentrations and wirelessly transmits it to the head unit through our wireless communication module. At the head unit, the data undergoes analysis to ensure compliance with OSHA standards for an eight-hour monitoring window. This process provides real-time data and alerts about gas concentrations, helping the system respond to and manage safety or environmental concerns.

![Gas Module Block diagram](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143034071/c0c971c0-ab34-4693-a6ac-00cb6879f5f2)


## Constraints
| No. | Constraints                                                                                    | Origin                              |
| --- | ---------------------------------------------------------------------------------------------- | ----------------------------------- |
|  1  | The Gas module shall be able to detect ammonia, propane, and carbon oxide. | Project  Team, Insurance Agencies|
|  2  | Head unit shall receive data from the gas module and follow OSHA standards for ammonia, propane, and carbon oxides (50 ppm, 1000 ppm, and 50 ppm respectively over an eight-hour window)| OSHA |
|  3  | The Gas module shall send data to headunit every second if the targeted gases are detected | Project Team |
|  4  | The Gas module shall be installed in a central location outside each sleeping area or in the immediate vicinity of the bedrooms, at the maximum of 20 feet | NFPA |
|  5  | The Gas module shall be placed as close as possible to potential gas leak spots | Project Team, Existing Products |
|  6  | The Gas module shall be orientated to where the target gas vapours tend to rise or fall | Project Team, Existing Produts |
|  7  | The Gas module shall not be placed near entrances/disturbances or fresh air vents where concentrations can be diluted | Project Team, Existing Products |
|  8  | The Gas module shall not be placed in bathrooms, garages, kitchens, furnace rooms, extremely dusty or dirty areas | Project Team, Existing Products |
|  9  | The Gas module shall not be placed in areas of the house enviroment where it is colder than -10°C or hotter than 50°C | Manufacturer |
|  10  | The Gas module shall not be placed in areas of the house enviroment where the humidity is more than 95% | Manufacturer |
|  11  | The Gas module shall be protected from unwanted variation of sensor readings due to noise | Project Team |

<sup>1</sup> Preserve Home Pro aims to detect three specific gases commonly known for causing poisoning at home. [1]

<sup>2</sup> To comply with OSHA standards, the gas concentrations monitored by Preserve Home Pro will be checked for an eight-hour period. [2]

<sup>3</sup> Preserve Home Pro will ensure fast response times if there is a adequate amount of gas presence specified in the other constraints in order to prevent harmful effects to the customer.

<sup>4</sup> Preserve Home Pro will follow the guidelines specified in the fourth constraint as per the NFPA standards. [3-4]

<sup>5</sup> To maximize the potential in detecting gas leaks, the gas module will be installed where gas piping is being fed into. [5]

<sup>6</sup> The targeted gases will be placed either near the ceiling or near the floor since each gas is either heavier or lighter than air and flows up or down. [5]

<sup>7</sup> Based on existing product installation manuals, Preserve Home Pro will avoid placing gas sensors in areas where there is a potential disturbance that could affect sensor detection. [3-5]

<sup>8</sup> Based on existing product installation manuals, Preserve Home Pro will avoid placing sensors in environments where there is a likelihood of false positives from other sources. [4]

<sup>9</sup> To meet the manufacturer's work environment, the sensors will not be placed within the specified temperature range.in order to keep functionality for constraints 9 and 10. [6-7]

<sup>10</sup> In order to provide reliable, accurate, and usable data the team will need to implement filtering in order to provide stable sensor readings. [16]

## Buildable Schematic  

![Screenshot 2023-11-01 145628](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143034071/59f374f8-044c-44ba-af4c-2bbdb6955dba)

Figure 1. This is the schematic of the MQ-9 sensor that is being used on the SRAQ-G014, this sensor targets propane and carbon monoxide. [9]

![Screenshot 2023-11-01 150119](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143034071/9e32d46a-e733-4559-89af-41e114e904ec)

Figure 2. This is the schematic of the MQ-135 sensor that is being used on the SRAQ-G016, this sensor targets ammonia. [8]

#### Third-Party Buildable Schematic

![Gas module](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143034071/781086de-2ab5-424b-b295-1be82180a822)
Figure 3. This the wiring schematic of how the gas sensors will be connected to the each respective ESP32-H2

## Analysis

<sup>1</sup> To meet constraints 1 and 2, there will be a need for two sensors to detect the gases Preserve Home Pro is targeting. The SRAQ-G014 will detect the presence and concentration of flammable gases (Propane) and carbon monoxide. The device features the MQ-9 sensing element that is highly sensitive to propane and carbon monoxide and has a detection range of 50-10000 ppm for propane and 10-1000 ppm for carbon monoxide.[6] The SRAQ-G016 is like the SRAQ-G014 but features the MQ-135 sensor whose elements are highly sensitive to ammonia and the detection range is from 10-1000ppm.[7] These ranges are crucial to meet the standards set by OSHA for the eight-hour monitoring window.

The gas module technical parameters show that the module will need a one-time 24-48 hour burn-in time for the sensors to be correctly calibrated and accurate. After that, the pre-heat time will be 30 minutes for the gas module to be calibrated and then the sensor will start collecting accurate data and be checked every second.[6-7]

Since the gas module detects and measures the concentrations of the specified gas ranges using analog voltage levels (within 0-5V), the analog output pins from the gas module will be connected to a 12-bit ADC pin on the ESP32-H2 so the microcontroller can collect and process into meaningful concentration data.[13] The ESP ADC takes data from the range of 0-3.3V, this means Preserve Home Pro will have to incorporate of voltage divider with the gas sensors in order to bring the voltage levels down from 5V to 3.3V in order to record accurate data and not lose any.

Now knowing this, we can use the binary base equation **2<sup>n</sup>**, where n is the number of bits the ADC is using which is 12 bits.[13] From the equation below, the ADC provides 4,096 discrete values within the 0-3.3V range, enabling fine voltage distinctions required for the calculation of ppm measurements. [13-15]

```math
Resolution = 2^n = 2^{12} = 4,096 steps
```

To be able to detect the smallest step size in ppm the ADC provides 4,096 unique values and Preserve Home Pro needs to detect the ppm range of 10-10000ppm for the gas targets.[6-7] [13] 

From the equation below, we can calculate smallest possible difference in values that can be measured compared to a scale of 10 to 10,000. This is calculated by dividing 9,990 (or the range between 10-10,000ppm) by the number of steps, or 9,990/steps. [15]

```math
Smallest-step = \frac{(Maximum-ppm)} {(Resolution)} = \frac{(9,990)} {(4,096)} = 2.439 ppm/step
```

<sup>2</sup> For constraint 3, the sensor will be connected to the communication module powered by an ESP32 microcontroller. As stated in the communication sign-off, the microcontroller has a transmission rate of 250 Kbps and sends two packets of data at a time. The sensor will will output a max value of 4096 or 12 bits when converted. Even with the PAN ID and data type as mentioned in the communication module, one sensor reading will not take up the full 128 bits in the two-packet transmission. Since the ESP32 can send at a 250 Kbps rate, one reading will take less than a second to reach the head unit.

<sup>3</sup> To meet constraint 4, Preserve Home Pro will be mounting the gas module no further than 20 feet from a location that is central to the surrounding vicinities of bedrooms. This is a requirement that NFPA has set on carbon monoxide detectors and will be addressed. Also, from already existing carbon monoxide alarms, the installation manuals address that if a home has a bedroom hallway of 40 feet then a module will be needed at each end to make up for 40 feet. [3] [4]

<sup>4</sup> For constraints 5 through 8, Preserve Home Pro looked at existing solutions from gas sensor manufacturers and developers to best suit the location of the gas module. The consensus for constraints 4 and 5 was to place the modules where leaks are prevalent or where gas sources are prone to leak.[5] This would include piping from gas sources to appliances (if homeowners have that feature for their house) so that Preserve Home Pro could detect propane accurately. The module for propane detection needs to be placed near the floor because propane is heavier than air and will naturally flow to the floor. [5] [11] The carbon monoxide spreads evenly through the air, and its location was addressed previously, so Preserve Home Pro must meet that location. [3-4] [10] Ammonia is lighter than air and will naturally want to float upwards, so the module will be placed near ceilings to be in the environment where ammonia resides. [12] For constraints 6 and 7, our selection of location will be the best place to conduct accurate readings without external environments affecting them. [3-5]

<sup>5</sup> According to the manufacturer's datasheet, Preserve Home Pro needs to meet constraints 9 and 10 to provide suitable work environments for the sensor. If the constraints are not met, the sensor will not function correctly and may potentially cause harm to homeowners. [6-7]

<sup>6</sup> Lastly for constraint 11, anytime when sensor measurements are taking place that data needs to be accurate and reliable. Preserve Home Pro has addressed the concerning attention of noise interference in the area of the system. A LTspice simulation was conducted in order to model the environment of our system and be able to verify the noise implemented on the system and to make sure the noise is not affecting the data involving measurements.

## Noise Simulation

![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143034071/e091db1c-9e8b-45e2-82b3-53d51c8fcc6f)
Figure 4.The LTspice circuit of two coupled parallel wires next to each other.

From the figure above, this is modeling the system with wall power wires running next to the sensor wiring. The circuit on the left is the AC wiring of the house with 120V at 60 Hz frequency being modeled. This is then coupled together using inductors with the secondary circuit which is the sensor circuit. The turns ratio was selected by a regarded source on how to model noise source that gave a range of 500-1000 turns to 1 for noise simulation [17]. The choice of the resistor values was from the datasheets of the gas sensors that shows the sensing resistor is from this range due to various gas concentrations [6-7]. The coupling coefficent was calculated by using a derivation of the mutual inductance of two parallel wires while using the specifications of 14 AWG that is commonly used for wiring residential houses wall sockets as seen below [18-19]. 

distance between wires (d), radius of the wire (rw), and length of the wire of how long they run together (l). These calculations are taken from inches to meters in order to match the units, 1 inch = 0.0254 meters

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

![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143034071/79e9de13-0b8f-4022-a8d8-03d85eecee42)

Figure 5. This is the ouputs of the simulation with the green sinusoid being the 2k ohm resistor and the 20k ohm resistor being the blue, hypothetically the 2k ohm resistor would be the most noise as seeing the larger sinusoid produced. The nosie being about 40mV as seen in the figure.

![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143034071/80fe956f-3d1c-4251-9f92-490f9948aac3)

Figure 6. This is the schematic where a RC filter is introduced, this is useful in order to filter out the high frequencies and only capture the signal preserve home pro needs for accurate measuring.

The secondary circuit is modeled using a sinusoidal voltage source with a DC offset of 3.3V which is the ADC voltage range of the microcontroller being used in order to take the data and make it useful for the customer to understand, then factoring in ripple voltage from the wall wart which is specified 120mVpp on the datasheet [20]. 

![image](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143034071/237fb844-b49c-41f9-874f-5611858bb2eb)
Figure 8. The output simulation taken from figure 6 LTspice schematic on the secondary side after the filter.

After the filtering, looking at the green sinusoid, a measurement of 110 uVpp is found which is reduced from the 40mV seen in figure 5. 

The Voltage resolution is found to be 3.3V/4096 = 0.00081 V/step or 0.8mV/step

The PPM resolution was 2.439 ppm/step

To calculate the value representing the smallest detectable change in gas concentration per unit change in voltage, you can simply multiply the voltage resolution by the ppm resolution

Sensitivity = 0.8mV×2.439ppm = 1.95 ppm/mV

The RC filtering shows that the noise being reduced to 110 uV would be negligible until the noise got to that 0.8mV or 800uV mark then there would be a change in ppm which would result in giving false readings or measurements of the gas module. Therefore, with this filter in place there will be better sensor or measurement accuracy creating a reliable gas monitoring system. 

## Bill of Materials
| DEVICE | Quantity | Price Per Unit | Total Price |
| ------ | -------- | -------------- | ----------- |
|  SRAQ-G014 | 1 | $7.19 | $7.19 |
|  SRAQ-G016 | 1 | $18.99 | $18.99 |
|  |  |  | $26.18 |

## References

[1] I. Maloca, J. Macan, V. Varnai, and R. Turk, “[household gas poisonings],” Arhiv za higijenu rada i toksikologiju, https://pubmed.ncbi.nlm.nih.gov/17265686/ (accessed Nov. 1, 2023). 

[2] OSHA, “1910.1000 table Z-1 - Table Z-1 limits for Air Contaminants,” Occupational Safety and Health Administration, https://www.osha.gov/laws-regs/regulations/standardnumber/1910/1910.1000TABLEZ1 (accessed Oct. 3, 2023).

[3] F. Alert, “Where to place smoke alarms, CO detectors and fire extinguishers in your home,” Where to Place Smoke Alarms, CO Detectors &amp; Fire Extinguishers, https://www.firstalert.com/us/en/safetycorner/do-you-know-where-to-place-your-fire-safety-devices/ (accessed Nov. 1, 2023). 

[4] Lowes, Regulatory information for CO alarms - lowes holiday, https://pdf.lowes.com/productdocuments/b416e051-dfbb-48d5-9e75-0cc2b15ea775/43462394.pdf (accessed Nov. 1, 2023). 

[5] C. Allcock, “Where to place your fixed gas sensors,” DSA Suppliers, https://dsasuppliers.com/blog/where-to-place-your-fixed-gas-sensors/#:~:text=Place%20sensors%20as%20close%20as%20possible%20to%20potential,sensors%20relative%20to%20the%20target%20gases%20vapour%20density (accessed Nov. 1, 2023). 

[6] L. Com, L, https://www.l-com.com/flammable-gas-sensor-mq9%3B-co-flammable-gas-analog-ttl-output-sraq-g014?gclid=CjwKCAjwp8OpBhAFEiwAG7NaEk1WaGOvZfrDJBcsirTAcMBFrEK2e4DYIgXLhRn1yB7nGe5K9ezilRoC62gQAvD_BwE (accessed Nov. 1, 2023). 

[7] L. Com, L, https://www.l-com.com/ammonia-nh3-sensormq135-sraq-g016?gclid=CjwKCAjwp8OpBhAFEiwAG7NaErm3UWXtUdyUrSZbj9WfhZF-R8SvJ0-PjiYGTYgoy0oFk4063ynE3xoCHncQAvD_BwE (accessed Nov. 1, 2023). 

[8] T. K. Hareendran, “How to use MQ-135 Gas Sensor,” Codrey Electronics, https://www.codrey.com/electronic-circuits/how-to-use-mq-135-gas-sensor/ (accessed Nov. 1, 2023). 

[9] tlfong01, “MQ9 learning notes,” tlfong01.blog, https://tlfong01.blog/2019/11/03/mq9-learning-notes/ (accessed Nov. 1, 2023). 

[10] “Why carbon monoxide (CO) alarms don’t need to be installed near the floor,” Google Nest Help, https://support.google.com/googlenest/answer/9259392?hl=en (accessed Nov. 1, 2023). 

[11] “Where should a fixed gas detector sensor be mounted?,” RKI, https://www.rkiinstruments.com/blog/where-should-a-fixed-gas-detector-sensor-be-mounted/ (accessed Nov. 1, 2023). 

[12] Sensidyne, “(NH3) ammonia gas detection,” Sensidyne, https://www.sensidynegasdetection.com/support/application-support/ammonia-gas-detection.php (accessed Nov. 1, 2023). 

[13] Espressif Systems, “ESP32-H2 - Espressif Systems,” Adafruit, https://www.espressif.com/sites/default/files/documentation/esp32-h2_datasheet_en.pdf (accessed Oct. 24, 2023).

[14] I. S. U. Share, “Binary world,” Binary World, https://loadingtech.blogspot.com/2012/07/binary-world.html (accessed Nov. 28, 2023). 

[15] S. One, “Bit to measurement resolution converter,” SensorsONE, https://www.sensorsone.com/bit-to-measurement-resolution-converter/#parts (accessed Nov. 28, 2023). 

[16] B. Murphy, “How do you deal with Sensor Data Noise, outliers, and missing values?,” Sensor Data Cleaning: Noise, Outliers, and Missing Values, https://www.linkedin.com/advice/0/how-do-you-deal-sensor-data-noise-outliers-missing#:~:text=Noise%20can%20be%20caused%20by,the%20data%20analysis%20and%20modeling. (accessed Jan. 30, 2024). 

[17] Wideband power amplifier illustration | keysight, https://www.keysight.com/us/en/assets/9921-02529/help-files/5306PPD-FAQ-42.pdf (accessed Jan. 30, 2024).

[18] G. Lee, Guy LeeGuy Lee 16311 gold badge11 silver badge1313 bronze badges, and analogsystemsrfanalogsystemsrf 34k22 gold badges1919 silver badges4646 bronze badges, “Calculating mutual inductance in parallel wires,” Electrical Engineering Stack Exchange, https://electronics.stackexchange.com/questions/304211/calculating-mutual-inductance-in-parallel-wires#:~:text=L%20%3D%20%28%CE%BCo%20%E2%88%97%20Length%20%CF%80%29%20%E2%88%97%20ln%28separation,the%20center_to_center%20distance%2C%20to%20be%20greater%20than%202%2Aradius (accessed Jan. 30, 2024).  

[19] T. Thiele, “A guide to electrical wire sizes,” The Spruce, https://www.thespruce.com/electrical-wire-sizes-1152851 (accessed Jan. 30, 2024). 

[20] Chicago Electronic Distributors, “Raspberry pi 4 power supply in white,” Chicago Electronic Distributors, https://chicagodist.com/products/raspberry-pi-4-psu-us-white?src=raspberrypi (accessed Jan. 30, 2024). 
