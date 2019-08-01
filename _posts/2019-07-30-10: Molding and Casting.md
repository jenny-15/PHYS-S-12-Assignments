
---
layout: post
title:  "10: Molding & Casting"
permalink: /10/
---

### Header 3

10: Molding and Casting

Today I worked on a mold and my final project. 




**Molding:**


I decided to make a mold of a Harvard magnet-
![IMG_2434](https://user-images.githubusercontent.com/52216217/62301925-74658a00-b447-11e9-8979-fe13ff883756.jpg)

The first step was to make a one-part mold and suspend it in a cup. For the mold, you need two holes: one to pour the plaster in and one for air bubbles to escape. These two holes can be made in the mold by attaching two sticks of clay onto the original positive object. I did this as pictures below, and I also stuck a needle through a popsicle stick to suspend the magnet: ![IMG_2435](https://user-images.githubusercontent.com/52216217/62301927-7596b700-b447-11e9-9b14-26b3f8e2e456.jpg)


Then, I poured a mix of silicone inside. This mix was made with a 1:1 ratio of oomoo A and oomoo B (Image 1). After this dried for around 2 hours, I cut the negative mold in half with an exacto knife-
![IMG_2445](https://user-images.githubusercontent.com/52216217/62302076-b68ecb80-b447-11e9-9c4f-aa78238d11b7.jpg)
![IMG_2447](https://user-images.githubusercontent.com/52216217/62302079-b989bc00-b447-11e9-9f85-58b43e7384dc.jpg)

![IMG_2439](https://user-images.githubusercontent.com/52216217/62302013-9a8b2a00-b447-11e9-8033-49dbe5d80e96.jpg)
Oomoo


Then, I placed the mold back in a cup and began casting. To create the plaster, I mixed gypsum cement (Image 2) with water. At first, my mixture was way too thin because I added too much water. I learned from Nathan that the texture should be like a milkshake, but it should be between what you would something with a spoon and what you would drink with a straw. 

![IMG_2450](https://user-images.githubusercontent.com/52216217/62302175-e76f0080-b447-11e9-97b6-d49fefe34d40.jpg)
Image 2



Problem:
My cast kept on breaking when I took it out of the mold (Image 3). I think that the first time, the texture was probablys till a little too thin. I decided to try again, but this time I waited a few hours to make sure that it completely dried and hardened. This time, the cast did not break and turned out pretty well! It did not break when I took it out, but it broke when I was filing it down. I used joined the broken piece with glue

![IMG_2455](https://user-images.githubusercontent.com/52216217/62302188-eb9b1e00-b447-11e9-8791-5bb985a85892.jpg)
Image 3

Final result before filling:
![IMG_2470](https://user-images.githubusercontent.com/52216217/62302312-1eddad00-b448-11e9-8063-0942c8112bdb.jpg)

Final result:
![IMG_2501](https://user-images.githubusercontent.com/52216217/62309240-1475e000-b455-11e9-82db-d83ed1fae4ca.jpg)





**Final project:**
During the lab, I also worked on my final project. I did not want to disassemble my prototype, so I made a new circuit. This time, I incorporated a transistor. I plan on using this in my wristband  to turn the motor on and off. Previously, in my prototype, I used a physical button so that the motor+buzzer would turn on while I held the button down. This will not work in my final design, so I had to use a different method of controlling my circuit. 

I spent a lot of time on the motor. The wires connected to the motor are very weak and kept on unattaching from the circuit. I tried using tape, but that did not secure it either. Then, I decided to solder the wire. After a while, this broke as well. I re-soldered the motor with a different strategy. First, I strengthened the wires on the motor itself with the tin wire. Then, I added this onto a seperate wire and joined them with additional tin wire (Image 4). This worked very well, and I do not think that it will break again. 
Something else that I found difficult with the motor is the delicacy of the wires. It was really hard to strip the wires without cutting it off since they are incredibly thin. 
![IMG_2491](https://user-images.githubusercontent.com/52216217/62304681-7a119e80-b44c-11e9-8d28-84d0405ef196.jpg)
Image 4

In the first circuit that I made, I tested the transistors code. I made a circuit with a button, a transistor, a buzzer, and a vibration motor. The motor turned on through the transistor, and the button is controlled separately of the transistor, when the button is pressed.
Circuit:
![IMG_2459](https://user-images.githubusercontent.com/52216217/62304684-7bdb6200-b44c-11e9-8fcc-2d0da081b32b.jpg)

Video:


Next, to take it further, I incorporated radio modules. I am still working on the code because it has not been working. The light that indicates that my transmitter is not lighting. But, essentially I have a tilt switch, LED, radio module, and button on one circuit, and a button, vibration motor, radio module, and transistor on the other. The former will go on my laptop, and it will turn on when I push the button, even when I release my finger. If the button is on, the LED will light. Then, if the button is turned on, the switch will detect whether my computer is flipped open. If it is, it will tell the other radio module and the buzzer and vibration motor will turn on on the wristband. 

I have written the code for both the transmitter and receiver, although neither are working yet. I am not sure if the problem is with the radio modules, the circuit wiring, or the code. I previously had some difficulty with the radio modules. I will keep working on finding the problem. 

Eventually, I will use Arduino Micros instead of Arduino Unos in my project. I soldered a Arduino Micro during the lab.
![IMG_2451](https://user-images.githubusercontent.com/52216217/62304687-7da52580-b44c-11e9-98c6-268fe7b00e5b.jpg)


Update***
Moments after writing about my problems, I realized that I may have had the LED in the wrong way, which is why it was not lighting. I was right, and I have spent a lot of time examining the code and circuits. The problem was actually a lot simpler than I thought. 

However, now that the LED has turned on it is acting strangely and will not turn off when I press the button. It just keeps blinking. The receiver reacts with the LED. It vibrates and buzzes as the LED blinks, and it vibrates much stronger when the transmitter is tilted (the tilt switch), but nothing turns off when the transmitter is laid flat, which is the goal. Instead, the buzzing+vibrating just gets weaker.
