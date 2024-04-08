The goal of experimentation is to measure the conformance to all specs and constraints and the attainment of all measures of success. Each team must be able to evaluate, in a non-trivial manner ($N>1$), attainment of all measures of success and all constraints enumerated in the signoffs.

After experimentation, it should be the case that the level of conformance to specs and constraints and attainment of the measures of success is well understood and the subsystems which need improvements are understood.

It is not required that the team be "done" with the project by the experimentation date (it is expected that there will be improvements to be made after this date). However, the conformance to all requirements and constraints must be measured by that date. This will typically require significant functionality as many measures of success require multiple subsystems. If errors in the initial design have caused some items to be unmeasurable by the experimentation date, the appropriate deduction (if any) will be considered on a case by case basis by the supervisor and instructor.

Regarding the design of the experiments, the experiment must sufficiently establish the value of whatever is being measured and the statistical significance of the value being measured. If the number of experiments, $N$, is equal to 1 then the results aren't meaningful.

## Requirements for the Deliverable

The deliverable for this assignment is a demonstration of the experiments (live or videoed) and a well organized markdown file in the project github. For each experiment, you must give the following in a well organized fashion: 
1. purpose of the experiment (what you intend to measure)
2. description of what you did (experimental procedure)
3. the expected result (prediction)
4. the number of trials 
5. a data table or graph of the results (whichever is appropriate) 
6. an interpretation of the data (interpreting the data requires the writer to explain what the results of the experiments mean and conclusions you draw)

### Module Constraints

| No. | Constraints | Origin |
| --- | **Head Unit** | ------ |
| --- | ----------- | ------ |
|  1  | The head unit shall know what sensor is sending data to it, the sensors location, and be able to differentiate from other sensors. | Team Supervisor & Project Team |
|  2  | The head unit shall be able to display and log active and historical data from sensors. | Project Team & Team Supervisor |
|  3  | The head unit shall be able to detect if the fire module temperature is at 176&#176; Fahrenheit or higher and display a warning. | Project Team |
|  4  | The head unit shall be able to receive data from the water module to display a warning if water is present and the total water depth. | Project Team |
|  5  | The head unit shall be able to receive data and follow OSHA standards for ammonia, propane, and carbon oxides (50 ppm, 1000 ppm, and 50 ppm respectively over an eight hour window). | Standards & Project Team |
|  6  | The head unit shall be able to interpret, from the received data, that mold could form if the humidity levels exceed 50% and temperatures range between 55&#176; and 85&#176; Fahrenheit for a minimum of two days. | Project Team |
| --- | **Communication** | ------ |
| --- | ---------------------------------------------------------------------------------------------- | ----------------------------------- |
|  1  | System shall not require an internet connection to work and communicate with the head unit and sensors | Home Owners, Insurance Agencies, & Team Supervisor |
|  2  | At least one sensor shall be placed within 200ft of the head unit. | Project Team |
|  3  | Sensors shall be within 32ft from each other for every sensor outside of 200ft of the head unit. | Project Team |
|  4  | Sensor communication shall send the sensor name, number, data type, and raw data to the head unit. | Project Team |
|  5  | ESP32 shall be able to send a minimum of 128 bits (2 packets) at a transmission rate of at most 250 Kbps on a 2.4 GHz frequency. | Project Team & Standards|
|  6  | The head unit shall, at minimum, receive data every 24 hours, when the data from the sensor reaches a critical level, or when the user requests the data. | Project Team |
| --- | **Flood** | ------ |
| --- | ---------------------------------------------------------------------------------------------- | ----------------------------------- |
|  1  | Sensor shall be able to detect if at least one inch of water is present in a room. | Project Team & Broader Implications |
|  2  | Sensors shall be able to detect water levels at various depths.| Project Team |
|  3  | Sensor shall send data to headunit in seconds if water is detected.| Project Team |
|  4  | Sensor shall be placed in areas flooding is most likely to occur. | Project Team |
|  5  | Sensor shall not be placed in areas where condensation can't easily form. | Broader Implications |
| --- | **Gas** | ------ |
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
| --- | **Fire** | ------ |
| --- | ----------- | ------ |
|  1  | Shall be able to detect the minimum temperature of 176&deg; Fahrenheit. | Project Team |
|  2  | Shall send sensor data to the ESP32 every second. | Project Team |
|  3  | Shall send temperature data to the head unit if 176&deg; Fahrenheit has been reached. | Project Team |
|  4  | Shall not be a distraction to the homeowner. | All External Stakeholders, Ethics, & Team Supervisor |
| --- | **Mold** | ------ |
| --- | ----------- | ------ |
|  1  | Shall be able to detect temperature ranges between 55&deg; F - 85&deg; F and humidity levels exceeding 50% RH. | Project Team |
|  2  | Shall be able to communicate through I2C protocol and send data once every hour to its local ESP32-H2 transmitter, then enter sleep mode until the next hour. | Project Team |
|  3  | Shall be protected and not exposed to harsh environmental conditions to prevent any damage to the sensor. | All External Stakeholders, Ethics, & Team Supervisor |
|  4  | Shall give precise temperature and humidity readings within 0.5&deg; F and 2% RH of the actual values, rounding to the nearest whole number to properly evaluate and determine if mold like conditions are present. | Project Team |
| --- | **Power** | ------ |
| --- | ----------- | ------ |
|  1  | System shall be primarily powered from the house's 120 Volt power supply. | Project Team |
|  2  | Shall have a backup power system that will allow the system to function in case of primary power outage for up to two continuous weeks. | Project Team & Team Supervisor |
|  3  | Shall fully function without regularly changing sensors or head unit batteries. | All External Stakeholders, & Team Supervisor |
