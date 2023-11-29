# Preserve Home Pro (PHP)
## Executive Summary

Houses face many types of issues like gas leaks, fires, floods, and mold, which cause damage to the house leading to a decrease in value. Unlike a smartphone or a modern car, current house constructions lack a mechanism to detect and monitor this information. This information, such as knowing if water damage has occurred, could improve the value of the house by proving that issues have not occurred or were taken care of quickly by the homeowner. To detect and monitor all of these problems, this project proposes a collection of sensors and a head unit, called Preserve Home Pro. The goal of the system is to measure, record, and display important active and historical data, giving a homeowner valuable information to help maintain and protect the value of their home. The Preserve Home Pro will be designed as a semi-permanent system that will last for up to thirty years. The system will also communicate information through a closed network without requiring the Internet. Combining these concepts, this project proposes an advanced solution to house health monitoring.


## Capabilities

Detailed capabilities for this project are described in the [Signoffs](https://github.com/jacksonrwoodard/HouseHealthMonitoring/tree/main/Documentation/Signoffs) section of this repository. Each signoff includes the function of the subsystem, constraints, buildable schematics, analysis, and bill of materials. The following bullet points detail the current expectations of the house health monitoring system.
- The Head Unit subsystem expects to receive serial data from the communication receiver and implement a user friendly interface that displays historical and active data from each sensor module.
- The Communication subsystem will allow the sensors' microcontroller to send data wirelessly to the head unit's microcontroller through the Zigbee protocol.
- The Power subsystem will supply power functionality for each subsystem. Each subsystem will be hard-wired into the house with each sensor module having an uninteruptable power supply (UPS) to power them when the electricty in the home goes out. All head unit and communication functionality will be disabled while the power is out to ensure maximum battery lifetime.
- The Mold subsystem will read temperature and humidity levels at its respective sensor in order to detect if mold like conditions are present in a home.
- The Fire subsytem will read specific temperature levels to detect whether a fire is present or not in a room.
- The Gas subsystem will read parts per million (ppm) levels to determine if gas is present in a room and specifiy which gas it is.
- The Flood subsytem will read water levels based on resistivity to detect any amounts of water present in the area.
- Each sensor module will serially send data to a local microcontroller so that it can send the data to the head unit for computation and storage.

## Salient Outcomes

Projects often have some outcomes that are more interesting than others. Here, highlight those things that you found interesting!


## Project Demonstration & Images

Give a link to a video of the project being demonstrated. The video should be hosted on the capstone youtube.

Below the video link show some well-taken, appropriately sized images of the project.


## About Us

### Team

[Jackson Woodard](https://www.linkedin.com/in/jacksonrwoodard/) is currently pursuing a degree in Electrical Engineering with a minor in Computer Science at Tennessee Technological University. His academic focus lies in the field of Programmable Logic Controllers (PLC) and Control Systems. In the context of the project, Jackson has been assigned the responsibility of developing a Fire Module designed to detect potential fire occurrences within a designated space. He is also helping design the 3D models for all the subsystems for the project. 

[Cole Cooper](https://www.linkedin.com/in/cole-cooper-78063520b/) is a student of Electrical Engineering enrolled at Tennessee Technological University in Cookeville. He has an academic interest in following the development and sustainment of power systems, microcontrollers, and communication protocols to name a few. Cole's role in this project is the development of the head unit and the communications system between the head unit and the sensor modules.

[Dylan Robbins](https://www.linkedin.com/in/dylan-robbins-51b933256/) is a student currently pursuing a bachelor's degree in Computer Engineering at Tennessee Technological University. His academic interests are focused in Embedded Systems, microcontrollers, and computer programming. Dylan's role in the project is to develop a mold sensing module and design it to detect any mold like conditions in a home. He is also responsible in assisting in any programminng of the sensors and data computations for the system.

[Nate Campbell](https://www.linkedin.com/in/nathaniel-campbell-0b24a2225) is a dedicated Electrical Engineering student enrolled at Tennessee Technological University. His academic focus revolves around Power Systems and Programmable Logic Controllers (PLC). Within the current project, Nathaniel assumes a pivotal role, primarily concentrating on the water sensor aspect and actively contributing to the development of the Uninterruptible Power Supply (UPS) for the overall power system.

[Luke Carson](https://www.linkedin.com/in/luke-carson/) is an Electrical Engineering at Tennessee Technological University with a minor in Mathematics. His primary area of interest lies in power systems, including power generation, transmission, and distribution. As part of a project, Luke is responsible for designing the gas module for the Preserve Home Pro system. The module will be used to detect the presence of propane, carbon monoxide, and ammonia.

### Faculty Supervisor

[Jesse Roberts, M.S.](https://www.tntech.edu/directory/engineering/faculty/jesse-roberts.php) is a professor at Tennessee Technological University. He has received both a Bachelor's and Master's degree in Electrical Engineering at Tennessee Technological University. He is currently pursuing a Doctorate of Philosophy in Computer Science at Vanderbilt University.

### Stakeholders

Tell a bit about the customer for the project. Also discuss any other groups (specific or general) that are expected to be impacted by the project.

### Recognitions

The team would like to thank the ECE Department at Tennessee Technological University for all the assistance needed in the design process. The team would also like to thank Jesse Roberts for all the assistance that he has given throughout the entire Capstone Project. Finally, the team would like to thank one of the external stakeholders, Wes Harris from State Farm, for answering any questions and providing the team with useful information to further advance the project.

## Repo Organization

### [Reports](/Reports)

The [Project Propsal](https://github.com/jacksonrwoodard/HouseHealthMonitoring/blob/main/Reports/Project%20Proposal/Project%20Proposal%20V2.pdf) report provides information about what the project problem is and the proposed solution.

The [Conceptual Design and Planning](https://github.com/jacksonrwoodard/HouseHealthMonitoring/blob/main/Reports/Conceptual%20Design%20%26%20Planning/Conceptual%20Design%20Final.pdf) report provides all specifications and constraints that the House Health Monitoring project must follow. The report includes all standards and regulations that will be followed during the project.

The [Experimentation](/Reports/Experimentation) report includes (will be finished later)

The [Poster](/Reports/Poster) shows (will be finished later)

The [Final Report](/Reports/Final_Presentation) includes (will be finished later)

The [Lessons Learned](/Reports/Lessons_Learned_&_Acquired_Skills) files show the lessons the team learned throughout the project process. 

### [Documentation](/Documentation)

All documentation for the project is included in the folder listed above. There are folders for 3D Models, Electrical, Images, Meeting Minutes, and Signoffs. All folders can be found in the documentation folder. 

The [Signoffs](/Documentation/Signoffs) folder has all of the approved detailed designs. The designs met all specifications and constraints for each subsystem. 

The [Meeting Minutes](https://github.com/jacksonrwoodard/HouseHealthMonitoring/tree/main/Documentation/Meeting%20Minutes) folder contains detailed minutes for each team meeting that occurred throughout the project process. Reading these files will provide you will knowledge of how the team advanced week to week.

### Software

All software used in the project will be located in this directory. For each system, a folder will be created that contains the relevant code with a readme file explaining the process of installing, executing, and testing the code.
