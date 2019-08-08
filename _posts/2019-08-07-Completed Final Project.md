---
layout: default
title:  "Completed Final Project"
permalink: /13/
---

### Completed Final Project

**Goal:**
The goal of my final project is to create a wearable device that helps users stay focused and electronics-free. It alerts users when they use electronics and discourage the continued use of them by reacting negatively(beeping+vibrating). The device uses aversive conditioning.

I decided to make this device because it is very useful in the modern world. People spend increasingly concerning amounts of time on electronics, and much of this time could be better spent on other activities. Although I personally do not spend that much time on my phone, I do use it more often than I would like. The idea behind this device is to help people disconnect from the internet and spend more time in the real world. 

(I started going on a bit of a tangent here, so feel free skip ahead to “Aversive Conditioning” to learn about how my project works.) The internet can be a great learning resource when sharing knowledge with others on websites like this, but too much time on electronics can be harmful. Given recent events, people should not be divided by screens and opinions during such tumultuous times. They should be open-minded of other perspectives instead of sticking to personal prejudices to work towards the mutual goal of making the world a better place. With more time on people’s hands, important issues can actually be resolved; if face-to-face interactions increased, people would spend less time arguing with others on the internet, resulting in a less divided and more cooperative world. 



**Aversive Conditioning:**
Aversive conditioning is a behavioral training that uses negative stimuli to associate certain actions as negative. It exposed subjects to a bad behavior and discomfort, associating the undesired behavior and the discomfort. By associating bad behaviors with uncomfortable feelings, the brain begins to associate bad behaviors with it. The concept is that if behaviors can be learned, they can also be unlearned.


**How it Works:**
My final project consists of two separate cirucits. One transmits and the other receives. 

Transmitter-
This circuit has a button, an LED, and a tilt switch. The button acts as an on/off switch. Each time the button is pressed, the LED turns on/off. The code is programmed to check the state of the tilt switch when the LED is on. It then sends the tilt switch state to the receiver. The tilt switch detects the angle of the device it is attatched to. So, if your computer screen is closed, the switch is off. The, when you tilt open the screen, the tilt switch is on. This works on phones too. If your phone is laid flat the switch will be off, and if you pick it up it will be on.

Receiver-
This circuit has a buzzer, a vibration motor, and a transistor. I used the transistor to control the motor and turn it on/off. When the tilt switch is on, the transistor powers the motor. The buzzer beeps when the tilt state is on.


Materials:
Circuit-
A breadboard, 2 protoboards, 2 nrf24l01 radio modules, buzzer, ERM cylindrical vibration motor, transistor, button, tilt switch, LED, wires, AND 2 Arduino Uno's and/or Nano's.

Device-
Cardboard, hot glue, fishnet material, velcro

Tools-
Soldering gun, laser cutter

Software-
Fusion 360, Arduino IDE

Cardboard cube cut on Fusion 360:
Receiver-
<script src="https://embed.github.com/view/3d/jenny-15/PHYS-S-12-Assignments/master/13/DF%20R4.stl"></script>

Transmitter-
<script src="https://embed.github.com/view/3d/jenny-15/PHYS-S-12-Assignments/master/13/DFT4.stl"></script>


The circuit diagram:
Transmitter-
<img width="973" alt="Screen Shot 2019-08-06 at 7 35 57 PM" src="https://user-images.githubusercontent.com/52216217/62584677-95810d00-b883-11e9-9326-8f307fc5a38c.png">

Receiver-
<img width="1005" alt="Screen Shot 2019-08-06 at 7 35 40 PM" src="https://user-images.githubusercontent.com/52216217/62584681-97e36700-b883-11e9-8b0c-17fecbee6eb1.png">

The final circuit video:
<video width="" controls="">
		<source src="IMG_2651.TRIM.mp4" type="video/mp4">
	</video>

Final code:
<a href="https://create.arduino.cc/editor/jennyxu/2cfe51be-07db-43fd-8736-ba8b8eaefe5c/preview
">Transmitter</a>

<a href="https://create.arduino.cc/editor/jennyxu/b309f01a-2e6c-4a24-be1e-637bd7ceee92/preview
">Receiver</a>

The final device:
	
Receiver-
![IMG_2707](https://user-images.githubusercontent.com/52216217/62587842-a0db3500-b891-11e9-85a2-f57cbd63f163.jpg)
![IMG_2730](https://user-images.githubusercontent.com/52216217/62707198-f82af380-b9be-11e9-8714-f5259c9f39f2.jpg)

Transmitter-
![IMG_2749](https://user-images.githubusercontent.com/52216217/62707208-fbbe7a80-b9be-11e9-91c7-f1d26dc8e24c.jpg)
![IMG_2750](https://user-images.githubusercontent.com/52216217/62707214-00832e80-b9bf-11e9-93e9-ef971415fe12.jpg)
![IMG_2751](https://user-images.githubusercontent.com/52216217/62707224-05e07900-b9bf-11e9-8d5e-25c634ee329f.jpg)
![IMG_2753](https://user-images.githubusercontent.com/52216217/62707231-09740000-b9bf-11e9-83f8-1e291a98a84b.jpg)
![IMG_2754](https://user-images.githubusercontent.com/52216217/62707237-0c6ef080-b9bf-11e9-8a69-033b9e30baa5.jpg)
![IMG_2756](https://user-images.githubusercontent.com/52216217/62707248-0f69e100-b9bf-11e9-86aa-27f72f0cfcf4.jpg)


**What I learned:**
During this project, I gained a lot of new skills. Firstly, I gained more programming experience. Before this class, I had not written any code. Throughout this project, I gained a much better understanding about how C++ works. I also got to learn about the capabilities of Arduino's. Although we learned some basic commands in class, during this project I used radio modules to communicate between two Arduinos and learned how to add this into the code. 

A major skill that I learned is debugging, which will be useful in all future projects. To get my code and radio communication working I had to spend a long time debugging. The first thing that I had to achieve was a working code. After I first wrote it, it was not working, so I looked through each line to figure out where the problem was. I checked the code execution, the if statements, the variable values, and if the Arduino’s were sending and receiving, and what the Arduino’s were sending and receiving. At one point, I was really stuck on why the circuit was not working as I wanted it to. Nathan’s helped me figure it out, and it turns out that I needed to change the pinMode to INPUT_PULLUP instead of INPUT. 

After I debugged the code, I had a lot of trouble with the protoboard after I transferred my circuit from the breadboard. I checked the soldering, the wiring, the hardware, the connections, the power, the sending and receiving, and I looked at how the pins should be communicating. Even after all of this, I was not able to determine the problem or how to fix it.


**Final Thoughts:**
My final project did not turn out the way that I expected, but I learned a lot along the way. I initially planned on making a wristband that shocked the wearer when they turn on electronics, and I ended up with a wristband that vibrates and buzzes and a separate device that attaches to electronics. In the end, I did not have enough time to condense my circuit into a protoboard due to issues I had with the radio module. So, I created the circuits that I would have put into the protoboard on a breadboard and made the devices that hold my circuit separately. My final project works, just not altogether. The code, sensor, vibrator, and buzzer all work, just not when transferred onto a protoboard. 

I think that this whole experience has been very worthwhile. Although this project did not turn out as I expected, I will definitely work on my protoboard after this class ends and get the radio modules to work. I will probably just start with a new protoboard and nrf24l01 and solder the connections again.

This entire class has been very interesting. Everything that I was exposed to was pretty new to me, and much of it was not anything that I could have learned in school. This has been very a eye-opening class since I got to learn about many diffrent fields within technology and where they are going. It is definitely something that I am interested in pursuing and exploring further!


