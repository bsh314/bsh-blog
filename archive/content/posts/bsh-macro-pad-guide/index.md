+++
title = "[Guide] MacroPad ⌨️"
description = "MacroPad build guide [work in progress]"
date = "2020-01-26"
tags = [ "3D", "printing", "DIY", "macro", "pad", "electronics", "mechanical", "cherry", "switch", "arduino", "HID", "RGB" ]
categories = [ "electronics", "keyboard", "MacroPad", "guide" ]
type = "post"
+++

![macro-pad header image](/posts/bsh-macro-pad/header.png)

# Introduction
This project is preaty simple and gives a good introduction into electronics desing and Arduino ecosystem, dont worry about BOM, we will go step by step. I am not affiliated in any way with given Aliexpress suppliers, providen links are just for reference.

# BOM
- 3D printer
- 1x TCA9548A CJMCU-9548 module ([Aliexpress](https://es.aliexpress.com/item/32806052132.html))
- 2x AS5600 magnetic encoders ([Aliexpress](https://es.aliexpress.com/item/4000551682522.html))
- 2x 608RS bearings ([Aliexpress](https://es.aliexpress.com/item/4000029831520.html))
- 2x 15x8mm steel shaft ([Aliexpress](https://www.aliexpress.com/item/4000186787300.html))
- 4x 8mm lock collar ([Aliexpress](https://www.aliexpress.com/item/4000054409294.html))
- 24x cherry style switches ([Aliexpress](https://es.aliexpress.com/item/4001111706889.html))
- 24x BAT85 diodes ([Aliexpress](https://es.aliexpress.com/item/32855239485.html))
- 1x Arduino Pro Micro ATmega32U4 5v ([Aliexpress](https://www.aliexpress.com/item/32768308647.html))
- 3x 55mm WS2812B 144/m LED strip ([Aliexpress](https://www.aliexpress.com/item/2036819167.html))
- 11x M3 8mm hex bolts ([Aliexpress](https://es.aliexpress.com/item/32810872544.html))
- 11x M3 threaded inserts ([Recommended model](https://es.aliexpress.com/item/4000232858343.html))
- 250g of ABS/PLA is enoth, but having two different plastic colors would be a nice aestethics boost!
- Soldering iron, small wires and a good beer 🍺.
- [optional] 2x 80x60mm perforated prototyping pcb board
- [optional] JST connector assortment

# Step 1
**1.1** Print all of the STL files and ensure that bearings can fit firmly in bearing holders, if not, adjust extrusion multiplier to match dimensionsional accuracy of 0.2mm.

![placeholder-image](/posts/bsh-macro-pad-guide/gallery/placeholder.png)

**1.2** Melt in the M3 threaded inserts in their designated spaces.

![placeholder-image](/posts/bsh-macro-pad-guide/gallery/placeholder.png)

# Step 2
**2.1** Cut 3 RGB LED strip 55mm sections.

![placeholder-image](/posts/bsh-macro-pad-guide/gallery/placeholder.png)

**2.2** Place them in the designated holders of 'mount-plate' facing upwards and solder the power and signal lines forming a countinous line like it is described on the image, leaving enoth cable to make the connection to the arduino microcontroller afterwards.

![placeholder-image](/posts/bsh-macro-pad-guide/gallery/placeholder.png)

# Step 3
**3.1** Put all of the mechanical switches on their place on 'mount-plate' in the same orientation.

![placeholder-image](/posts/bsh-macro-pad-guide/gallery/placeholder.png)

**3.2** Prepare diodes to be soldered by bending them like it is describen on the image. Do it for all of the 24 that we need.

![placeholder-image](/posts/bsh-macro-pad-guide/gallery/placeholder.png)

**3.3** Turn around the 'mount-plate' and solder all of them in the arrangement described on the image. This with allow us to form our key rows.

![placeholder-image](/posts/bsh-macro-pad-guide/gallery/placeholder.png)

**3.4** Prepare 4x 200mm wires by stripping them each 20mm from the end, use a wire stripper or do it manually. Make 8x 200mm wires more for the top row connections.

![placeholder-image](/posts/bsh-macro-pad-guide/gallery/placeholder.png)

**3.5** Solder wires in vertical order starting with top top-left corner and non-stripped cables.

![placeholder-image](/posts/bsh-macro-pad-guide/gallery/placeholder.png)

# Step 4
**4.1** Prepare 2x AS5600 magnetic encoders wiring by soldering 200mm cables to pins VCC, GND, DIR, SCL, SDA. Brige GP0 to GND with small portion of wire. Try to use wires with different color to identify each type of connection.

![placeholder-image](/posts/bsh-macro-pad-guide/gallery/placeholder.png)

**4.2** Put both of the sensors on the 'base-bottom' designated place. Use your soldering iron tip to melt plastic pins and this way attach sensors to case permanently. Leave cable harness accessible.

![placeholder-image](/posts/bsh-macro-pad-guide/gallery/placeholder.png)

# Step 5
**5.1** Prepare rotary encoder knobs by cutting 2x XXmm from 8mm rod and securing both lock collars on the bearing.

![placeholder-image](/posts/bsh-macro-pad-guide/gallery/placeholder.png)

**5.2** Add diametrically magnetized neodimium magnet on the inner portion of the rod.

![placeholder-image](/posts/bsh-macro-pad-guide/gallery/placeholder.png)

**5.3** Place 3D printed knob on the 8mm outer portion and secure it with the 8mm M3 screw.

![placeholder-image](/posts/bsh-macro-pad-guide/gallery/placeholder.png)

# Step 6
**6.1** Solder rows and colums cables by guidance of the next diagram.

![placeholder-image](/posts/bsh-macro-pad-guide/gallery/placeholder.png)

**6.2** Solder rotary encoders cables to TCA9548A by guidance of the next diagram.

![placeholder-image](/posts/bsh-macro-pad-guide/gallery/placeholder.png)

**6.3** Connect TCA9548A to the Arduino Pro Micro.

![placeholder-image](/posts/bsh-macro-pad-guide/gallery/placeholder.png)

# Step 7
Place arduino inside of the 'base-bottom' designed place and secure it with a screw. Afterwards close the enclosure and secure it with 8 more screws from the bottom.
 
![placeholder-image](/posts/bsh-macro-pad-guide/gallery/placeholder.png)

# Step 8

**8.1** Flash "Custom Firmware"

![placeholder-image](/posts/bsh-macro-pad-guide/gallery/placeholder.png)

**8.2** Flash QMK firmware

![placeholder-image](/posts/bsh-macro-pad-guide/gallery/placeholder.png)

