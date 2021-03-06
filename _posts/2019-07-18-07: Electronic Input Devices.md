---
layout: default
title:  "07: Electronic Input Devices"
permalink: /07/
---

### 07: Electronic Input Devices

Today we made electronic input devices using a sensor, and we also had to calibrate the sensor. I made a tilt sensor using capacitance. I then attached this sensor to my computer so it can detect when the computer is on/off. I may use something like this in my final project, where I am making a wristband that helps you focus by vibrating and beeping when you use electronics. To learn about capacitance, please visit this site for more information: https://learn.sparkfun.com/tutorials/capacitors/all

Making the sensor:
First, I filled a little container less than halfway with water. Next, I used duct tape to secure the cap of the container and ensure that no water leaks. Then, I soldered a wire onto a small strip of electrical tape, and I did this step twice to make two strips of tape. I then placed electrical tape onto opposite sides of the container.

Electrical tape-
![IMG_2224](https://user-images.githubusercontent.com/52216217/61652587-46818800-ac86-11e9-98f7-942ac57072cb.jpg)

Sensor-
![IMG_2220](https://user-images.githubusercontent.com/52216217/61652368-c6f3b900-ac85-11e9-8f13-cd184872f66c.jpg)

The circuit:
I connected one of the wires connected to the tape into pin 4 and the other in A0 (it doesn’t really matter which is which). Then, I used a breadboard to make a basic circuit. After connecting 5V into the board, I connected another wire from Pin 4 to the LED. I then connected a 10 kilolm resistor to the LED from the 5V. 
![IMG_2216](https://user-images.githubusercontent.com/52216217/61652420-e559b480-ac85-11e9-80f8-8ccafa2a3948.jpg)

The code:
The code dictates when the LED turns on. The variable “diff” is the difference between the 2 capacitance readings, which changes as the computer tilts. Then, I added an if else statement in which the LED turns on when the diff is greater than or less than a certain value. The LED is meant to turn on when the computer screen is opened enough for it to be “on”

<pre>
<font color="#00979c">int</font> <font color="#000000">read_high</font><font color="#000000">;</font>
<font color="#00979c">int</font> <font color="#000000">read_low</font><font color="#000000">;</font>
<font color="#00979c">int</font> <font color="#000000">diff</font><font color="#000000">;</font>

<font color="#00979c">int</font> <font color="#000000">ledPin</font> <font color="#434f54">=</font> <font color="#000000">2</font><font color="#000000">;</font>

<font color="#00979c">void</font> <font color="#5e6d03">setup</font><font color="#000000">(</font><font color="#000000">)</font> <font color="#000000">{</font>
<font color="#d35400">pinMode</font><font color="#000000">(</font><font color="#000000">4</font><font color="#434f54">,</font><font color="#00979c">OUTPUT</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Pin 4 provides the voltage step</font>
<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">begin</font><font color="#000000">(</font><font color="#000000">9600</font><font color="#000000">)</font><font color="#000000">;</font>
<font color="#000000">}</font>

<font color="#00979c">void</font> <font color="#5e6d03">loop</font><font color="#000000">(</font><font color="#000000">)</font> <font color="#000000">{</font>

 
 &nbsp;&nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">4</font><font color="#434f54">,</font><font color="#00979c">HIGH</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Step the voltage high on conductor 1.</font>
 &nbsp;&nbsp;<font color="#000000">read_high</font> <font color="#434f54">=</font> <font color="#d35400">analogRead</font><font color="#000000">(</font><font color="#000000">A0</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Measure response of conductor 2.</font>
 &nbsp;&nbsp;<font color="#d35400">delayMicroseconds</font><font color="#000000">(</font><font color="#000000">100</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Delay to reach steady state.</font>
 &nbsp;&nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">4</font><font color="#434f54">,</font><font color="#00979c">LOW</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Step the voltage to zero on conductor 1.</font>
 &nbsp;&nbsp;<font color="#000000">read_low</font> <font color="#434f54">=</font> <font color="#d35400">analogRead</font><font color="#000000">(</font><font color="#000000">A0</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Measure response of conductor 2.</font>
 &nbsp;&nbsp;<font color="#000000">diff</font> <font color="#434f54">=</font> <font color="#000000">read_high</font> <font color="#434f54">-</font> <font color="#000000">read_low</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;desired answer is the difference between high and low.</font>


<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">println</font><font color="#000000">(</font><font color="#000000">diff</font><font color="#000000">)</font><font color="#000000">;</font>
<font color="#434f54">&#47;&#47;delay(100);</font>

<font color="#5e6d03">if</font> <font color="#000000">(</font><font color="#000000">diff</font><font color="#434f54">&gt;=</font><font color="#000000">25</font><font color="#000000">)</font> <font color="#000000">{</font>
 &nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47; turn LED on:</font>
 &nbsp;&nbsp;&nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">ledPin</font><font color="#434f54">,</font> <font color="#00979c">HIGH</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#000000">}</font> <font color="#5e6d03">else</font> <font color="#000000">{</font>
 &nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47; turn LED off:</font>
 &nbsp;&nbsp;&nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">ledPin</font><font color="#434f54">,</font> <font color="#00979c">LOW</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#000000">}</font> &nbsp;<font color="#000000">}</font>

</pre>


Problems:
This sensor is very difficult to work with. The soldering to the tape broke off on both pieces of tape, so I had to use conductive tape to reattatch the wire. But, the tape was not that strong so the wire sometimes shifts, changing values. The wire connected to the tape also snapped off at one point. 

Conductive tape-
![IMG_2223](https://user-images.githubusercontent.com/52216217/61652512-1c2fca80-ac86-11e9-9d6a-bd2b47220445.jpg)

The next problem that I had was stabilising the sensor on my computer. The values on the serial monitor changed even when the sensor was slightly disrupted. It was difficult to secure the sensor without disrupting any of the electrical tape. Also, when opening and closing my computer the sensor would move around. Even if one of the wires was at a slightly weird angle all of the sensor values would change or be inconsistent. The values would also change if the sensor touched my computer or the surface on which my computer was placed.

These factors made it really hard to find a stable value at which the computer was tilted enough to be “closed.” To calibrate the sensor, I recorded the values in 6 trials, and, inbetween each trial, I removed the sensor from the computer and placed it in the same spot to deomstrate inconsistencies. The varying values in these 6 trials are actually pretty tame compared to other values that I had when I was still working on the sensor before the lab (and did not record them). During that time, none of the values that I got made sense and there were random jumps in values when tilting my computer. In my calibration table I give the values of the serial monitor when my computer was at certain angles. The first value I recorded is the value that I received when my computer was closed as much as possible before the screen close and went black. The next was when the computer was tilted at 90 degrees, and the final was the value when I tilted my computer as far back as possible.

Table:

<img width="609" alt="Screen Shot 2019-07-23 at 12 09 07 PM" src="https://user-images.githubusercontent.com/52216217/61728201-c10fdd80-ad42-11e9-80ab-24fd7fac3699.png">

Final thoughts:
Once stabilised, the sensor works quite well. But, this is very difficult, and, if I move the computer around the sensor/values become unstable again. I worked on this before lab, during lab, and before class, and the values from the monitor changed each time I transported my computer. Rob says that if I solder very carefully, the readings will become more stable. however, I am not very confident in my soldering abilities since pretty much everything I have soldered in this class has broken off at one point. So, there probably is not much practical usage of this sensor, unless I find a secure way to mount the sensor without disrupting any of the values.
If I decide to use a tilt sensor in my final project I think that I will just use a tilt switch (with a rolling ball) like this one: https://www.adafruit.com/product/173 

![IMG_2218](https://user-images.githubusercontent.com/52216217/61652485-0c17eb00-ac86-11e9-9879-dd6f0ed6b511.jpg)

Here is a video of the sensor (the LED lightly faintly when the computer opens):
	
<video width="400" controls="">
		<source src="IMG_0612.TRIM 2_2 (1) (1).mp4" type="video/mp4">
	</video>
