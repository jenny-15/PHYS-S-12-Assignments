---
layout: default
title:  "09: Electronic Output Devices"
permalink: /09/
---

### 09: Electronic Output Devices-July 29

During this lab we worked with electronic output devices. I chose to use the Arduino nRF24L01, a radio module, to transmit between two Arduinos.The two circuits on both Arduinos are the same, but the code is slightly different. The objective is to get a LED to light on one Arduino when a button on the other is pressed and vice versa.

The diagram I used to set up the circuit is below:


The materials that you will need are 2 Arduino Unos, wires, 2 LEDs, 2 220 ohm resistors, and 2 10k ohm resistors. 


After setting up the circuits, I programmed the two Arduinos with slightly different codes. It does not particularly matter which code goes into which Arduino since the circuit and function is the same. 


Code:
Arduino 1-
<pre class="hljs arduino"><code><span><span class="hljs-meta">#<span class="hljs-meta-keyword">include</span> <span class="hljs-meta-string">&lt;SPI.h&gt;</span></span>
</span><span><span class="hljs-meta">#<span class="hljs-meta-keyword">include</span> <span class="hljs-meta-string">&lt;nRF24L01.h&gt;</span></span>
</span><span><span class="hljs-meta">#<span class="hljs-meta-keyword">include</span> <span class="hljs-meta-string">&lt;RF24.h&gt;</span></span>
</span><span>RF24 radio(<span class="hljs-number">9</span>, <span class="hljs-number">10</span>); <span class="hljs-comment">// CE, CSN</span>
</span><span><span class="hljs-keyword">const</span> <span class="hljs-keyword">byte</span> addresses [][<span class="hljs-number">6</span>] = {<span class="hljs-string">"00001"</span>, <span class="hljs-string">"00002"</span>};  <span class="hljs-comment">//Setting&nbsp;the&nbsp;two&nbsp;addresses.&nbsp;One&nbsp;for&nbsp;transmitting&nbsp;and&nbsp;one&nbsp;for&nbsp;receiving</span>
</span><span><span class="hljs-keyword">int</span> button_pin = <span class="hljs-number">2</span>;
</span><span><span class="hljs-keyword">int</span> led_pin = <span class="hljs-number">3</span>;
</span><span><span class="hljs-keyword">boolean</span> button_state = <span class="hljs-number">0</span>;
</span><span><span class="hljs-keyword">boolean</span> button_state1 = <span class="hljs-number">0</span>;
</span><span><span class="hljs-keyword">void</span> <span class="hljs-built_in">setup</span>() {
</span><span>  <span class="hljs-built_in">pinMode</span>(button_pin, <span class="hljs-literal">INPUT</span>);
</span><span>  <span class="hljs-built_in">pinMode</span>(led_pin, <span class="hljs-literal">OUTPUT</span>);
</span><span>  radio.<span class="hljs-built_in">begin</span>();                           <span class="hljs-comment">//Starting&nbsp;the&nbsp;radio&nbsp;communication</span>
</span><span>  radio.openWritingPipe(addresses[<span class="hljs-number">1</span>]);     <span class="hljs-comment">//Setting&nbsp;the&nbsp;address&nbsp;at&nbsp;which&nbsp;we&nbsp;will&nbsp;send&nbsp;the&nbsp;data</span>
</span><span>  radio.openReadingPipe(<span class="hljs-number">1</span>, addresses[<span class="hljs-number">0</span>]);  <span class="hljs-comment">//Setting&nbsp;the&nbsp;address&nbsp;at&nbsp;which&nbsp;we&nbsp;will&nbsp;receive&nbsp;the&nbsp;data</span>
</span><span>  radio.setPALevel(RF24_PA_MIN); <span class="hljs-comment">//You&nbsp;can&nbsp;set&nbsp;it&nbsp;as&nbsp;minimum&nbsp;or&nbsp;maximum&nbsp;depending&nbsp;on&nbsp;the&nbsp;distance&nbsp;between&nbsp;the&nbsp;transmitter&nbsp;and&nbsp;receiver.&nbsp;</span>
</span><span>}
</span><span><span class="hljs-keyword">void</span> <span class="hljs-built_in">loop</span>() 
</span><span>{  
</span><span>  <span class="hljs-built_in">delay</span>(<span class="hljs-number">5</span>);
</span><span>  radio.stopListening();                             <span class="hljs-comment">//This&nbsp;sets&nbsp;the&nbsp;module&nbsp;as&nbsp;transmitter</span>
</span><span>  button_state = <span class="hljs-built_in">digitalRead</span>(button_pin);
</span><span>  radio.<span class="hljs-built_in">write</span>(&amp;button_state, <span class="hljs-keyword">sizeof</span>(button_state));  <span class="hljs-comment">//Sending the data</span>
</span><span>  <span class="hljs-built_in">delay</span>(<span class="hljs-number">5</span>);
</span><span>  
</span><span>  radio.startListening();                            <span class="hljs-comment">//This&nbsp;sets&nbsp;the&nbsp;module&nbsp;as&nbsp;receiver</span>
</span><span>  <span class="hljs-built_in">while</span>(!radio.<span class="hljs-built_in">available</span>());                         <span class="hljs-comment">//Looking for incoming data</span>
</span><span>  radio.<span class="hljs-built_in">read</span>(&amp;button_state1, <span class="hljs-keyword">sizeof</span>(button_state1)); <span class="hljs-comment">//Reading the data</span>
</span><span>  <span class="hljs-built_in">if</span> (button_state1 == <span class="hljs-literal">HIGH</span>)
</span><span>  {
</span><span>    <span class="hljs-built_in">digitalWrite</span>(led_pin, <span class="hljs-literal">HIGH</span>);
</span><span>  }
</span><span>  <span class="hljs-built_in">else</span>
</span><span>  {
</span><span>    <span class="hljs-built_in">digitalWrite</span>(led_pin, <span class="hljs-literal">LOW</span>);
</span><span>  }
</span><span>}
</span></code></pre>


