---
layout: default
title:  "Final Project"
permalink: /Project/
---
<div class="wrapper">
        <article class="post h-entry" itemscope="" itemtype="http://schema.org/BlogPosting">

  <header class="post-header">
    <h1 class="post-title p-name" itemprop="name headline">Final Project</h1>
    <p class="post-meta">
      <time class="dt-published" datetime="2019-07-23T00:00:00+00:00" itemprop="datePublished">Jul 23, 2019
      </time></p>
  </header>

  <div class="post-content e-content" itemprop="articleBody">
    <meta name="viewport" content="max-width= 95%, initial-scale= 1">

<style>
body {font-family: Arial;}
body {background-color: white}
/* Style the tab */
.tab {
  overflow: hidden;
  border: 10px solid #933e43;
  background-color: white;
}

/* Style the buttons inside the tab */
.tab button {
  background-color: white;
  float: left;
  border: none;
  outline: none;
  cursor: pointer;
  padding: 14px 16px;
  transition: 0.3s;
  font-size: 18px;
}

/* Change background color of buttons on hover */
.tab button:hover {
  background-color: #933e43;
}

/* Create an active/current tablink class */
.tab button.active {
  background-color: white;
}

/* Style the tab content */
.tabcontent {
  display: none;
  padding: 9px 18px;
  border: 10px solid #933e43;
  border-top: none;
}
</style>


<p><font color="black">(click on the tabs below)</font></p>

<div class="tab">
  <button class="tablinks" onclick="openCity(event, 'Final Project Original Plan)">Final Project Original Plan</button>
  <button class="tablinks" onclick="openCity(event, 'Final Project Plan 2')">Final Project Plan 2</button>
	<button class="tablinks" onclick="openCity(event, 'Final Plan')">Final Plan</button>
</div>

<div id="Final Project Original Plan" class="tabcontent">

Idea:
-A wearable device on the wrist that allows you to focus by sending a small and safe electrical current onto your wrist when you start procrastinating or become distracted.
	--The current should be irritating but not painful
	--An alternative, if a current is unsafe, would be a vibration or loud beeping noise
--It can shock when you pick up your phone or other electronics.
-The device can include a lie detector that tracks your heartbeat to determine if you are lying about doing your work
-The device can be used through an app which allows you to create blocks of time in which you do not use electronics. 

Tools:
Solder, glue?, 3D printing



Materials:

Lie detector-
Heartbeat sensor, arduino, breadboard, Jumper Wire, 16x2 LCD Display, 10k ohm Potentiometer
Tutorial on heartbeat sensors with Arduino: https://www.youtube.com/watch?v=sTkroVP3y0k
	Edit*- the lie detector is probably a little too complex to add

Electric shock-
Electrode wire, or copper tape, or conductive rubber and wires

Or I could use something similar to electric fly swatters- https://www.youtube.com/watch?v=BK1RP60Y45M
	-Magnetics, high voltage capacitor 0.330uF, oscillator, button, LED, resistors, standard rectifier diode, transistor 		is an NPN with part number: 8050S
	-circuit diagram : <img width="1496" alt="Screen Shot 2019-07-08 at 11 12 43 AM" src="https://user-images.githubusercontent.com/52216217/60821392-72bee400-a171-11e9-8555-a27121cd49bc.png">
	
If electric shocks are unethical I can also use vibration**: http://www.learningaboutelectronics.com/Articles/Vibration-motor-circuit.php
Materials- Arduino Board, vibration Motor, 1N4001 Diode, 0.1µF ceramic capacitor, 1KΩ Resistor, 2N2222 NPN Transistor, USB Connector
Circuit: <img width="796" alt="Screen Shot 2019-07-09 at 10 36 42 AM" src="https://user-images.githubusercontent.com/52216217/60897140-8d5a9100-a235-11e9-86df-736c0daa2403.png">


Hardware-
Silicon for the wristband, rechargeable battery, aluminum, circuit board

Software-
Bluetooth chip, and ...?
Possibilities:
https://www.makeuseof.com/tag/6-easy-ways-connect-arduino-android/
https://www.makeuseof.com/tag/6-easy-ways-connect-arduino-android/


Similar product: Pavlock - https://pavlok.com/blog/inside-pavlok-history-pavlok-hardware-steve-trambert-mechanical-engineer/


