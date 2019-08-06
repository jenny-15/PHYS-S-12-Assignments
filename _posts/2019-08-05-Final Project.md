---
layout: default
title:  "Final Project"
permalink: /12/
---

### Final Project
			
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
body {font-family: Arial;} 

/* Style the tab */
.tab {
  overflow: hidden;
  border: 1px solid #ccc;
  background-color: #f1f1f1;
}

/* Style the buttons inside the tab */
.tab button {
  background-color: inherit;
  float: left;
  border: none;
  outline: none;
  cursor: pointer;
  padding: 14px 16px;
  transition: 0.3s;
  font-size: 17px;
}

/* Change background color of buttons on hover */
.tab button:hover {
  background-color: #ddd;
}

/* Create an active/current tablink class */
.tab button.active {
  background-color: #ccc;
}

/* Style the tab content */
.tabcontent {
  display: none;
  padding: 6px 12px;
  border: 1px solid #ccc;
  border-top: none;
}
</style>
</head>
<body>

<h2>Tabs</h2>
<p> Click on the buttons inside the tabbed menu:</p>


<div class="tab">
  <button class="tablinks" onclick="openCity(event, 'Final Project Original Plan')">Final Project Original Plan</button>
  <button class="tablinks" onclick="openCity(event, 'Final Project Plan 2')">Final Project Plan 2</button>
	<button class="tablinks" onclick="openCity(event, 'Final Plan')">Final Plan</button>
	<button class="tablinks" onclick="openCity(event, 'Project Update 07/31')">Project Update 07/31</button>
	<button class="tablinks" onclick="openCity(event, 'Progress')">Progress</button>
</div>


<div id="Final Project Original Plan" class="tabcontent">
  <h3>Final Project Original Plan</h3>
  <p> <iframe src="https://docs.google.com/document/d/1lwFWprxDkQgblWIpog1j_dIiaDs_jzjJ_5lyDi-J3wg/edit?usp=sharing" style="width:600px; height:500px;" frameborder="0"></iframe>

</p>
</div>

<div id="Final Project Plan 2" class="tabcontent">
  <h3>Final Project Plan 2</h3>
  <p> 
	  
<iframe src="https://docs.google.com/document/d/1g7VfImK2Aelp6CDwWc0NSYQ_VkU76Y93SXhcfRu0560" style="width:600px; height:500px;" frameborder="0"></iframe>

 </p> 
</div>

<div id="Final Plan" class="tabcontent">
  <h3>Final Plan</h3>
	
  <p> <iframe src="https://docs.google.com/document/d/1iUxP3WUQkKK1ayuvKkRupLUH8T-d88zNqGBm1yYudVE/edit?usp=sharing" frameborder="0"></iframe> </p>
</div>

<div id="Project Update 07/31" class="tabcontent">
  <h3>Project Update 07/31</h3>
  <p> <iframe src="https://docs.google.com/document/d/1-LVbl4_siurPn3JIq2tPXhH4YKHk0wKiKJPSXjMJ0pI/edit?usp=sharing" frameborder="0"></iframe>  </p>
</div>

<div id="Progress" class="tabcontent">
  <h3>Progress</h3>
  <p  
     <iframe src=" https://docs.google.com/document/d/139E958er5j9MPKxyXhbfnbgA3y83sf7eP6fXaIT4rO4/edit?usp=sharing" style="width:600px; height:500px;" frameborder="0"></iframe>  
     Today I finished my circuit and code, changed my Arduino Uno’s to Arduino Micro’s, soldered my vibration motor, and began working on soldering my protoboard.

