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
  <p>
During the lab, I also worked on my final project. I did not want to disassemble my prototype, so I made a new circuit. This time, I incorporated a transistor. I plan on using this in my wristband  to turn the motor on and off. Previously, in my prototype, I used a physical button so that the motor+buzzer would turn on while I held the button down. This will not work in my final design, so I had to use a different method of controlling my circuit. 

I spent a lot of time on the motor. The wires connected to the motor are very weak and kept on unattaching from the circuit. I tried using tape, but that did not secure it either. Then, I decided to solder the wire. After a while, this broke as well. I re-soldered the motor with a different strategy. First, I strengthened the wires on the motor itself with the tin wire. Then, I added this onto a seperate wire and joined them with additional tin wire (Image 4). This worked very well, and I do not think that it will break again. 
Something else that I found difficult with the motor is the delicacy of the wires. It was really hard to strip the wires without cutting it off since they are incredibly thin. 

![IMG_2491](https://user-images.githubusercontent.com/52216217/62304681-7a119e80-b44c-11e9-8d28-84d0405ef196.jpg)
Image 4

In the first circuit that I made, I tested the transistors code. I made a circuit with a button, a transistor, a buzzer, and a vibration motor. The motor turned on through the transistor, and the button is controlled separately of the transistor, when the button is pressed.

Circuit:

![IMG_2459](https://user-images.githubusercontent.com/52216217/62304684-7bdb6200-b44c-11e9-8fcc-2d0da081b32b.jpg)


Next, to take it further, I incorporated radio modules. I am still working on the code because it has not been working. The light that indicates that my transmitter is not lighting. But, essentially I have a tilt switch, LED, radio module, and button on one circuit, and a button, vibration motor, radio module, and transistor on the other. The former will go on my laptop, and it will turn on when I push the button, even when I release my finger. If the button is on, the LED will light. Then, if the button is turned on, the switch will detect whether my computer is flipped open. If it is, it will tell the other radio module and the buzzer and vibration motor will turn on on the wristband. 

I have written the code for both the transmitter and receiver, although neither are working yet. I am not sure if the problem is with the radio modules, the circuit wiring, or the code. I previously had some difficulty with the radio modules. I will keep working on finding the problem. 

Eventually, I will use Arduino Micros instead of Arduino Unos in my project. I soldered a Arduino Micro during the lab.

![IMG_2451](https://user-images.githubusercontent.com/52216217/62304687-7da52580-b44c-11e9-98c6-268fe7b00e5b.jpg)


Update***
Moments after writing about my problems, I realized that I may have had the LED in the wrong way, which is why it was not lighting. I was right, and I have spent a lot of time examining the code and circuits. The problem was actually a lot simpler than I thought. 

However, now that the LED has turned on it is acting strangely and will not turn off when I press the button. It just keeps blinking. The receiver reacts with the LED. It vibrates and buzzes as the LED blinks, and it vibrates much stronger when the transmitter is tilted (the tilt switch), but nothing turns off when the transmitter is laid flat, which is the goal. Instead, the buzzing+vibrating just gets weaker. </p>
</div>

<div id="Progress" class="tabcontent">
  <h3>Progress</h3>
  <p  
     <iframe src=" https://docs.google.com/document/d/139E958er5j9MPKxyXhbfnbgA3y83sf7eP6fXaIT4rO4/edit?usp=sharing" style="width:600px; height:500px;" frameborder="0"></iframe>  </p>
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
