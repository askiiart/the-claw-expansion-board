# The Claw Expansion Board

An expansion board to support further modding for my printer I'm desinging for Blueprint. The goals of this are:

- Power output rails on 24V, 12V, and 5V
- Power + I2C expansion port
- Laser (power/GND/PWM) port
- PNP (vacuum PWR/GND ; solenoid PWR/GND) port
- MOSFET to turn bed on/off, rather than depending on messy external one(?)
  - Need to try to figure out bed pinout

## Parts

- [LDO regulators](https://www.lcsc.com/product-detail/C41428569.html)
- [io expander](https://www.lcsc.com/product-detail/C561268.html)
- [4p screw terminals](https://www.lcsc.com/product-detail/C918122.html)
- [3p screw terminals](https://www.lcsc.com/product-detail/C918121.html)
- [N-channel MOSFETs](https://www.lcsc.com/product-detail/C2902884.html)
- [P-channel MOSFETs](https://www.lcsc.com/product-detail/C50386320.html)
- [3x3 pin headers](https://www.lcsc.com/product-detail/C7429377.html)
- Connectors
  - XT30 (power)
    - [headers](https://www.lcsc.com/product-detail/C2913282.html)
  - XT60 (bed)
    - [headers](https://www.lcsc.com/product-detail/C428722.html)
  - Laser:
    - [JST XH 3 pin headers](https://www.lcsc.com/product-detail/C157928.html)
  - PNP
    - [JST XH 4 pin headers](https://www.lcsc.com/product-detail/C163037.html)
  - I/O connector
    - [ZPD header](https://www.lcsc.com/product-detail/C265342.html)
      - optional:
        - [housing](https://www.lcsc.com/product-detail/C566943.html)
        - [crimps](https://www.lcsc.com/product-detail/C20539070.html)
- misc components:
  - capacitors
    - [68uF bulk](https://www.lcsc.com/product-detail/C106558.html)
    - [0.1uF](https://www.lcsc.com/product-detail/C5632430.html)
  - resistors (highly accurate for setting LDOs)
    - [10k](https://www.lcsc.com/product-detail/C2903232.html)
    - [8.2k](https://www.lcsc.com/product-detail/C2848599.html)
    - [3.3k](https://www.lcsc.com/product-detail/C2903352.html)
    - [1k](https://www.lcsc.com/product-detail/C2903245.html)
    - [470](https://www.lcsc.com/product-detail/C119317.html)
  - [diodes](https://www.lcsc.com/product-detail/C84410.html)
  - [jumpers](https://www.lcsc.com/product-detail/C2998928.html)