I made a few tweaks to the transmitter and receiver code, which are attached below.
Transmitter-
<pre>
<font color="#5e6d03">#include</font> <font color="#434f54">&lt;</font><b><font color="#d35400">SPI</font></b><font color="#434f54">.</font><font color="#000000">h</font><font color="#434f54">&gt;</font>
<font color="#5e6d03">#include</font> <font color="#434f54">&lt;</font><font color="#000000">nRF24L01</font><font color="#434f54">.</font><font color="#000000">h</font><font color="#434f54">&gt;</font>
<font color="#5e6d03">#include</font> <font color="#434f54">&lt;</font><b><font color="#d35400">RF24</font></b><font color="#434f54">.</font><font color="#000000">h</font><font color="#434f54">&gt;</font>
<b><font color="#d35400">RF24</font></b> <font color="#000000">radio</font><font color="#000000">(</font><font color="#000000">9</font><font color="#434f54">,</font> <font color="#000000">10</font><font color="#000000">)</font><font color="#000000">;</font> <font color="#434f54">&#47;&#47; CE, CSN</font>
<font color="#00979c">const</font> <font color="#00979c">byte</font> <font color="#000000">address</font><font color="#000000">[</font><font color="#000000">6</font><font color="#000000">]</font> <font color="#434f54">=</font> <font color="#005c5f">&#34;00001&#34;</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Byte of array representing the address. This is the address where we will send the data. This should be same on the receiving side.</font>
<font color="#00979c">int</font> <font color="#000000">tilt_pin</font> <font color="#434f54">=</font> <font color="#000000">7</font><font color="#000000">;</font>
<font color="#00979c">boolean</font> <font color="#000000">tilt_state</font> <font color="#434f54">=</font> <font color="#000000">0</font><font color="#000000">;</font>
<font color="#00979c">int</font> <font color="#000000">LED</font> <font color="#434f54">=</font> <font color="#000000">2</font><font color="#000000">;</font>

<font color="#00979c">const</font> <font color="#00979c">int</font> <font color="#000000">switchPin</font> <font color="#434f54">=</font> <font color="#000000">6</font><font color="#000000">;</font>
<font color="#00979c">int</font> <font color="#000000">switchState</font> <font color="#434f54">=</font> <font color="#000000">0</font><font color="#000000">;</font>

<font color="#00979c">int</font> <font color="#000000">outPin</font> <font color="#434f54">=</font> <font color="#000000">4</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47; LED</font>


<font color="#00979c">boolean</font> <font color="#000000">oldSwitchState</font> <font color="#434f54">=</font> <font color="#00979c">LOW</font><font color="#000000">;</font>
<font color="#00979c">boolean</font> <font color="#000000">newSwitchState1</font> <font color="#434f54">=</font> <font color="#00979c">LOW</font><font color="#000000">;</font>
<font color="#00979c">boolean</font> <font color="#000000">LEDstatus</font> <font color="#434f54">=</font> <font color="#00979c">LOW</font><font color="#000000">;</font>


