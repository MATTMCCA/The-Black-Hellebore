
# The Black Hellebore

### The Black Hellebore, RK61 PCB (Clone)

What to do with the most popular keyboard on amazon? Reverse engineer! it obviously! New and more better, QMK powered PCB for the RK61. Uses actual STM32 not a cloned Sonix IC.
 
*I would like to note, that during testing of the Black Hellebore, I observed LED flickering. (see edit 3, below)*

*Edit 2: I'm actually using the 12mA variant, SK6812, not the SK6803 (which would of been better for this application)*

*Edit 3: I'm now 100% sure that using a series limiting resistor to regulate the supply current was a really stupid thing to do. I'm sure Georg Simon Ohm is spinning in his grave. I need to revisit my idea of using a current mirror to remove the need for series resistance. MR. OHM'S!! I'M SORRY!!!! I BELIEVE YOU NOW!*
~~~
V=I*R
As you increase the brightness, you increase the power draw (P=I*V).
Vt = Vr + Vf.
Ir = Vr / 12 or Vr/Ir = 12. 
so if Ir increases, Vr must increase. If (VCC - Vr) < (LED Vfx), the led won't illuminate.

If Ir = 100mA, Vcc = 5V | Vr = 1.2V, Vfx = 3.1V
If Ir = 200mA, Vcc = 5V | Vr = 2.4V, Vfx = 2.6V
If Ir = 300mA, Vcc = 5v | Vr = 3.6V, Vfx = 1.4V

Red Vf: 1.8~2.2V  
Green Vf: 3.0~3.2V  
Blue Vf: 3.2~3.4V 
~~~

*HACK Alert, if your know the host port can safely limit the supply current with out damage, you could replace the aforementioned resistor, with zero ohms.*

* CC1 & CC2 Resistors should be 1% not 5%.
* I really hope I got the switch spacing and PCB size correct!! (spoiler, I didn't, but its been fixed)
* Prototype has split BOM, PCB will come partially assembled.
* SK6803MINI-E recommended over SK6812MINI-E.

### Project State

* My Digikey order has arrived.
* Waiting on PCB's (ETA Jan 20th) - Arrived 1-8-2023
* Finished final hand assembly (1-21-2023)
* Tested and confirmed working with QMK and VIA.
---


![Alt text](/src/PCB.png)

![Alt text](/src/ProjectPics/img003.jpeg)
 
# View All Project Files Online
 
https://www.altium.com/viewer/

---
 
MIT licensed keyboard.

[!["Buy Me A Coffee"](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://www.buymeacoffee.com/mccardlema3)