Design:
![PHYS FP 1](https://user-images.githubusercontent.com/52216217/60459780-0c394380-9c10-11e9-9421-c2592daccb9d.jpg)
</div>




<div id="Final Project Plan 2" class="tabcontent">
	Final project idea(s):

A wearable device that beeps and vibrates to keep its user focused. It will sound when the user uses his/her computer.

I plan on executing this through one of two ways:
Using a tilt sensor to detect when a computer screen is flipped on
Drawbacks:
I know how to use tilt sensors, but the calibration may be tricky. I tried making one during lab 7 (see https://jenny-15.github.io/PHYS-S-12-Assignments/2019/07/18/Session07.html for more information), and it was very inconsistent. 
I used a small container, water, and capacitance. The capacitance was difficult to work with because it was disturbed very easily whenever the sensor shifted or its wires moved.
Maybe if I used an actual tilt switch like this one: https://www.adafruit.com/product/173 it would be more reliable
I would have to make a whole other circuit on the computer, making it bulky
Benefits:
If I used a tilt switch it would probably be pretty reliable
Creating a program that will run when once a computer is turned on, outputting to the Arduino to turn on the buzzer+motor.
Drawbacks:
I do not have much experience with code, so writing the program to achieve this would be a lot more difficult
I do not know how to create a program that runs automatically whenever my computer turns on that outputs to an Arduino
https://www.howtogeek.com/228467/how-to-make-a-program-run-at-startup-on-any-computer/
This may be too difficult for me
Benefits:
I would not need to physically attach anything onto my computer
This would be more reliable than the tilt sensor
It would be able to detect when the computer is actually on instead of simply detecting the physical movement of a close laptop to an open one


Design:

My design will be fairly similar to what I did for my prototype. I will have a wristband with a circuit concentrated in one area, sort of like a watch. 



Materials:

Buzzer-
A Piezo buzzer
They are a little bulky

Vibration motor-
I will use a ERM vibration motor
Pros
They are more powerful than coin vibration motors
Cons
They are bulkier and less compact than coin vibration motors
I will have to make a container to hold it because it does not stick in place
I also have to bolt it down somehow
There is a free-spinning mass that must have room to rotate within the container
I will mount the motor either through housing (left) or securing directly (right)
Lights-
I may potentially add LED strips like these: https://learn.adafruit.com/adafruit-neopixel-uberguide/the-magic-of-neopixels
These will turn on with the vibration motor and buzzer to further incentivize users to close their computer
They may be an unnecessary addition since I already have a buzzer and vibrator
I would have to modify the design of my wristband and it may also become bulkier
I would have to find a suitable material
I am unsure how I would incorporate it into the wristband
It would be hard to connect it to the Arduino through the wristband
The lights would either circle around the enclosure or run down the wristband, but this would probably not work very well logistically since I am not directly connecting the wristband and enclosure.


Circuit-
It would be ideal if I could create a soldered protoboard or PCB for the circuit to conserve space
This will be challenging since I do not know how either of these work
PCB basics: https://www.autodesk.com/products/eagle/blog/printed-circuit-boards-10000-feet-introduction-electronics-beginners/

Enclosure-
I need to make an enclosure for the circuit that depends on if I make a protoboard or PCB
It needs to accommodate the bulkiness of the buzzer and vibrator
The vibrator also needs to be ERM vibrator has to be secure
Potential materials (for 3D printing)
Should be rigid
POLYAMIDE (PA)
PROS • Toughest plastic material • Bends without snapping • Relatively inexpensive • High chemical resistance • Food compatible (check with supplier if it’s colored Nylon!) • High softening temperature 
CONS • Nylon filaments are prone to absorb humidity fast and need to be properly stored
ACRYLONITRILE BUTADIENE STYRENE (ABS)
PROS • Stronger than PLA • Long lifespan • Inexpensive • Wide variety • LEGO® uses this plastic so it must be good CONS • Warping can be an issue • Not biodegradable • It can shrink significantly when it cools down • Unpleasant and toxic fumes when printing
Regula Polyactide (PLA)
I would like to make the enclosure in the shape of a hexagon if it not overly bulky


Wristband-
The material for the wristband depends on the circuit that I make (PCB or soldered protoboard), if I decide to add LED strips, and how I make the enclosure. 
Instead of mounting the circuit enclosure I as did in the prototype, I think I will probably attach it somehow
The band would probably be hooked onto the enclosure
This would conserve space and make everything less bulky
It would create a better shape overall because the wristband is curved when wearing it, so the enclosure would have to adhere to that rounded surface if it was mounted on, which would be tricky
I would not have to compromise the flexibility of the wristband or the hard structure of the enclosure
I want the wristband to have one of 2 properties:
Stretchiness:
It has to be able to hold on its own when not stretched but still have the room to expand
I would like 3D print something like this for the wristband: http://www.hk3dprint.com.hk/en/gallery/Fashion-Accessory/Nylo-Flexible-Stretch
It is able to stretch upon expansion
This make be difficult to attach to the enclosure because will probably add a rectangular hook to the enclosure
I am not sure how strong this would be because the enclosure would have a weight that needs to be accounted for
Or I could make something with a simpler pattern like a zigzag but it would probably be even weaker than the other design (http://www.hk3dprint.com.hk/en/gallery/Fashion-Accessory/Nylo-Flexible-Stretch )
Adjustability:
This would be much simpler than a stretchy design and more secure
The design would be like a standard watch strap
Potential materials:
The materials for this wristband need to be flexible so that the design can expand or at least bend to adhere to the wrist
PLA- polyactide (preferably the flexible kind)
PROS • Odorless • Not petroleum-based • Biodegradable • Inexpensive • Wide variety 
CONS • Low temperature resistance • Low strenth • Brittle
THERMOPLASTIC POLYURETHANE (TPU)
PROS • Flexible • Abrasion resistant 
CONS • Not the best for tiny details
GLYCOL MODIFIED PETG
inexpensive, naturally transparent, flexible and durable material that has found its way to FDM 3D printers aiming to match the strength of ABS plastic with the ease of use of PLA plastic.
