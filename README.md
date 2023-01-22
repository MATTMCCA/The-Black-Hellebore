# The Black Hellebore

### The Black Hellebore, RK61 PCB (Clone)

What to do with the most popular keyboard on amazon? Reverse engineer! it obviously! New and more better, QMK powered PCB for the RK61. Uses actual STM32 not a cloned Sonix IC.
 
*I would like to note, that during testing of the Black Hellebore, I observed LED flickering, I suspect this is due to insufficient supply voltage. Since the LED supply is limited with a current limiting resistor, cranking the brightness with all LED's on will cause the SK6803MINI-E's to intermittently brown out. (This is my current working theory, pun not intended, but still funny)*

*HACK Alert, if your know the host port can safely limit the supply current with out damage, you could replace the aforementioned resistor, with zero ohms.*

* CC1 & CC2 Resistors should be 1% not 5%.
* I really hope I got the switch spacing and PCB size correct!! (spoiler, I didn't, but its been fixed)
* Prototype has split BOM, PCB will come partially assembled.

### Project State

* My Digikey order has arrived.
* Waiting on PCB's (ETA Jan 20th) - Arrived 1-8-2023
* Finished final hand assembly (1-21-2023)

---


![Alt text](/src/PCB.png)

![Alt text](/src/ProjectPics/img003.jpeg)
 
# View All Project Files Online
 
https://www.altium.com/viewer/

---
 
MIT licensed keyboard.

[!["Buy Me A Coffee"](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://www.buymeacoffee.com/mccardlema3)
