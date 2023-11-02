# Gas Module Signoff

## Subsystem Function
The gas module plays a critical role in ensuring safety and well-being by detecting three gases that can be found in homes: propane, carbon monoxide, and ammonia. The module collects data on gas concentrations and wirelessly transmits it to the head unit through our wireless communication module. At the head unit, the data undergoes analysis to ensure compliance with OSHA standards for an eight-hour monitoring window. This process provides real-time data and alerts about gas concentrations, helping the system respond to and manage safety or environmental concerns.

The module is a part of our overall system, seamlessly working to preserve the environment of the house and comply with regulatory standards. The module’s performance is essential to maintaining a safe and healthy living environment. Any malfunction of the gas sensor module could result in potential risks, such as gas leaks or air quality degradation. Therefore, its function is crucial in achieving the system's primary goal of providing accurate, timely, and actionable gas-related information while adhering to established safety standards and guidelines.

![Gas Module Block diagram](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143034071/c0c971c0-ab34-4693-a6ac-00cb6879f5f2)


## Constraints
| No. | Constraints                                                                                    | Origin                              |
| --- | ---------------------------------------------------------------------------------------------- | ----------------------------------- |
|  1  | The Gas module shall be able to detect ammonia, propane, and carbon oxide. | Project  Team, Insurance Agencies|
|  2  | Head unit shall receive data from the gas module and follow OSHA standards for ammonia, propane, and carbon oxides (50 ppm, 1000 ppm, and 50 ppm respectively over an eight-hour window)| OSHA |
|  3  | The Gas module shall be installed in a central location outside each sleeping area or in the immediate vicinity of the bedrooms, at the maximum of 20 feet | NFPA |
|  4  | The Gas module shall be placed as close as possible to potential gas leak spots | Project Team, Existing Products |
|  5  | The Gas module shall be orientated to where the target gas vapours tend to rise or fall | Project Team, Existing Produts |
|  6  | The Gas module shall not be placed near entrances/disturbances or fresh air vents where concentrations can be diluted | Project Team, Existing Products |
|  7  | The Gas module shall not be placed in bathrooms, garages, kitchens, furnace rooms, extremely dusty or dirty areas | Project Team, Existing Products |
|  8  | The Gas module shall not be placed in areas of the house enviroment where it is colder than -10°C or hotter than 50°C | Manufacturer |
|  9  | The Gas module shall not be placed in areas of the house enviroment where the humidity is more than 95% | Manufacturer |
|  10 | The Gas module shall use analog communication every second, in the range of 0-5V, that will be connected to a ADC on the ESP32-H2 | Project Team |

<sup>1</sup> These are the three specific gases perserve home pro set out to be able to detect due to the common gases causing poisoning at the home. [1]

<sup>2</sup> In order to abide by OSHA standards, these are the gas concentrations perserve home pro will be detecting for an eight hour monitoring window. [2]

<sup>3</sup> In accordance to NFPA standards, perserve home pro will adhere to the located specified in the third constraint. [3-4]

<sup>4</sup> For perserve home pro to best maximize the potential in finding gas leaks the gas module will be placed where gas piping is being feed into. [5]

<sup>5</sup> For the gases that are being targeted, they will be orientated either near the ceiling or near the floor because the each gas is heavier or lighter than air and either flow up or down. [5]

<sup>6</sup> From looking at exisitng products installation manuals, perserve home pro will not be placing the gas sensors where their is a potential disturbance that will effect the sensing of the sensor.[3-5]

<sup>7</sup> From looking at existing products installation manuals, perserve home pro will not place sensors in environments where there will be false positives for the sensor from other environments.[4]

<sup>8</sup> To meet the manufacturers work environment, the sensors will not be placed in the specified temperature range in order to keep functionality.[6-7]

<sup>9</sup> To meet the manufacturers work environment, the sensors will not be placed in the specified temperature range in order to keep functionality.[6-7]

<sup>10</sup> For perserve home pro to keep a coverage of a house's environment to the three target gases, the gas module will need to be sending data every second in order to actively protect homeowner's from potential threats.


## Buildable Schematic  

![Screenshot 2023-11-01 145628](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143034071/59f374f8-044c-44ba-af4c-2bbdb6955dba)

Figure 1. This is the schematic of the MQ-9 sensor that is being used on the SRAQ-G014, this sensor targets propane and carbon monoxide. [9]

![Screenshot 2023-11-01 150119](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143034071/9e32d46a-e733-4559-89af-41e114e904ec)

Figure 2. This is the schematic of the MQ-135 sensor that is being used on the SRAQ-G016, this sensor targets ammonia. [8]

#### Third-Party Buildable Schematic

![Gas module](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/143034071/781086de-2ab5-424b-b295-1be82180a822)
Figure 3. This the wiring schematic of how the gas sensors will be connected to the each respective ESP32-H2

## Analysis

<sup>1</sup> In order to meet constraints 1 and 2, there will be a need for two sensors in order to detect the gases perserve home pro is targeting. The SRAQ-G014 will be used to detect the prescence and concentration of flammable gases (Propane) and carbon monoxide. The device features the MQ-9 sensing element that is highly sensitivity to those gases mentioned and has a detection range of 50-10000 ppm for propane and 10-1000 ppm for carbon monoxide.[6] This range is crucial in order to meet the standards set by OSHA for the eight hour monitoring window. The MQ-9 technical parameters from the datasheet shows that it will have a "burn in" time for more than 30 minutes that allows for calibration of meeting the specified ppm ranges that will be done by introducing the gases to the sensor and calibrating the sensor using the adjusting knob (potentiometer) to find the range specified for propane and carbon monoxide.[6] The SRAQ-G016 is very similar to the SRAQ-G014 but has the MQ-135 sensing element that is highly sensitive to ammonia. The detection range is from 10-1000ppm and that is sufficient to meeting our OSHA standard for ammonia.[7] The SRAQ-G016 will be calibrated and tested just like the SRAQ-G014 in order to meet the given protocals for ammonia. 

<sup>2</sup> To meet constraint 3, perserve home pro will be mounting the gas module no further than 20 feet from a location that is central to the surrounding vicinitys of bedrooms. This is a requirement that NFPA has set on carbon monoxide detectors and will be adressed by perserve home pro. Also, from already existing carbon monoxide alarms, the installation manuals address that if a home has a bedroom hallway of 40 feet then a module will be needed at each end to make up for 40 feet. [3] [4]

<sup>3</sup> For constraints 4 through 7, perserve home pro looked at alredy existing solutions from gas sensor manufacturers and developers in order to best suit the location of the gas module. The consensus for constraints 4 and 5 was to place the modules prevelant for leaks or sources that are prone to leak.[5] This would be the piping from gas sources to appliances (if homeowners have that feature for their house) so perserve home pro would detect propane accurately and would need to placed near the floor because propane is heavier than air and will naturally flow to the floor.[5] [11] The carbon monoxide spreads evenly through the air and was adressed previously on the location so perserve home pro must have that location meet.[3-4] [10] Ammonia is a lighter than air so will naturally want to float upwards so that module will be placed near ceilings to be in the environment where ammonia resides.[12] The constraints 6 and 7 will be meet for our selection of location in order to best place our module in a environment where accurate readings can be conducted without external environments affecting them.[3-5]

<sup>4</sup> Also, perserve home pro will need to meet constraints 8 and 9 given from the manufacturers datasheet in order to have proper work environments for the sensor. If those constraints are not meet from perserve home pro then the sensor will not work properly and potentially lead to harmful affects to homeowners.[6-7]

<sup>5</sup> Lastly, 

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
