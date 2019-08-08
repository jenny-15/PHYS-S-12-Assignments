---
layout: default
title:  "Completed Final Project Completed"
permalink: /13/
---

### Completed Final Project

The goal of my final project is to create a wearable device that helps users stay focused and electronics-free. It alerts users when they use electronics and discourage the continued use of them by reacting negatively(beeping+vibrating). The device uses aversive conditioning.

**Aversive Conditioning:**
Aversive conditioning is a behavioral training that uses negative stimuli to associate certain actions as negative. It exposed subjects to a bad behavior and discomfort, associating the undesired behavior and the discomfort. By associating bad behaviors with uncomfortable feelings, the brain begins to associate bad behaviors with it. The concept is that if behaviors can be learned, they can also be unlearned.


My final project did not turn out the way that I expected, but I learned a lot along the way. I initially planned on making a wristband that shocked the wearer when they turn on electronics, and I ended up with a wristband that vibrates and buzzes and a separate device that attaches to electronics. In the end, I did not have enough time to condense my circuit into a protoboard due to issues I had with the radio module. So, I created the circuits that I would have put into the protoboard on a breadboard and made the devices that hold my circuit separately. My final project works, just not altogether. The code, sensor, vibrator, and buzzer all work, just not when transferred onto a protoboard. 

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




