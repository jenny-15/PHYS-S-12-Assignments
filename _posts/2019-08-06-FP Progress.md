---
layout: default
title:  "Final Project Progress"
permalink: /14/
---

### Final Project Progress

July 31:
During the lab, I worked on my final project. I did not want to disassemble my prototype, so I made a new circuit. This time, I incorporated a transistor. I plan on using this in my wristband to turn the motor on and off. Previously, in my prototype, I used a physical button so that the motor+buzzer would turn on while I held the button down. This will not work in my final design, so I had to use a different method of controlling my circuit. 

I spent a lot of time on the motor. The wires connected to the motor are very weak and kept on unattaching from the circuit. I tried using tape, but that did not secure it either. Then, I decided to solder the wire. After a while, this broke as well. I re-soldered the motor with a different strategy. First, I strengthened the wires on the motor itself with the tin wire. Then, I added this onto a separate wire and joined them with additional tin wire (Image 4). This worked very well, and I do not think that it will break again. Something else that I found difficult with the motor is the delicacy of the wires. It was really hard to strip the wires without cutting it off since they are incredibly thin. 
![IMG_2491](https://user-images.githubusercontent.com/52216217/62708679-dda64980-b9c1-11e9-9eab-741fd4cb2a57.jpg)


In the first circuit that I made, I tested the transistors code. I made a circuit with a button, a transistor, a buzzer, and a vibration motor. The motor turned on through the transistor, and the button is controlled separately of the transistor, when the button is pressed. 
Circuit: 
![IMG_2459](https://user-images.githubusercontent.com/52216217/62708752-029abc80-b9c2-11e9-9373-3d071b408a83.jpg)


Next, to take it further, I incorporated radio modules. I am still working on the code because it has not been working. The light that indicates that my transmitter is not lighting. But, essentially I have a tilt switch, LED, radio module, and button on one circuit, and a button, vibration motor, radio module, and transistor on the other. The former will go on my laptop, and it will turn on when I push the button, even when I release my finger. If the button is on, the LED will light. Then, if the button is turned on, the switch will detect whether my computer is flipped open. If it is, it will tell the other radio module and the buzzer and vibration motor will turn on on the wristband. I have written the code for both the transmitter and receiver, although neither are working yet. I am not sure if the problem is with the radio modules, the circuit wiring, or the code. I previously had some difficulty with the radio modules. I will keep working on finding the problem. 

Eventually, I will use Arduino Micros instead of Arduino Unos in my project. I soldered an Arduino Micro during the lab. 

Update*** Moments after writing about these issues, I realized that I may have had the LED in the wrong way, which is why it was not lighting. I was right, and I have spent a lot of time examining the code and circuits. The problem was actually a lot simpler than I thought. However, now that the LED has turned on it is acting strangely and will not turn off when I press the button. It just keeps blinking. The receiver reacts with the LED. It vibrates and buzzes as the LED blinks, and it vibrates much stronger when the transmitter is tilted (the tilt switch), but nothing turns off when the transmitter is laid flat, which is the goal. Instead, the buzzing+vibrating just gets weaker.JulyAugust 1:

I am currently working on creating the circuit that I will transfer onto a protoboard. 

I am mostly working on the code and working out little kinks. I spent a lot of time reworking my code so that my button and tilt switch would work well, and, with Nathan’s help, I found that the problem was with the pinMode. I needed to change the tilt switch and button to INPUT_PULLUP instead of just INPUT. 

After fixing this, my circuits should theoretically be working. However, the circuit has been acting strangely. The vibrating motor sometimes turns on spontaneously, and sometimes it will not turn on at all. Sometimes, if I re-insert wires, the motor will suddenly turn on again.

The main goal that I am currently working on is getting the motor and buzzer to turn on as the tilt switch turns on.  


August 3:

Today I finished my circuit and code, changed my Arduino Uno’s to Arduino Micro’s, soldered my vibration motor, and began working on soldering my protoboard.

I made a few tweaks to the transmitter and receiver code, which are attached below.

Transmitter-
https://create.arduino.cc/editor/jennyxu/2cfe51be-07db-43fd-8736-ba8b8eaefe5c/preview

Receiver-
https://create.arduino.cc/editor/jennyxu/b309f01a-2e6c-4a24-be1e-637bd7ceee92/preview


After finishing with the circuit, I swapped out the Arduino Uno’s with Micro’s to save space. 

Finished circuit:
![IMG_2570](https://user-images.githubusercontent.com/52216217/62708795-1b0ad700-b9c2-11e9-8069-c97c48df1256.jpg)
![IMG_2561](https://user-images.githubusercontent.com/52216217/62708813-23631200-b9c2-11e9-85fd-06944c438fa8.jpg)
![IMG_2567](https://user-images.githubusercontent.com/52216217/62708867-3b3a9600-b9c2-11e9-8a0f-3f1f99102143.jpg)

I also had to solder my vibration motor again because broke off (again). This time, Nathan helped me, and I used heat shrink tubing and hot glue to keep everything in place.
![IMG_2552](https://user-images.githubusercontent.com/52216217/62708959-6e7d2500-b9c2-11e9-9323-05ac636db266.jpg)
![IMG_2553](https://user-images.githubusercontent.com/52216217/62708944-63c29000-b9c2-11e9-8fee-96377fb1e4d5.jpg)
![IMG_2555](https://user-images.githubusercontent.com/52216217/62708939-61f8cc80-b9c2-11e9-8b0c-261a25f93021.jpg)



August 4th:
Today I replicated my circuits on a protoboard. I first soldered on an Arduino Micro and a nRF24L01 radio module. This took quite a while because I have not made a protoboard before, and the soldering was small and detailed. After I did this, I tested the radio module to see if it could receive anything from my other circuit. It did not work, and after checking the nRF24L01 and my soldering for a long time, Nathan and I were still unable to figure out the problem. We checked the soldering, the voltage, and the device pinout, but we still did not see the problem. The issue is definitely not with the code or circuit setup because it worked perfectly before I transferred it onto the protoboard.

I spent most of the lab on debugging, but, towards the end, I began soldering my other circuit that goes on my computer. So far I have added an Arduino Micro, a LED, a resistor, a button, and my tilt switch. Everything is currently working except for the LED, which is strange because was working. The LED was the first thing that I soldered on after the Arduino, so I checked to see if it worked. It lit, but then after I added other components it stopped lighting. I will work on this problem and the radio module problem tomorrow.


August 5: 
Today I worked on debugging the nRF24L01 radio module. First, Rob and I tested them with a 3.3 V power source, and this seemed to work well. So, I soldered on a 3.3 V regulator, but it still did not work. Something that was weird was that the radio module that I soldered was able to successfully transmit, but not receive. It only received zeros even though I sent it ones. With Julian, I also checked the device pinout with an Oscill to figure out how the pins communicate. After a long time of more debugging, we were unable to determine the problem and how to fix it. So, Rob suggested that, due to time constraints, I should just create my circuit on a breadboard with Arduino Uno’s to demonstrate that my circuit and code work and work on debugging outside of this class. I will still be creating a wristband and container to hold the tilt sensor that attaches to my computer and the buzzer, but the protoboards inside it will not be functional (yet). For the rest of class, I added the circuit onto a breadboard and made the protoboard smaller by cutting off the excess with a saw. I did not add a vibration motor onto the protoboard because there are no more so I need to use the one that i have on the breadboard.

Solder:
![IMG_2638](https://user-images.githubusercontent.com/52216217/62709109-c156dc80-b9c2-11e9-9aae-eac295200cb3.jpg)

Circuit:
![IMG_2640](https://user-images.githubusercontent.com/52216217/62709142-cd429e80-b9c2-11e9-974d-58e480cc18d7.jpg)


August 6:
Today I created the containers for the protoboard. I decided to use cardboard instead of 3D printing because I need there to be a flexible opening/closing lid so that I can take the protoboard out when I need to. I could not have really done this with 3D printing. Unfortunately, this doesn’t look as nice, but I realized that I would not have much time to figure out how to make such a case with 3D printing. Due to the time I spent on this project over the past week, I have had a lot of work pile up so my time is very limited. It would take a while to figure something out and then design it in Fusion since I am not very experienced with it, and I often have scaling issues. 
Essentially, I wanted to make a box with a lid. I made the box and the lid the same size because I thought that the box would expand slightly. 
Transmitter-
<img width="471" alt="Screen Shot 2019-08-07 at 12 37 03 AM" src="https://user-images.githubusercontent.com/52216217/62709243-fcf1a680-b9c2-11e9-9ba9-97e8562b313a.png">
<img width="1304" alt="Screen Shot 2019-08-07 at 12 37 13 AM" src="https://user-images.githubusercontent.com/52216217/62709248-ffec9700-b9c2-11e9-9ad2-6a0264a9dd67.png">

Receiver-
<img width="1312" alt="Screen Shot 2019-08-07 at 12 38 06 AM" src="https://user-images.githubusercontent.com/52216217/62709290-1397fd80-b9c3-11e9-86b8-6fada29f36a9.png">
<img width="446" alt="Screen Shot 2019-08-07 at 12 35 59 AM" src="https://user-images.githubusercontent.com/52216217/62709298-1692ee00-b9c3-11e9-8459-ee5284ec383a.png">

I spent a long time trying to print my designs because the laser cutter was abnormally weak that day, and the laser barely touched the surface of the cardboard (Image 1). After a lot of adjusting, I was able to get the cutter to work by increasing the power and decreasing the speed. However, I used an x-acto knife to remove the shapes from the cardboard because I made little halfway cuts to make the sides bendable. 
![IMG_2670](https://user-images.githubusercontent.com/52216217/62709374-3b876100-b9c3-11e9-9e20-8640e9b68d02.jpg)

After I printed the shapes and removed them with a knife, I tried putting the box together. I had to hot glue all of the sides but the flap (Image 2+3) since the cube would not stay together. The transmitter has an opening at the top for the on and off button and LED.
![IMG_2671](https://user-images.githubusercontent.com/52216217/62709433-58239900-b9c3-11e9-8cc0-b09239e361a6.jpg)
![IMG_2678](https://user-images.githubusercontent.com/52216217/62709434-59ed5c80-b9c3-11e9-9fc2-e232bb8ae603.jpg)
Image 2+3 (transmitter+receiver)

 I realized that all of the sides overlappings was pointless, so I decided to reprint the containers as a cube. The stl files can be found on my “Final Project Results” page. Once again I removed the shapes from the cardboard after I laser cut it, and I hot glued the sides so they would stay up. This looks a lot cleaner than my first design.
![IMG_2689](https://user-images.githubusercontent.com/52216217/62709640-bea8b700-b9c3-11e9-928c-ced3cad7fe41.jpg)
![IMG_2687](https://user-images.githubusercontent.com/52216217/62709651-c36d6b00-b9c3-11e9-884f-992d2d61ec9c.jpg)
![IMG_2692](https://user-images.githubusercontent.com/52216217/62709710-e7c94780-b9c3-11e9-9422-4f6701be4c52.jpg)

The next step was to attach a wristband to my first container. I first planned on using the same material as I did for my prototype (webbing). After I hot glued straps onto my cardboard container, I went to look for velcro for the straps. As I did this, I found another material that is kind of like a fish net (Image 4). I decided to use this instead since it is stretchy, so I removed the webbing material and glued this on instead.

![IMG_2700](https://user-images.githubusercontent.com/52216217/62709735-f57ecd00-b9c3-11e9-8791-9311a70b586c.jpg)
Image 4

Finally, I added velcro to the transmitter container that will attach to my computer. 
Please see the “Completed Final Project” to see the final results.
