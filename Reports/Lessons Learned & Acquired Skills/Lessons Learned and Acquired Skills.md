# Lessons Learned

- Reflect on the project, both technical and organizational. What went well? What didn’t go well? 
- What unanticipated problems occurred? 
- What would you do differently if you were to do it over again? 
- What “best practices” have you identified? 
- What words of wisdom would you pass on to future students?
- What new knowledge or skills did you acquire throughout capstone.

## Jackson Woodard
- My expectations for this project were pretty high because I always set high standard for myself. At the beginning of capstone two, I was so stressed and assuming that we would not be able to get it working. After a month or two of trial and error in coding, we finally got it working and it was the greatest feeling. The group did really well with communication and we had meetings multiple times a week to complete our project.

- I thought we would be able to use Arduino IDE for the entire project, but I was completly wrong. We had to learn how to code with ESP-IDF in VSCode, and that took some time. I figured it would be easy to use the sensor libraries, but once again, I was wrong. We had to code the sensors from scratch with no libraries and that was tough, but we got it done.

- Even though we were on campus everyday 4-5 hours outside of class, I would have like to have the project done sooner so we could have got a better grade. Taking capstone two while full time in school is the most time consuming thing I have ever done, so if I could go back and change something, it would be spending even more time working on this project.

- I would say my public speaking skills have increased in this class due to the amount of speaking we have to do infront of people. I would also say I have a better understanding of understanding what a customer wants and be able to get the information from them about what they want if they do not provide enough.

- Be ready to devote your entire semester to capstone because if you do not, it will be hard to make a good grade and complete everything on time. Take everything a step at a time because it is very very easy to get overwhelmed very quickly.

- I learned more in capstone then I learned in any class I took in college. The amount of research and trial and error in this class tought me how to properly do research, how to code alot more effectively, and how to work better and effectively with a team.

## Nate Campbell
- I honestly didn't know what to expect going into capstone. However, after months of persistent coding and teamwork, we achieved success, which was incredibly satisfying. Our group's communication and persistence was excellent, with frequent meetings helping us stay on track and complete our project efficiently. What didnt go as well would be the sheer amount of time we spent each day working on the project.

- Some unanticipated problems would be just trying to integrate zigbee communication. I personally thought the process would be a little more straightforward.
  
- If i could change anything I would have put more effort into the communication subsystem upfront and make sure it was ready to go before the other subsystems.

- Documenting everything and having a reason for why everything is done the way we did. Being able to take a third party perspective on the entire project.
  
- To not get lost in the grades and not lose sight of the end goal.

- How to build a proper project from beginning to end. It required extensive research and critical thinking. It also allowed me to really see ways of thinking from different perspectives.

## Cole Cooper
- The biggest technical failure the team had was the XBee S2C not functioning as intended. We found out after already having the unit and setting it up that it would not communicate with the ESP32 H2, Raspberry Pi 4B, and a spare Arduino Mega 2560. The team ended up buying the Sonoff USB 3.0 Zigbee coordinator dongle that worked exactly as expected when connected to the head unit. The sensors’ communication to the ESP32s went very smoothly using the Arduino IDE with the ESP IDF but the Zigbee communication would not work until the Arduino libraries were converted over to the Visual Studio Code IDE with the ESP IDF. Organization wise, the team worked well together with a lot of communication between members over the successes and holdups experienced. 

- The largest unanticipated problem was figuring out how to code the ESP32 H2s to communicate via Zigbee protocols. We expected this to be difficult but not to take up about two months of the project’s time. Eventually the team did overcome these obstacles, but it took a lot of trial and error to achieve this success. 

- If I were to do something differently it would be to use different microcontrollers for the sensor modules. The ESP32 H2s used are fantastic hardware, but they are still quite new and do not have a lot of example codes which makes it much more difficult to design custom solutions using the microcontroller. Other ESP devices are easier to work with since they do have more example codes to work with.

- The primary best practice I identified is researching if codes exist for the hardware that is planning on being used. Researching forums, github repositories, and manufacturer documents to ensure that the intended application is possible and achievable within the six month time period demanded by this course.

