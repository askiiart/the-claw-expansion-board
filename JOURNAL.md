## 2/14/2026 - Looked into lasers and stuff, anadapter board for connectors

*1.5 hours*

I'm aiming to have easy compatibility with lasers, with as little rewiring to switch out tools as possible, so I'm planning to have a board to adapt whatever's on the motherboard to easy wiring - for example, BL-touch to a single 5-pin connector, 2/3-pin laser to VDD + GND with PWM handled via a MOSFET on the board itself (will be 3 pin to support lasers that have PWM, can just use 2 out of 3 pins for standalone lasers), and connector for vacuum pump going to HE3.

Will also have 12/24V jumpers and buck converter for either voltage (for laser and vacuum pump), and will have an io expander connected via i2c for GPIO. Will also add general 12/24V power terminals for whatever.

![image](https://blueprint.hackclub.com/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTA0NTA1LCJwdXIiOiJibG9iX2lkIn19--5e66a9a90a4f92be73b9819c17a518af14801590/image.png)

Also some general resources relating to this cuz why not

- Octopus wiki thing: <https://global.bttwiki.com/Octopus.html>
- 3rd party diagram: <https://gadgetangel.org/build/electrical/images/BIGTREETECH-Octopus-1.1-color-PIN.pdf>
- Git repo (with manual and stuff): <https://github.com/bigtreetech/BIGTREETECH-OCTOPUS-V1.0>

## 2/21/2026 - Figured out pinout of the PCB

*3.5 hours*

So uh after like forever I figured out the pinout of the PCB. JST ZPD is quite niche but will work perfectly, and isn't so niche that it's too difficult to find replacements, hence going with that for GPIO/I2C + power after much deliberation. LCSC's out of stock for female right-angle XT30 connectors, so instead I'm having to go with XT60, hence I'm having to make the GPIO connector much smaller. 26 pin *would* have fit (just barely), and would've allowed for 16 pins + i2c + 3.3/5/12/24V power, but XT60, so instead I'm having to reduce it down. 10 pin would've been fine - no GPIO, just i2c and power - but LCSC doesn't have those so I figured I might as well make it 12 pin and add another 24V pin for 4A total.

(also for context regarding the high pin count, every power pin has a matching GND pin so that's not limiting this, with just 1 it would be a max 2A power draw across everything)

(i also removed 2+2 laser support to clear up room - can rewire that very easily anyways)

![image](https://blueprint.hackclub.com/user-attachments/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTA4OTE4LCJwdXIiOiJibG9iX2lkIn19--1b2940142eef81e77b9e1775e8e0407d9969a0fc/image.png)

## 2026-03-18 - Looked into alternative DC-DC voltage regulators and connectors, added more parts such as MOSFETs

*4 hours*

I looked into alternative DC-DC voltage regulators - TO-220-5 buck converters are available, however that would mean far more supporting circuitry, so it's not worth it imo.

However, I also need solenoid control for pick and place, which requires a larger connector. To do this I redesigned the board to use a [JST ZPD 10 pin connector](https://www.digikey.com/en/products/detail/jst-sales-america-inc/SM10B-ZPDSS-TF/2472584) rather than 12 pin.

As for voltage selection for laser, the easiest way seems to be to use [screw terminals](https://www.lcsc.com/product-detail/C918122.html) and have wires jumping between them. Normal jumpers can't exactly handle 7.5 amps (nor can 0 ohm resistors). However, for the vacuum (and certainly the solenoid), those will be under 2 amp, so those can use jumper wires... though that won't actually be much smaller, so I'll probably just use screw terminals anyways.

Additionally, voltage selection will have to not be an option - level shifting above 5V is difficult, and given 5V will never be above the valid voltage range, it will only be set to output 5V.

Regarding the MOSFETs, given the low frequency (500Hz to 25kHz for laser), it's easy to find [a good MOSFET](https://www.lcsc.com/product-detail/C2902884.html). For the PNP stuff, a P-channel MOSFET controlled by a BJT + pullups would be *ideal* (increase in heat aside), but given wiring the PNP head/vacuum will be much cleaner with 2 separate GNDs, heat has a remote chance of being a concern, and this is much easier, I'm going with just using NMOSes on the vacuum and solenoid.

## 2026-03-19A - Added I/O expander, finished up schematic

*2 hours*

Pretty simple, just added the I/O expander and finished the few bits of the schematic. I'm just using pin headers and jumpers to set the I/O expander address - which is already pretty overkill but who cares :p

I also went through and selected components, nothing too interesting there, sticking with through-hole when possible though for ease of assembly - space isn't much of a concern here.

## 2026-03-19B - Added MOSFET for external bed control

*1.5 hours*

This is as good a place as any to put the bed MOSFET, so why not. Plus it actually need supporting circuitry sooooo it really need a PCB anyways. Regardless, I checked out [this](https://frank26080115.github.io/Bones-3D-Printer/other_pages/externalmosfet.html) blog post on how to use an external bed MOSFET to make sure I'm actually doing it competently. Anyways, just using 

MOSFETs and to some extent voltage dividers and electricity in general confuse me so this took far longer than it should have and my brain nearly combusted. But uh yay done with that.

![image](https://cdn.hackclub.com/019d09a4-1846-77e8-bb6e-f4fe3d3c1ec6/image.png)

## 2026-03-19B - Routed PCB

*3 hours*

Took forever but I routed the PCB. Had to make custom symbols for the NMOSes so they'd work with the footprint properly, but it wasn't too bad. Also wow I love filling areas, very helpful.

Oh also I was using inner layer trace widths so I had to redo that. Much more viable with external layers.

The bed control area (many fills):

![image](https://cdn.hackclub.com/019d09a8-46f9-7db9-b6f8-3d6e334637a3/image.png)

...for how long this took it feels like there should be more to write, but no routing is just kinda boring. okay byeeeeeeeeeeeeeeeee

---

Note: sorry if my journals seem a bit odd, originally they were part of the main printer project on Blueprint before being split off to a separate project. I will be leaving a reviewer note to subtract 5 hours from the journal entries being moved.
