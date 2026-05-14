# The Claw Expansion Board

## NOTE: OH GOD I JUST REALIZED I USED LDOs PLEASE PLEASE PLEASE SWITCH THOSE OUT FOR BUCK CONVERTERS IF YOU DO THIS YOURSELF I HAVE UP TO 232.5 WATTS OF HEAT FOR NO REASON

An expansion board to support further modding for my printer I'm desinging for Blueprint. The goals of this are:

- Power output rails on 24V, 12V, and 5V
- Power + I2C expansion port
- Laser (power/GND/PWM) port
- PNP (vacuum PWR/GND ; solenoid PWR/GND) port
- MOSFET to turn bed on/off, rather than depending on messy external setup
- Able to handle the maximum current (25A, 7.5A for buck converters) anywhere

![A 3D model of the PCB](/readme-assets/image.png)

## Parts

|Item                                |Price |Quantity|Link                                                                                 |Total Cost|Notes                                                          |
|------------------------------------|------|--------|-------------------------------------------------------------------------------------|----------|---------------------------------------------------------------|
|COS29752WU (LDO regulator)          |$2.10 |2       |https://www.lcsc.com/product-detail/C41428569.html                                   |$4.20     |                                                               |
|XD8574AP (I/O expander)             |$0.57 |1       |https://www.lcsc.com/product-detail/C561268.html                                     |$0.57     |                                                               |
|DB125-2.54-4P-GN-S (4P screw term)  |$0.40 |2       |https://www.lcsc.com/product-detail/C918122.html                                     |$0.80     |                                                               |
|DB125-2.54-3P-GN-S (3P screw term)  |$0.33 |1       |https://www.lcsc.com/product-detail/C918121.html                                     |$1.67     |                                                               |
|MS50N06 (50A NMOS)                  |$0.11 |4       |https://www.lcsc.com/product-detail/C2902884.html                                    |$0.57     |                                                               |
|AO3400A (5.8A NMOS)                 |$0.03 |1       |https://www.lcsc.com/product-detail/C347475.html                                     |$0.65     |                                                               |
|BSS84 (PMOS)                        |$0.01 |1       |https://www.lcsc.com/product-detail/C50386320.html                                   |$0.55     |                                                               |
|PZ254-3-03-Z-2.5-G0 (3x3 pins)      |$0.21 |1       |https://www.lcsc.com/product-detail/C7429377.html                                    |$1.03     |                                                               |
|XT30PW-F20.G.Y (XT30 headers)       |$0.33 |3       |https://www.lcsc.com/product-detail/C2913282.html                                    |$1.00     |                                                               |
|XT60PW-F (XT60 female headers)      |$0.55 |1       |https://www.lcsc.com/product-detail/C428722.html                                     |$0.55     |                                                               |
|XT60PW-M (XT60 male header)         |$0.52 |1       |https://www.lcsc.com/product-detail/C98732.html                                      |$0.52     |                                                               |
|S3B-XH-A(LF)(SN) (XH 3P R/A)        |$0.09 |1       |https://www.lcsc.com/product-detail/C157928.html                                     |$0.92     |                                                               |
|S4B-XH-A-1(LF)(SN) (XH 4P R/A)      |$0.15 |2       |https://www.lcsc.com/product-detail/C157925.html                                     |$0.77     |                                                               |
|SM12B-ZPDSS-TF(LF)(SN) (ZPD 12P R/A)|$0.80 |1       |https://www.lcsc.com/product-detail/C265342.html                                     |$0.80     |                                                               |
|ZPDR-12V-S (ZPD 12P housing)        |$0.34 |1       |https://www.lcsc.com/product-detail/C566944.html                                     |$1.68     |                                                               |
|HC-ZHD-T-05 (ZPD crimps)            |$0.02 |12      |https://www.lcsc.com/product-detail/C20539070.html                                   |$0.96     |                                                               |
|JST XHP-3 (XH 3P housing)           |$0.02 |2       |https://www.lcsc.com/product-detail/C144402.html                                     |$0.46     |                                                               |
|JST XHP-4 (XH 4P housing)           |$0.02 |2       |https://www.lcsc.com/product-detail/C144403.html                                     |$0.45     |                                                               |
|ZX-XH2.54-DZ (XH crimps)            |$0.01 |14      |https://www.lcsc.com/product-detail/C7462731.html                                    |$0.42     |                                                               |
|B3B-XH-A(LF)(SN) (XH 3P vertical)   |$0.05 |1       |https://www.lcsc.com/product-detail/C144394.html                                     |$0.54     |                                                               |
|ERJ1EM680E09OT (68uF caps)          |$0.03 |4       |https://www.lcsc.com/product-detail/C106558.html                                     |$0.67     |MUST be aluminum electrolytic caps, do NOT replace with ceramic|
|178MU0006 (0.1uF caps)              |$0.01 |2       |https://www.lcsc.com/product-detail/C5632430.html                                    |$0.69     |                                                               |
|MF1/4W-10K±1%-ST52 (10k resistor)   |$0.01 |7       |https://www.lcsc.com/product-detail/C2903232.html                                    |$0.59     |All resistors are highly accurate due to setting LDO regulators|
|MF1/4W-8K2±1%-ST52 (8.2k resistor)  |$0.00 |1       |https://www.lcsc.com/product-detail/C2848599.html                                    |$0.49     |                                                               |
|MF1/8W-3K3±1%-ST52 (3.3k resistor)  |$0.01 |1       |https://www.lcsc.com/product-detail/C2903352.html                                    |$0.50     |                                                               |
|MF1/4W-1K±1%-ST52 (1k resistor)     |$0.01 |1       |https://www.lcsc.com/product-detail/C2903245.html                                    |$0.56     |                                                               |
|MF1/4W-470Ω±1% T (470 resistor)     |$0.01 |1       |https://www.lcsc.com/product-detail/C119317.html                                     |$0.58     |                                                               |
|1N4148TR (diode)                    |$0.02 |1       |https://www.lcsc.com/product-detail/C84410.html                                      |$0.80     |                                                               |
|2.54mm jumpers                      |$0.01 |4       |https://www.lcsc.com/product-detail/C2998928.html                                    |$0.44     |                                                               |
|TMP100NA/3K (temp sensor)           |$0.46 |1       |https://www.lcsc.com/product-detail/C31810.html                                      |$0.46     |                                                               |
|9733 24V fan                        |$6.39 |1       |https://www.aliexpress.us/item/3256804645826698.html                                 |$6.39     |                                                               |
|Wire crimping tool                  |$15.99|1       |https://www.amazon.com/Crimping-Amliber-Connectors-Electrical-Terminals/dp/B0D1FR76Q7|$15.99    |                                                               |
|                                    |      |        |                                                                                     |          |                                                               |
|Subtotal                            |      |        |                                                                                     |$47.28    |                                                               |
|                                    |      |        |                                                                                     |          |                                                               |
|JLCPCB                              |      |        |                                                                                     |$7.30     |                                                               |
|LCSC shipping                       |      |        |                                                                                     |$14.56    |                                                               |
|                                    |      |        |                                                                                     |          |                                                               |
|Total                               |      |        |                                                                                     |$74.84    |                                                               |

## Notes

- **The case will be made by hand out of wood**, not 3D printed, due to potential for high temperatures. As such there is obviously no CAD model.
- **XT60 polarity is reversed!!!** I don't have the time (or energy) to redo the entire board right now, but I may redo it later.
  - XT30 has been fixed, that does not apply here
  - BOM may change slightly, as when I fix that I will make the 24V input male. Cost should be slightly lower.
- Some 3D models don't exist, and so those components aren't in the render.