Arduino 2-
<pre class="hljs arduino"><code><span><span class="hljs-meta">#<span class="hljs-meta-keyword">include</span> <span class="hljs-meta-string">&lt;SPI.h&gt;</span></span>
</span><span><span class="hljs-meta">#<span class="hljs-meta-keyword">include</span> <span class="hljs-meta-string">&lt;nRF24L01.h&gt;</span></span>
</span><span><span class="hljs-meta">#<span class="hljs-meta-keyword">include</span> <span class="hljs-meta-string">&lt;RF24.h&gt;</span></span>
</span><span>RF24 radio(<span class="hljs-number">9</span>, <span class="hljs-number">10</span>); <span class="hljs-comment">// CE, CSN</span>
</span><span><span class="hljs-keyword">const</span> <span class="hljs-keyword">byte</span> addresses [][<span class="hljs-number">6</span>] = {<span class="hljs-string">"00001"</span>, <span class="hljs-string">"00002"</span>};    <span class="hljs-comment">//Setting the two addresses. One for transmitting and one for receiving</span>
</span><span><span class="hljs-keyword">int</span> button_pin = <span class="hljs-number">2</span>;
</span><span><span class="hljs-keyword">boolean</span> button_state = <span class="hljs-number">0</span>;
</span><span><span class="hljs-keyword">boolean</span> button_state1 = <span class="hljs-number">0</span>;
</span><span><span class="hljs-keyword">int</span> led_pin = <span class="hljs-number">3</span>;
</span><span><span class="hljs-keyword">void</span> <span class="hljs-built_in">setup</span>() {
</span><span>  <span class="hljs-built_in">pinMode</span>(led_pin, <span class="hljs-literal">OUTPUT</span>);
</span><span>  <span class="hljs-built_in">Serial</span>.<span class="hljs-built_in">begin</span>(<span class="hljs-number">9600</span>);
</span><span>  radio.<span class="hljs-built_in">begin</span>();                            <span class="hljs-comment">//Starting the radio communication</span>
</span><span>  radio.openWritingPipe(addresses[<span class="hljs-number">0</span>]);      <span class="hljs-comment">//Setting the address at which we will send the data</span>
</span><span>  radio.openReadingPipe(<span class="hljs-number">1</span>, addresses[<span class="hljs-number">1</span>]);   <span class="hljs-comment">//Setting the address at which we will receive the data</span>
</span><span>  radio.setPALevel(RF24_PA_MIN);            <span class="hljs-comment">//You can set it as minimum or maximum depending on the distance between the transmitter and receiver.</span>
</span><span>}
</span><span><span class="hljs-keyword">void</span> <span class="hljs-built_in">loop</span>() 
</span><span>{
</span><span>  <span class="hljs-built_in">delay</span>(<span class="hljs-number">5</span>);
</span><span>  radio.startListening();                    <span class="hljs-comment">//This sets the module as receiver</span>
</span><span>  <span class="hljs-built_in">if</span> (radio.<span class="hljs-built_in">available</span>())                     <span class="hljs-comment">//Looking for incoming data</span>
</span><span>  {
</span><span>    radio.<span class="hljs-built_in">read</span>(&amp;button_state, <span class="hljs-keyword">sizeof</span>(button_state));
</span><span>    <span class="hljs-built_in">if</span>(button_state == <span class="hljs-literal">HIGH</span>)
</span><span>  {
</span><span>     <span class="hljs-built_in">digitalWrite</span>(led_pin, <span class="hljs-literal">HIGH</span>);
</span><span>  }
</span><span>  <span class="hljs-built_in">else</span>
</span><span>  {
</span><span>     <span class="hljs-built_in">digitalWrite</span>(led_pin, <span class="hljs-literal">LOW</span>);
</span><span>  }
</span><span>  <span class="hljs-built_in">delay</span>(<span class="hljs-number">5</span>);
</span><span>  
</span><span>  radio.stopListening();                           <span class="hljs-comment">//This sets the module as transmitter</span>
</span><span>  button_state1 = <span class="hljs-built_in">digitalRead</span>(button_pin);
</span><span>  radio.<span class="hljs-built_in">write</span>(&amp;button_state1, <span class="hljs-keyword">sizeof</span>(button_state1));   <span class="hljs-comment">//Sending the data</span>
</span><span>  }
</span><span>}
</span></code></pre>