- Make sure to check all of the grading rubrics before starting and while making your “Project Proposal” and “Conceptual Design & Planning” documents. The Project Proposal is what you are doing, like declaring your standards and constraints. Be aware of how you can solve what you are doing, but do not actually go into depth with how to solve your issues until you get to the Conceptual Design & Planning phase. This class is very similar to the stricter side of engineering work experience that I have worked with in the past, a lot of points may seem overly strict or unnecessary, but if you can figure out how to work within the rules given this class gets a lot more straightforward. 

- Team building, communication, patience, coding, experimenting, and proving that a system will work beyond what a manufacturer claims are a few of the experiences that this class has given me. I have a decent amount of experience with the stuff mentioned from previous engineering and non-engineering work experiences, but even so I feel the challenges and overcoming of those challenges has been a good experience.

## Luke Carson
- From start to finish the project was a series of obstacles. At times it was overwhelming and frustrating. Once, the group or even yourself got over a obstacle you felt a sign relief but you had to be looking ahead and staying on task in order to meet your deadlines. Overall, this course does teach you skills that will translate into your future job like documentation, communication, teamwork, and accountability. 

- Definitely the coding of our sensors was the biggest anticipation of the group. In your head you feel like you have it all planned out and this is going to work like this and sadly that was not the case for our communication module. Instead of using arduino IDE, we had to implement ESP-IDF which I think any of us had previous experience with unlike arduino IDE. So, we had to learn on the fly and watch alot of youtube and research alot more than intended.

- Even though we already spent countless hours on our capstone project, it just felt like we still needed more time to really accomplish what we set out to do. But time is a constraint and you have to manage with what you are given.

- Researching is very helpful and being able to look at datasheets to see if the product is going to meet your desired needs is a big thing. Also, communication with your team is another big practice because of the aspect of everyone is on the same page or even you need some help with your system you always got another mind there for your benefit.

- Time management is going to be your biggest friend and enemy. The project will eat up alot of your time during the semester with signoffs being checked off or even experimentation testing. Luckily, I only had 6 hours this semester so I could almost fully commit to our project, but if that was a different scenario I could see myself under alot of stress.

- Literally taking everything I learned in undergrad and being able to tie everything in together with one big project. Also, I felt like this class helped with my public speaking skills as well. 

## Dylan Robbins
- Going into Capstone, I was expecting the course to be just like any other course except strictly focused on the process of design and being hands on with things. I was right about most of it, but I had no idea that it was going to consume so much of my time. I learned that being proactive and having great communication with your team are two of the most important things for success throughout this course. Our team had a lot of success with our project, but the implementation of the communication set us back quite a bit. We spent maybe a month or longer trying to code for our modules to be able to communicate with each other. I believe that without the relationship and communication we all had the project might not have gotten finished.

- Touching back on my first point, coding for wireless communication was the biggest unanticipated problem we encountered. At first, we were on track to have everything finished up well before the deadline, but after days upon days trying to figure out the communication code, we were not getting anywhere. We ended up having to swap coordinator devices and digging deep into a lot of example codes to get the issue resolved. We learned a lot of new things on our own through research and trial and error.

- If I were to do something differently, I would have tried my best to understand the full implementation of the system and pieces needed from the start. Not knowing exactly what was expected of us with the communication module was rough when we finally got to it. I think it would have been nice to do a little more research and understand how to implement the communication before we bought a device and wasted a bunch of time on it.

- I would say that some of the best practices would be to stay proactive and have great communication with your team. Making sure everyone stays involved in research so they know what is going on will benefit everyone in the long run.

- Stay proactive and start immediately. Do not think that a due date being a month out is plenty of time to get things done. This course is very intensive so expect to spend a lot of time with your group and in the lab if you want to make a good grade.

- I believe that my research, problem solving, and analysis skills greatly improved over the course of capstone. To be honest, not many classes will prepare you for the work in this course. I had to spend countless hours trying to figure things out on my own and doing my own research to learn new things. In the end, it pays off because it has prepared me a little more for what to expect in the real world.
