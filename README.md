
# The Black Hellebore

### The Black Hellebore, RK61 PCB (Redesign)

What to do with the most popular keyboard on amazon? Reverse engineer it obviously! QMK powered PCB for the RK61. Uses actual STM32 not a cloned Sonix IC.

**The PCB design in this repository is not intended for commercial sales**


## Understanding USB 2.0 Power Spec.

[In general, the specifications for a USB 1.0 and 2.0 standard downstream port, delivers up to 500 mA or 0.5A.](https://resources.pcb.cadence.com/blog/2020-what-are-the-maximum-power-output-and-data-transfer-rates-for-the-usb-standards) With this statement it becomes clear, the max power available to any system using a **type A** connector is 500mA. If the host implements brick-wall current limiting, and the device attached attempts to draw more than 2.5Watts, the current limiter will start dissipating heat. This dissipated heat can lead to thermal shutdown and or possible damage to the host system.

Building on this further, it makes since why most USB type A ports provide more than 500mA. Its to prevent the host current limiting circuit from going into thermal shutdown.

*because I don't have mechanisms in place on the device to handle power negotiation, I'm not assuming the host port can supply more than 2.5Watts of power*

*I would also like to briefly point out that the STM32L412 only has USB Full speed 2.0. It seems kinda silly to use a USB 3.0 connector, when both power and data are USB gen 2.0, admittedly it is nice not worrying about the cable orientation.*

## Part Notes

* CC1 & CC2 Resistors should be 1% not 5%.
* SK6803MINI-E is recommended over SK6812MINI-E.

## Project State

* My Digikey order has arrived.
* Waiting on PCB's (ETA Jan 20th) - Arrived 1-8-2023
* Finished final hand assembly (1-21-2023)
* Tested and confirmed working with QMK and VIA.
* Figured out all of the things (duration, too long...)
* Board Revision Pending.... 
* Board Rev Finished (1-28-2023, sent to fab)
* Waiting on PCB's (ETA 2-10-2023) - Arrived 2-6-2023
* Started finial hand assembly (2-11-2023) (see project log below) 
* Board Revision Pending.... 


# Project Log

### Epic Fail
I began soldering the MCU and current switch IC and everything was going smooth. After I soldered the first row of LED's, I applied power and nothing happened. It was at this point I began to suspect my clever feedback network, sure enough I was getting zero volts on the output. 

Without a second thought, I depopulated the retry network and tested the circuit again. Same result, no RGB. I started measuring the RGB PWM of the MCU with my scope, I was getting no PWM output, I thought "Great! I zapped my STM32". I removed power from the circuit, then started poking around with my meter, come to find out, every RGB LED was shorted to ground.

I removed all of the RGB LED's and checked the first row of pads, no shorts. I replaced the LED, and there's a short!! I tried 5 different LED's before I noticed it..... JLCPCB milled into the ground pore copper!!!! see **001.bmp & 002.bmp**. When the LED is soldered, a short occurs between the pin and the ground plane.  

I'm going to add a keep out area around the RGB LED's to prevent my future revision from suffering the same fate as 1.2.0. .....that's another punch to the wallet, I'm not making that mistake again....

---




![Alt text](/src/PCB.png)

![Alt text](/src/ProjectPics/img003.jpeg)
 
# View All Project Files Online
 
https://www.altium.com/viewer/

---
 
MIT licensed keyboard.

[!["Buy Me A Coffee"](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://www.buymeacoffee.com/mccardlema3)
