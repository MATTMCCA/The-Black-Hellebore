

# The Black Hellebore

### The Black Hellebore, RK61 PCB (Clone)

What to do with the most popular keyboard on amazon? Reverse engineer! it obviously! New and more better, QMK powered PCB for the RK61. Uses actual STM32 not a cloned Sonix IC.
 
*I would like to note, that during testing of the Black Hellebore, I observed LED flickering. (see edit 3, below)*

---
*Edit 2: I'm actually using the 12mA variant, SK6812, not the SK6803 (which would of been better for this application)*

---
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

---
Edit 4: **Speculation Warning:** Why are my LED's really flickering? In truth, I don't know! but shorting the series resistor seems to fix everything (except my USB hub). Inquiring minds want to know!

 The data sheet states the LED's are fed by a....

*"The output is driven by patented PWM  
technology, which effectively guarantees high consistency of the color of the pixels. The control  
circuit consists of a signal shaping amplification circuit, a built-in constant current circuit, and a high precision RC oscillator."*

No simplified logic diagram is given, so I'm going to assume it operates similarly to a "LTC3212". This means the LED's are not directly connected to VCC, but rather a charge pump and current regulator.

So the above still holds true? More power dissipated = lower supply voltage = chip led's no more worky? 

Rather than append more broken thoughts to this jumbled mess of ideas, I'm just gonna buy up some FMB2907A's and see what happens. The end goal is to limit the the supply current without negatively effecting the chip LED's, via, the not so popular current mirror. The datasheet says 600mA, 700mW, 60V, the voltage drop on the PNP is going to be like < 500mW@350mA for (1/1.41v) (unless some how I drop more voltage over the CE? Then I run the risk of dissipating a destructive amount of heat, I better by more than 2... YAY Science!).

[Literally what I'm gonna do (see figure 3.b).](https://www.allaboutcircuits.com/textbook/semiconductors/chpt-4/current-mirrors/)

---
*HACK Alert, if you know the host port can safely limit the supply current **with out damage**, you could replace the aforementioned resistor, with zero ohms.*

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
