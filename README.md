


# The Black Hellebore

### The Black Hellebore, RK61 PCB (Clone)

What to do with the most popular keyboard on amazon? Reverse engineer! it obviously! New! <del>and more better,</del> QMK powered PCB for the RK61. Uses actual STM32 not a cloned Sonix IC.
 
*I would like to note, that during testing of the Black Hellebore, I observed LED flickering. (see edit 3.b, below)*

---
*Edit 2: I'm actually using the 12mA variant, SK6812, not the SK6803 (which would of been better for this application)*

---
*Edit 3.b: I'm now 100% sure that using a series limiting resistor to the LED supply was a really stupid thing to do.*

After much research, I don't think I can limit the supply current to a set level without generating heat. At best, limiting the supply current with a current mirror, results in a 50% power loss. I would need to dissipate 250mA, to mirror 250mA (It=500mA).

* Using a fuse seems to be valid, 0ZCG0020AF2C, and it fits the footprint ($0.12 @ 100)
* Using a FPF2223 (settable load switch with auto retry) is another option ($0.95 @ 100)
* Using a NUD4001 (High current automotive Led driver) ($0.72 @ 100) (*not sure this will even work*)

**Note on PTC's** Once the PTC trips, PTC's are "damaged", tripping multiple times will "damage" the device further, a cool down period is also involved after trip.

**I'm in favor of the FPF2223, I get a settable trip limit, it trips quick, it auto retries, won't generate heat, won't degrade over time.** 

---

* CC1 & CC2 Resistors should be 1% not 5%.
* SK6803MINI-E recommended over SK6812MINI-E.

### Project State

* My Digikey order has arrived.
* Waiting on PCB's (ETA Jan 20th) - Arrived 1-8-2023
* Finished final hand assembly (1-21-2023)
* Tested and confirmed working with QMK and VIA.
* Figured out all of the things (duration, too long...)
* Board Revision Pending....
---


![Alt text](/src/PCB.png)

![Alt text](/src/ProjectPics/img003.jpeg)
 
# View All Project Files Online
 
https://www.altium.com/viewer/

---
 
MIT licensed keyboard.

[!["Buy Me A Coffee"](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://www.buymeacoffee.com/mccardlema3)
