---
layout: default
title:  "05: Programmable Electronics"
permalink: /05/
---

### Lab 5: 07/15/19

Today we worked on producing an output with an input button, a conditional statement, and a for loop. I created a timer using the Arduino Projects Book. In the book, I chose project #8, the digital hourglass. Since I did not have a tilt switch that was needed for the hourglass, I just made a timer instead using a regular button.

The circuit diagram that I used is here:
<img width="1232" alt="Screen Shot 2019-07-15 at 2 24 18 PM" src="https://user-images.githubusercontent.com/52216217/61239177-504a3f00-a70c-11e9-9d66-a855ad303fb4.png">

![IMG_1759](https://user-images.githubusercontent.com/52216217/61239246-78d23900-a70c-11e9-8cac-af48f15086b4.jpg)
Image 2: my circuit

The materials that I used were wires, 5 LED lights, a button, a 10 kilolm resistor, and five 220 ohm resistors.


The next thing that I did after wiring the board was upload the code into the Arduino. The code that I used is below:
<pre>
<font color="#00979c">const</font> <font color="#00979c">int</font> <font color="#000000">switchPin</font> <font color="#434f54">=</font> <font color="#000000">8</font><font color="#000000">;</font>
<font color="#00979c">unsigned</font> <font color="#00979c">long</font> <font color="#000000">previousTime</font> <font color="#434f54">=</font> <font color="#000000">0</font><font color="#000000">;</font>
<font color="#00979c">int</font> <font color="#000000">switchState</font> <font color="#434f54">=</font> <font color="#000000">0</font><font color="#000000">;</font>
<font color="#00979c">int</font> <font color="#000000">prevSwitchState</font> <font color="#434f54">=</font> <font color="#000000">0</font><font color="#000000">;</font>
<font color="#00979c">int</font> <font color="#000000">led</font> <font color="#434f54">=</font> <font color="#000000">2</font><font color="#000000">;</font>
<font color="#00979c">long</font> <font color="#000000">interval</font> <font color="#434f54">=</font> <font color="#000000">2000</font><font color="#000000">;</font>

<font color="#00979c">void</font> <font color="#5e6d03">setup</font><font color="#000000">(</font><font color="#000000">)</font> <font color="#000000">{</font>
 <font color="#5e6d03">for</font><font color="#000000">(</font><font color="#00979c">int</font> <font color="#000000">x</font> <font color="#434f54">=</font> <font color="#000000">2</font><font color="#000000">;</font><font color="#000000">x</font><font color="#434f54">&lt;</font><font color="#000000">8</font><font color="#000000">;</font><font color="#000000">x</font><font color="#434f54">++</font><font color="#000000">)</font><font color="#000000">{</font>
 <font color="#d35400">pinMode</font><font color="#000000">(</font><font color="#000000">x</font><font color="#434f54">,</font> <font color="#00979c">OUTPUT</font><font color="#000000">)</font><font color="#000000">;</font>
 <font color="#000000">}</font>
 <font color="#d35400">pinMode</font><font color="#000000">(</font><font color="#000000">switchPin</font><font color="#434f54">,</font> <font color="#00979c">INPUT</font><font color="#000000">)</font><font color="#000000">;</font>
<font color="#000000">}</font>

<font color="#00979c">void</font> <font color="#5e6d03">loop</font><font color="#000000">(</font><font color="#000000">)</font><font color="#000000">{</font>
 <font color="#00979c">unsigned</font> <font color="#00979c">long</font> <font color="#000000">currentTime</font> <font color="#434f54">=</font> <font color="#d35400">millis</font><font color="#000000">(</font><font color="#000000">)</font><font color="#000000">;</font>
 <font color="#5e6d03">if</font><font color="#000000">(</font><font color="#000000">currentTime</font> <font color="#434f54">-</font> <font color="#000000">previousTime</font> <font color="#434f54">&gt;</font> <font color="#000000">interval</font><font color="#000000">)</font> <font color="#000000">{</font>
 <font color="#000000">previousTime</font> <font color="#434f54">=</font> <font color="#000000">currentTime</font><font color="#000000">;</font>
 <font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">led</font><font color="#434f54">,</font> <font color="#00979c">HIGH</font><font color="#000000">)</font><font color="#000000">;</font>
 <font color="#000000">led</font><font color="#434f54">++</font><font color="#000000">;</font>
 <font color="#5e6d03">if</font><font color="#000000">(</font><font color="#000000">led</font> <font color="#434f54">==</font> <font color="#000000">7</font><font color="#000000">)</font><font color="#000000">{</font>
 <font color="#000000">}</font>
 <font color="#000000">}</font>
 <font color="#000000">switchState</font> <font color="#434f54">=</font> <font color="#d35400">digitalRead</font><font color="#000000">(</font><font color="#000000">switchPin</font><font color="#000000">)</font><font color="#000000">;</font>
 <font color="#5e6d03">if</font><font color="#000000">(</font><font color="#000000">switchState</font> <font color="#434f54">!=</font> <font color="#000000">prevSwitchState</font><font color="#000000">)</font><font color="#000000">{</font>
 <font color="#5e6d03">for</font><font color="#000000">(</font><font color="#00979c">int</font> <font color="#000000">x</font> <font color="#434f54">=</font> <font color="#000000">2</font><font color="#000000">;</font><font color="#000000">x</font><font color="#434f54">&lt;</font><font color="#000000">8</font><font color="#000000">;</font><font color="#000000">x</font><font color="#434f54">++</font><font color="#000000">)</font><font color="#000000">{</font>
 <font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">x</font><font color="#434f54">,</font> <font color="#00979c">LOW</font><font color="#000000">)</font><font color="#000000">;</font>
 <font color="#000000">}</font>
 <font color="#000000">led</font> <font color="#434f54">=</font> <font color="#000000">2</font><font color="#000000">;</font>
 <font color="#000000">previousTime</font> <font color="#434f54">=</font> <font color="#000000">currentTime</font><font color="#000000">;</font>
 <font color="#000000">}</font>
 <font color="#000000">prevSwitchState</font> <font color="#434f54">=</font> <font color="#000000">switchState</font><font color="#000000">;</font>
<font color="#000000">}</font>

</pre>


Essentially, my circuit turns on lights periodically by using delays. The delay between lights can be adjusted in the line “long interval = 2000;” by changing the numeric value (in milliseconds). For my circuit, I made the delay 2000 miliseconds, or 2 seconds, so that the entire circuit would be a 10 second timer. After 10 seconds is over, the lights stay on and the timer runs again when the button is pressed. Something that I noticed is that there is a delay between pressing the button and the light turning on. Also, the delays vary in real time between each light turning on, but it takes 10 seconds total for all the lights to turn on. So, the delay essentially varys per light, but overall the timer works well because it takes 10 seconds for the light to turn on. 

Here is a video of my final result:
<video width="400" controls="">
		<source src="IMG_1761.TRIM 2_2.mp4" type="video/mp4">
	</video>


What I learned: 
Overall, I gained more experience in programming an Arduino. I do not have much background in using Arudinos or programming, so it was very interesting to be exposed to the Arduino’s capabilities. I learned about for loops, conditional statements, input, and output. I also practiced declaring pins and, in general, writing code. The project book was very helpful in explaining what each line of code does, clarifying many things. 
I think that I could potentially use a tilt switch in my final project. I could program my buzzer and vibrator to turn on when the tilt switch turns on. I could use the switch by attatching it onto my computer screen to detect when the computer is flipped on. The code would be similar to this; instead of turning on LEDs I would just turn on the vibrator and buzzer instead.

If you would like to try some of the projects, here is the book link: https://bastiaanvanhengel.files.wordpress.com/2016/06/arduino_projects_book.pdf. It offers great tutorials for beginners and introduces new concepts.