<font color="#00979c">void</font> <font color="#5e6d03">setup</font><font color="#000000">(</font><font color="#000000">)</font> <font color="#000000">{</font>
 &nbsp;<font color="#000000">{</font>
 &nbsp;&nbsp;&nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">begin</font><font color="#000000">(</font><font color="#000000">9600</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">print</font><font color="#000000">(</font><font color="#005c5f">&#34;Sketch: &nbsp;&nbsp;&#34;</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">println</font><font color="#000000">(</font><font color="#5e6d03">__FILE__</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">print</font><font color="#000000">(</font><font color="#005c5f">&#34;Uploaded: &#34;</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">println</font><font color="#000000">(</font><font color="#5e6d03">__DATE__</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">println</font><font color="#000000">(</font><font color="#005c5f">&#34; &#34;</font><font color="#000000">)</font><font color="#000000">;</font>

 &nbsp;&nbsp;&nbsp;<font color="#d35400">pinMode</font><font color="#000000">(</font><font color="#000000">outPin</font><font color="#434f54">,</font> <font color="#00979c">OUTPUT</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">outPin</font><font color="#434f54">,</font> <font color="#00979c">LOW</font><font color="#000000">)</font><font color="#000000">;</font>

 &nbsp;&nbsp;&nbsp;<font color="#d35400">pinMode</font><font color="#000000">(</font><font color="#000000">switchPin</font><font color="#434f54">,</font> <font color="#00979c">INPUT_PULLUP</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#000000">}</font>
 &nbsp;<font color="#000000">{</font>
 &nbsp;&nbsp;&nbsp;<font color="#d35400">pinMode</font><font color="#000000">(</font><font color="#000000">tilt_pin</font><font color="#434f54">,</font> <font color="#00979c">INPUT_PULLUP</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;<font color="#000000">radio</font><font color="#434f54">.</font><font color="#d35400">begin</font><font color="#000000">(</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Starting the Wireless communication</font>
 &nbsp;&nbsp;&nbsp;<font color="#000000">radio</font><font color="#434f54">.</font><font color="#d35400">openWritingPipe</font><font color="#000000">(</font><font color="#000000">address</font> <font color="#000000">)</font><font color="#000000">;</font> <font color="#434f54">&#47;&#47;Setting the address where we will send the data</font>
 &nbsp;&nbsp;&nbsp;<font color="#000000">radio</font><font color="#434f54">.</font><font color="#000000">setPALevel</font><font color="#000000">(</font><font color="#000000">RF24_PA_MIN</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;<font color="#434f54">&#47;&#47;You can set it as minimum or maximum depending on the distance between the transmitter and receiver.</font>
 &nbsp;&nbsp;&nbsp;<font color="#000000">radio</font><font color="#434f54">.</font><font color="#d35400">stopListening</font><font color="#000000">(</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;This sets the module as transmitter</font>
 &nbsp;<font color="#000000">}</font>
<font color="#000000">}</font>
<font color="#00979c">void</font> <font color="#5e6d03">loop</font><font color="#000000">(</font><font color="#000000">)</font> <font color="#000000">{</font>

 &nbsp;<font color="#000000">newSwitchState1</font> <font color="#434f54">=</font> <font color="#d35400">digitalRead</font><font color="#000000">(</font><font color="#000000">switchPin</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">delay</font><font color="#000000">(</font><font color="#000000">1</font><font color="#000000">)</font><font color="#000000">;</font>

 &nbsp;<font color="#5e6d03">if</font> <font color="#000000">(</font> <font color="#000000">newSwitchState1</font> <font color="#434f54">!=</font> <font color="#000000">oldSwitchState</font> <font color="#000000">)</font>
 &nbsp;<font color="#000000">{</font>

 &nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47; has the button switch been closed?</font>
 &nbsp;&nbsp;&nbsp;<font color="#5e6d03">if</font> <font color="#000000">(</font> <font color="#000000">newSwitchState1</font> <font color="#434f54">==</font> <font color="#00979c">HIGH</font> <font color="#000000">)</font>
 &nbsp;&nbsp;&nbsp;<font color="#000000">{</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#5e6d03">if</font> <font color="#000000">(</font> <font color="#000000">LEDstatus</font> <font color="#434f54">==</font> <font color="#00979c">LOW</font> <font color="#000000">)</font> <font color="#000000">{</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">outPin</font><font color="#434f54">,</font> <font color="#00979c">HIGH</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#000000">LEDstatus</font> <font color="#434f54">=</font> <font color="#00979c">HIGH</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#000000">}</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#5e6d03">else</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#000000">{</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">outPin</font><font color="#434f54">,</font> <font color="#00979c">LOW</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#000000">LEDstatus</font> <font color="#434f54">=</font> <font color="#00979c">LOW</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#000000">}</font>
 &nbsp;&nbsp;&nbsp;<font color="#000000">}</font>
 &nbsp;&nbsp;&nbsp;<font color="#000000">oldSwitchState</font> <font color="#434f54">=</font> <font color="#000000">newSwitchState1</font><font color="#000000">;</font>
 &nbsp;<font color="#000000">}</font>

 &nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">print</font><font color="#000000">(</font><font color="#005c5f">&#34;tilt: &#34;</font><font color="#000000">)</font><font color="#000000">;</font> <b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">println</font><font color="#000000">(</font><font color="#000000">tilt_state</font><font color="#000000">)</font><font color="#000000">;</font>


 &nbsp;<font color="#5e6d03">if</font> <font color="#000000">(</font><font color="#000000">LEDstatus</font> <font color="#434f54">==</font> <font color="#00979c">HIGH</font><font color="#000000">)</font> <font color="#000000">{</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47; if laptop is closed </font>
 &nbsp;&nbsp;&nbsp;<font color="#000000">tilt_state</font> <font color="#434f54">=</font> <font color="#d35400">digitalRead</font><font color="#000000">(</font><font color="#000000">tilt_pin</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;<font color="#000000">radio</font><font color="#434f54">.</font><font color="#d35400">write</font><font color="#000000">(</font><font color="#434f54">&amp;</font><font color="#000000">tilt_state</font><font color="#434f54">,</font> <font color="#00979c">sizeof</font><font color="#000000">(</font><font color="#000000">tilt_state</font><font color="#000000">)</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;<font color="#5e6d03">if</font> <font color="#000000">(</font><font color="#000000">tilt_state</font> <font color="#434f54">==</font> <font color="#00979c">HIGH</font><font color="#000000">)</font>
 &nbsp;&nbsp;&nbsp;<font color="#000000">{</font>
 &nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47; const char text[] = &#34;Your Button State is OFF&#34;;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47; radio.write(&amp;tilt_state, sizeof(tilt_state));</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;radio.write(&amp;text, sizeof(text)); &nbsp;&nbsp;&nbsp;&#47;&#47;Sending the message to receiver</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">digitalWrite</font> <font color="#000000">(</font><font color="#000000">LED</font><font color="#434f54">,</font> <font color="#00979c">HIGH</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;<font color="#000000">}</font>
 &nbsp;&nbsp;&nbsp;<font color="#5e6d03">else</font> <font color="#000000">{</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;const char text[] = &#34;Your Button State is ON&#34;;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;radio.write(&amp;text, sizeof(text)); &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#47;&#47;Sending the message to receiver</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">digitalWrite</font> <font color="#000000">(</font><font color="#000000">LED</font><font color="#434f54">,</font> <font color="#00979c">LOW</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;<font color="#000000">}</font>
 &nbsp;<font color="#000000">}</font>

<font color="#000000">}</font>

</pre>

Receiver-
<pre>
<font color="#5e6d03">#include</font> <font color="#434f54">&lt;</font><b><font color="#d35400">SPI</font></b><font color="#434f54">.</font><font color="#000000">h</font><font color="#434f54">&gt;</font>
<font color="#5e6d03">#include</font> <font color="#434f54">&lt;</font><font color="#000000">nRF24L01</font><font color="#434f54">.</font><font color="#000000">h</font><font color="#434f54">&gt;</font>
<font color="#5e6d03">#include</font> <font color="#434f54">&lt;</font><b><font color="#d35400">RF24</font></b><font color="#434f54">.</font><font color="#000000">h</font><font color="#434f54">&gt;</font>
<font color="#00979c">const</font> <font color="#00979c">int</font> <font color="#000000">buzzer</font> <font color="#434f54">=</font> <font color="#000000">5</font><font color="#000000">;</font> <font color="#434f54">&#47;&#47;buzzer to arduino pin 5</font>
<b><font color="#d35400">RF24</font></b> <font color="#000000">radio</font><font color="#000000">(</font><font color="#000000">9</font><font color="#434f54">,</font> <font color="#000000">10</font><font color="#000000">)</font><font color="#000000">;</font> <font color="#434f54">&#47;&#47; CE, CSN</font>
<font color="#00979c">const</font> <font color="#00979c">byte</font> <font color="#000000">address</font><font color="#000000">[</font><font color="#000000">6</font><font color="#000000">]</font> <font color="#434f54">=</font> <font color="#005c5f">&#34;00001&#34;</font><font color="#000000">;</font>
<font color="#00979c">boolean</font> <font color="#000000">tilt_state</font> <font color="#434f54">=</font> <font color="#000000">0</font><font color="#000000">;</font>

<font color="#00979c">void</font> <font color="#5e6d03">setup</font><font color="#000000">(</font><font color="#000000">)</font> <font color="#000000">{</font>
 &nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">begin</font><font color="#000000">(</font><font color="#000000">9600</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#000000">radio</font><font color="#434f54">.</font><font color="#d35400">begin</font><font color="#000000">(</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#000000">radio</font><font color="#434f54">.</font><font color="#d35400">openReadingPipe</font><font color="#000000">(</font><font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">address</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;<font color="#434f54">&#47;&#47;Setting the address at which we will receive the data</font>
 &nbsp;<font color="#000000">radio</font><font color="#434f54">.</font><font color="#000000">setPALevel</font><font color="#000000">(</font><font color="#000000">RF24_PA_MIN</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;You can set this as minimum or maximum depending on the distance between the transmitter and receiver.</font>
 &nbsp;<font color="#000000">radio</font><font color="#434f54">.</font><font color="#d35400">startListening</font><font color="#000000">(</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;This sets the module as receiver</font>
 &nbsp;<font color="#d35400">pinMode</font><font color="#000000">(</font><font color="#000000">buzzer</font><font color="#434f54">,</font> <font color="#00979c">OUTPUT</font><font color="#000000">)</font><font color="#000000">;</font> <font color="#434f54">&#47;&#47; Set buzzer - pin 5 as an output</font>
 &nbsp;<font color="#d35400">pinMode</font><font color="#000000">(</font> <font color="#000000">6</font> <font color="#434f54">,</font> <font color="#00979c">OUTPUT</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;<font color="#434f54">&#47;&#47; Must be a PWM pin</font>
<font color="#000000">}</font>
<font color="#00979c">void</font> <font color="#5e6d03">loop</font><font color="#000000">(</font><font color="#000000">)</font>

<font color="#000000">{</font>

 &nbsp;<font color="#5e6d03">if</font> <font color="#000000">(</font><font color="#000000">radio</font><font color="#434f54">.</font><font color="#d35400">available</font><font color="#000000">(</font><font color="#000000">)</font><font color="#000000">)</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Looking for the data.</font>
 &nbsp;<font color="#000000">{</font>
 &nbsp;&nbsp;&nbsp;<font color="#00979c">char</font> <font color="#000000">text</font><font color="#000000">[</font><font color="#000000">32</font><font color="#000000">]</font> <font color="#434f54">=</font> <font color="#005c5f">&#34;&#34;</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Saving the incoming data</font>
 &nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;radio.read(&amp;text, sizeof(text)); &nbsp;&nbsp;&nbsp;&#47;&#47;Reading the data</font>
 &nbsp;&nbsp;&nbsp;<font color="#000000">radio</font><font color="#434f54">.</font><font color="#d35400">read</font><font color="#000000">(</font><font color="#434f54">&amp;</font><font color="#000000">tilt_state</font><font color="#434f54">,</font> <font color="#00979c">sizeof</font><font color="#000000">(</font><font color="#000000">tilt_state</font><font color="#000000">)</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Reading the data</font>
 &nbsp;&nbsp;&nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">println</font><font color="#000000">(</font><font color="#000000">tilt_state</font><font color="#000000">)</font><font color="#000000">;</font>

 &nbsp;&nbsp;&nbsp;<font color="#5e6d03">if</font> <font color="#000000">(</font><font color="#000000">tilt_state</font> <font color="#434f54">==</font> <font color="#00979c">LOW</font><font color="#000000">)</font> <font color="#434f54">&#47;&#47;when tilt swtich is on</font>
 &nbsp;&nbsp;&nbsp;<font color="#000000">{</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Serial.print(&#34;switch: &#34;); Serial.println(tilt_state);</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">println</font><font color="#000000">(</font><font color="#000000">text</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">tone</font><font color="#000000">(</font><font color="#000000">buzzer</font><font color="#434f54">,</font> <font color="#000000">1000</font><font color="#000000">)</font><font color="#000000">;</font> <font color="#434f54">&#47;&#47; Send 1KHz sound signal...</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">analogWrite</font><font color="#000000">(</font> <font color="#000000">6</font> <font color="#434f54">,</font> <font color="#000000">153</font> <font color="#000000">)</font><font color="#000000">;</font> &nbsp;<font color="#434f54">&#47;&#47; 60% duty cycle</font>
 &nbsp;&nbsp;&nbsp;<font color="#000000">}</font>
 &nbsp;&nbsp;&nbsp;<font color="#5e6d03">else</font> <font color="#434f54">&#47;&#47;when tilt switch is off</font>
 &nbsp;&nbsp;&nbsp;<font color="#000000">{</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Serial.print(&#34;should be off: &#34;);</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Serial.println(text);</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">noTone</font><font color="#000000">(</font><font color="#000000">buzzer</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47; Stop sound...</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">analogWrite</font><font color="#000000">(</font> <font color="#000000">6</font> <font color="#434f54">,</font> <font color="#000000">0</font> <font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47; 0% duty cycle (off)</font>
 &nbsp;&nbsp;&nbsp;<font color="#000000">}</font>
 &nbsp;<font color="#000000">}</font>
 &nbsp;<font color="#5e6d03">else</font> <font color="#000000">{</font>
 &nbsp;&nbsp;&nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">print</font><font color="#000000">(</font><font color="#005c5f">&#34;no signal &#34;</font><font color="#000000">)</font><font color="#000000">;</font> <font color="#434f54">&#47;&#47;if it does not receive anything</font>
 &nbsp;&nbsp;&nbsp;<font color="#d35400">noTone</font><font color="#000000">(</font><font color="#000000">buzzer</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47; Stop sound...</font>
 &nbsp;&nbsp;&nbsp;<font color="#d35400">analogWrite</font><font color="#000000">(</font> <font color="#000000">6</font> <font color="#434f54">,</font> <font color="#000000">0</font> <font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47; 0% duty cycle (off)</font>
 &nbsp;<font color="#000000">}</font> 
 &nbsp;<font color="#d35400">delay</font><font color="#000000">(</font><font color="#000000">10</font><font color="#000000">)</font><font color="#000000">;</font>
<font color="#000000">}</font>

</pre>


After finishing with the circuit, I swapped out the Arduino Uno’s with Micro’s to save space. 

Finished circuit:
<img src="IMG_2570.jpg" alt="IMG_2570" 

![IMG_2570](https://user-images.githubusercontent.com/52216217/62416794-3915b780-b60f-11e9-8f65-e406465e831c.jpg)
![IMG_2561](https://user-images.githubusercontent.com/52216217/62416795-3a46e480-b60f-11e9-8098-58c8046ab548.jpg)
![IMG_2567](https://user-images.githubusercontent.com/52216217/62416796-3b781180-b60f-11e9-94cb-dfc7f76b2438.jpg)


Video of circuit:
<video width="" controls="">
		<source src="IMG_2457.mp4" type="video/mp4">
	</video>

I also had to solder my vibration motor again. It broke off once again. This time, Nathan helped me, and I used heat shrink tubing and hot glue to keep everything in place.
![IMG_2552](https://user-images.githubusercontent.com/52216217/62416802-59457680-b60f-11e9-9e75-87945394bc88.jpg)
![IMG_2553](https://user-images.githubusercontent.com/52216217/62416803-5c406700-b60f-11e9-99d3-4f63f1c784b8.jpg)
![IMG_2555](https://user-images.githubusercontent.com/52216217/62416805-5e0a2a80-b60f-11e9-87c0-739e0e31224e.jpg)



</p>
</div>

<script>
function openCity(evt, cityName) {
  var i, tabcontent, tablinks;
  tabcontent = document.getElementsByClassName("tabcontent");
  for (i = 0; i < tabcontent.length; i++) {
    tabcontent[i].style.display = "none";
  }
  tablinks = document.getElementsByClassName("tablinks");
  for (i = 0; i < tablinks.length; i++) {
    tablinks[i].className = tablinks[i].className.replace(" active", "");
  }
  document.getElementById(cityName).style.display = "block";
  evt.currentTarget.className += " active";
}
</script>
   
</body>
</html> 