Problems:
Once I uploaded the code, the LEDs on each Arduino only lit up around twice when I pressed the button, and then it completely stopped working. I tried reuploading the code on each Arduino, which fixed the problem temporarily, but then it stopped working again. Eventually, it stopped working completely. I am not sure why this happened; Rob said that it could be due to interference from other transmitter in the room, so I will check again before class tomorrow to see if this is the problem.  Also, I had to rewire one of my circuits because my computer would not recognize the port when uploading code so I had to use a different Arduino Uno.

After lab (July 29)- I tried re-uploading the code again after class, but nothing happened.
Before class (July 30)- I re-uploded the code again and it worked! I'm still not really sure why it stopped working last night. I hope it works in class today.
In-class- the code worked at the beginning of class but it stopped working again. I think that the issues most likely is interference from other radio modules.

Applications:
I may use radio module in my final project. If I decide to use a tilt switch to detect when my computer is being turned on and off, I can use a transmitter to send this data to my wristband, which will then beep and vibrate. The code should be somewhat similar because the tilt switch functions the same way as a button. I would only need to turn on a vibrating motor and buzzer instead of a LED. But, unlike this assignment, I would not really need for the wristband to communicate to the computer and it would really only need to be one-way from the computer to the wristband. 





Note:
At first, I wanted to make a different circuit that only communicated one-way so that if a button was pressed on one arduino then a LED would light on the other (instead of doing this both ways). However, this did not work. I am pretty sure that it was probably a problem with the code, but I did not really know how the fix it since I do not have much experience with code. I tried looking at multiple websites that had code to light an LED when a button was pushed, but the code always completed slightly more advanced tasks. The code also varied on all of the different websites, so I did not know how to piece together the code. I tried modifying the original code with what I had found on other websites, but I got really confused, so I decided to make something a little bit different.

The problem could have also been due to interference from other radio modules, but the LED never lit, unlike the circuit that I ended up making, which worked a few times before stopping. 

  Update**:
  
  I managed to fix the code in the circuit that I mentioned in "note". The fix was pretty simple, and I just had to edit the LED variable since the code that I originally used had called it two different things. It now works. I followed this circuit:
  
 Code:
  
 Transmit-
 <pre>
<font color="#5e6d03">#include</font> <font color="#434f54">&lt;</font><b><font color="#d35400">SPI</font></b><font color="#434f54">.</font><font color="#000000">h</font><font color="#434f54">&gt;</font>
<font color="#5e6d03">#include</font> <font color="#434f54">&lt;</font><font color="#000000">nRF24L01</font><font color="#434f54">.</font><font color="#000000">h</font><font color="#434f54">&gt;</font>
<font color="#5e6d03">#include</font> <font color="#434f54">&lt;</font><b><font color="#d35400">RF24</font></b><font color="#434f54">.</font><font color="#000000">h</font><font color="#434f54">&gt;</font>
<b><font color="#d35400">RF24</font></b> <font color="#000000">radio</font><font color="#000000">(</font><font color="#000000">9</font><font color="#434f54">,</font> <font color="#000000">10</font><font color="#000000">)</font><font color="#000000">;</font> <font color="#434f54">&#47;&#47; CE, CSN &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</font>
<font color="#00979c">const</font> <font color="#00979c">byte</font> <font color="#000000">address</font><font color="#000000">[</font><font color="#000000">6</font><font color="#000000">]</font> <font color="#434f54">=</font> <font color="#005c5f">&#34;00001&#34;</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Byte of array representing the address. This is the address where we will send the data. This should be same on the receiving side.</font>
<font color="#00979c">int</font> <font color="#000000">button_pin</font> <font color="#434f54">=</font> <font color="#000000">2</font><font color="#000000">;</font>
<font color="#00979c">boolean</font> <font color="#000000">button_state</font> <font color="#434f54">=</font> <font color="#000000">0</font><font color="#000000">;</font>
<font color="#00979c">void</font> <font color="#5e6d03">setup</font><font color="#000000">(</font><font color="#000000">)</font> <font color="#000000">{</font>
<font color="#d35400">pinMode</font><font color="#000000">(</font><font color="#000000">button_pin</font><font color="#434f54">,</font> <font color="#00979c">INPUT</font><font color="#000000">)</font><font color="#000000">;</font>
<font color="#000000">radio</font><font color="#434f54">.</font><font color="#d35400">begin</font><font color="#000000">(</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Starting the Wireless communication</font>
<font color="#000000">radio</font><font color="#434f54">.</font><font color="#d35400">openWritingPipe</font><font color="#000000">(</font><font color="#000000">address</font> <font color="#000000">)</font><font color="#000000">;</font> <font color="#434f54">&#47;&#47;Setting the address where we will send the data</font>
<font color="#000000">radio</font><font color="#434f54">.</font><font color="#000000">setPALevel</font><font color="#000000">(</font><font color="#000000">RF24_PA_MIN</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;<font color="#434f54">&#47;&#47;You can set it as minimum or maximum depending on the distance between the transmitter and receiver.</font>
<font color="#000000">radio</font><font color="#434f54">.</font><font color="#d35400">stopListening</font><font color="#000000">(</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;This sets the module as transmitter</font>
<font color="#000000">}</font>
<font color="#00979c">void</font> <font color="#5e6d03">loop</font><font color="#000000">(</font><font color="#000000">)</font>
<font color="#000000">{</font>
<font color="#000000">button_state</font> <font color="#434f54">=</font> <font color="#d35400">digitalRead</font><font color="#000000">(</font><font color="#000000">button_pin</font><font color="#000000">)</font><font color="#000000">;</font>
<font color="#5e6d03">if</font><font color="#000000">(</font><font color="#000000">button_state</font> <font color="#434f54">==</font> <font color="#00979c">HIGH</font><font color="#000000">)</font>
<font color="#000000">{</font>
<font color="#00979c">const</font> <font color="#00979c">char</font> <font color="#000000">text</font><font color="#000000">[</font><font color="#000000">]</font> <font color="#434f54">=</font> <font color="#005c5f">&#34;Your Button State is HIGH&#34;</font><font color="#000000">;</font>
<font color="#000000">radio</font><font color="#434f54">.</font><font color="#d35400">write</font><font color="#000000">(</font><font color="#434f54">&amp;</font><font color="#000000">text</font><font color="#434f54">,</font> <font color="#00979c">sizeof</font><font color="#000000">(</font><font color="#000000">text</font><font color="#000000">)</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Sending the message to receiver</font>
<font color="#000000">}</font>
<font color="#5e6d03">else</font>
<font color="#000000">{</font>
<font color="#00979c">const</font> <font color="#00979c">char</font> <font color="#000000">text</font><font color="#000000">[</font><font color="#000000">]</font> <font color="#434f54">=</font> <font color="#005c5f">&#34;Your Button State is LOW&#34;</font><font color="#000000">;</font>
<font color="#000000">radio</font><font color="#434f54">.</font><font color="#d35400">write</font><font color="#000000">(</font><font color="#434f54">&amp;</font><font color="#000000">text</font><font color="#434f54">,</font> <font color="#00979c">sizeof</font><font color="#000000">(</font><font color="#000000">text</font><font color="#000000">)</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Sending the message to receiver </font>
<font color="#000000">}</font>
<font color="#000000">radio</font><font color="#434f54">.</font><font color="#d35400">write</font><font color="#000000">(</font><font color="#434f54">&amp;</font><font color="#000000">button_state</font><font color="#434f54">,</font> <font color="#00979c">sizeof</font><font color="#000000">(</font><font color="#000000">button_state</font><font color="#000000">)</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;<font color="#434f54">&#47;&#47;Sending the message to receiver </font>
<font color="#000000">}</font>

</pre>

 Receive-
 <pre>
<font color="#5e6d03">#include</font> <font color="#434f54">&lt;</font><b><font color="#d35400">SPI</font></b><font color="#434f54">.</font><font color="#000000">h</font><font color="#434f54">&gt;</font>
<font color="#5e6d03">#include</font> <font color="#434f54">&lt;</font><font color="#000000">nRF24L01</font><font color="#434f54">.</font><font color="#000000">h</font><font color="#434f54">&gt;</font>
<font color="#5e6d03">#include</font> <font color="#434f54">&lt;</font><b><font color="#d35400">RF24</font></b><font color="#434f54">.</font><font color="#000000">h</font><font color="#434f54">&gt;</font>
<b><font color="#d35400">RF24</font></b> <font color="#000000">radio</font><font color="#000000">(</font><font color="#000000">9</font><font color="#434f54">,</font> <font color="#000000">10</font><font color="#000000">)</font><font color="#000000">;</font> <font color="#434f54">&#47;&#47; CE, CSN</font>
<font color="#00979c">const</font> <font color="#00979c">byte</font> <font color="#000000">address</font><font color="#000000">[</font><font color="#000000">6</font><font color="#000000">]</font> <font color="#434f54">=</font> <font color="#005c5f">&#34;00001&#34;</font><font color="#000000">;</font>
<font color="#00979c">boolean</font> <font color="#000000">button_state</font> <font color="#434f54">=</font> <font color="#000000">0</font><font color="#000000">;</font>
<font color="#00979c">int</font> <font color="#000000">led_pin</font> <font color="#434f54">=</font> <font color="#000000">3</font><font color="#000000">;</font>
<font color="#00979c">void</font> <font color="#5e6d03">setup</font><font color="#000000">(</font><font color="#000000">)</font> <font color="#000000">{</font>
<font color="#d35400">pinMode</font><font color="#000000">(</font><font color="#000000">led_pin</font><font color="#434f54">,</font> <font color="#00979c">OUTPUT</font><font color="#000000">)</font><font color="#000000">;</font>
<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">begin</font><font color="#000000">(</font><font color="#000000">9600</font><font color="#000000">)</font><font color="#000000">;</font>
<font color="#000000">radio</font><font color="#434f54">.</font><font color="#d35400">begin</font><font color="#000000">(</font><font color="#000000">)</font><font color="#000000">;</font>
<font color="#000000">radio</font><font color="#434f54">.</font><font color="#d35400">openReadingPipe</font><font color="#000000">(</font><font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">address</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;<font color="#434f54">&#47;&#47;Setting the address at which we will receive the data</font>
<font color="#000000">radio</font><font color="#434f54">.</font><font color="#000000">setPALevel</font><font color="#000000">(</font><font color="#000000">RF24_PA_MIN</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;You can set this as minimum or maximum depending on the distance between the transmitter and receiver.</font>
<font color="#000000">radio</font><font color="#434f54">.</font><font color="#d35400">startListening</font><font color="#000000">(</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;This sets the module as receiver</font>
<font color="#000000">}</font>
<font color="#00979c">void</font> <font color="#5e6d03">loop</font><font color="#000000">(</font><font color="#000000">)</font>
<font color="#000000">{</font>
<font color="#5e6d03">if</font> <font color="#000000">(</font><font color="#000000">radio</font><font color="#434f54">.</font><font color="#d35400">available</font><font color="#000000">(</font><font color="#000000">)</font><font color="#000000">)</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Looking for the data.</font>
<font color="#000000">{</font>
<font color="#00979c">char</font> <font color="#000000">text</font><font color="#000000">[</font><font color="#000000">32</font><font color="#000000">]</font> <font color="#434f54">=</font> <font color="#005c5f">&#34;&#34;</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Saving the incoming data</font>
<font color="#000000">radio</font><font color="#434f54">.</font><font color="#d35400">read</font><font color="#000000">(</font><font color="#434f54">&amp;</font><font color="#000000">text</font><font color="#434f54">,</font> <font color="#00979c">sizeof</font><font color="#000000">(</font><font color="#000000">text</font><font color="#000000">)</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Reading the data</font>
<font color="#000000">radio</font><font color="#434f54">.</font><font color="#d35400">read</font><font color="#000000">(</font><font color="#434f54">&amp;</font><font color="#000000">button_state</font><font color="#434f54">,</font> <font color="#00979c">sizeof</font><font color="#000000">(</font><font color="#000000">button_state</font><font color="#000000">)</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Reading the data</font>
<font color="#5e6d03">if</font><font color="#000000">(</font><font color="#000000">button_state</font> <font color="#434f54">==</font> <font color="#00979c">HIGH</font><font color="#000000">)</font>
<font color="#000000">{</font>
<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">led_pin</font><font color="#434f54">,</font> <font color="#00979c">HIGH</font><font color="#000000">)</font><font color="#000000">;</font>
<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">println</font><font color="#000000">(</font><font color="#000000">text</font><font color="#000000">)</font><font color="#000000">;</font>
<font color="#000000">}</font>
<font color="#5e6d03">else</font>
<font color="#000000">{</font>
<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">led_pin</font><font color="#434f54">,</font> <font color="#00979c">LOW</font><font color="#000000">)</font><font color="#000000">;</font>
<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">println</font><font color="#000000">(</font><font color="#000000">text</font><font color="#000000">)</font><font color="#000000">;</font><font color="#000000">}</font>
<font color="#000000">}</font>
<font color="#000000">}</font> 



</pre>


 Video-
<video width="400" controls="">
		<source src="IMG_2380.TRIM.mp4" type="video/mp4">
	</video>
