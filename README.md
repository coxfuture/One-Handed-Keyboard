# **One-Handed Keyboard**

> We received an unusual email. The writer's daughter had been run over by a heavy truck on her way to school and permanently lost the use of her right hand. Using a computer meant moving her hand back and forth between the keyboard and the mouse all the time, so typing was slow and exhausting. He asked us to build a one-handed keyboard for his daughter.

*This README is translated from the original Chinese. Part numbers, product names and code identifiers are kept as in the original.*

![Left-hand small keyboard, right side](/Docs/Image/左手小键盘右侧面.jpg "Left-hand small keyboard")

![Left-hand large keyboard, right side](/Docs/Image/左手大键盘右侧.jpg "Left-hand large keyboard")

This is a wired-only (single-mode) mechanical keyboard with an integrated trackball. The firmware is built on [QMK](https://github.com/qmk/qmk_firmware) — our thanks to everyone who contributes to the QMK community.

Reference for how this keyboard was made: [He Tongxue: "We made a very unusual keyboard…"](https://www.bilibili.com/video/BV1DtjAzUEb9)

Open-source hardware: [HTXStudio One-Handed Keyboard](https://oshwhub.com/htx-studio/One-Handed_Keyboard) on OSHWHub (LCSC/JLC open-source hardware platform)

[GitHub repository](https://github.com/htx-studio/One-Handed-Keyboard)

[Gitee repository](https://gitee.com/htxstudio/one-handed-keyboard)

For the development environment and how to set it up, see [here](https://docs.qmk.fm/newbs_getting_started "Setting up your QMK environment"). The firmware source is [here](https://github.com/htx-studio/qmk_firmware/tree/master/keyboards/htx_studio).

This repository contains:

* Eight PCBs covering all three keyboard models for the left and right hand, with the LCEDA (JLCEDA) project included.
* VIA keymap configuration files, plus precompiled firmware.
* Mechanical model design files.

---

## Repository layout

#### Docs (documentation)

Chip datasheets and images.

#### Firmware

QMK firmware for the three keyboard models, and the JSON files used for remapping in VIA.

#### Hardware

The JLCEDA project file.

#### Model

The model files and fabrication files used by each keyboard model.

---

## Build guide

### PCBs

The boards are numbered below; note that item 1 covers three different main keyboard PCBs (right-hand large, left-hand small, left-hand large), which together with items 2–6 makes eight boards in total.

1 – Right-hand keyboard, hot-swap (large): FR-4, 1.6 mm thick, 4 layers, stackup JLC04161H-3313, controlled impedance with a ±20% tolerance.

1 – Left-hand keyboard, soldered (small): FR-4, 1.6 mm thick, 2 layers. The ALPS yellow switches need a bit of firm pressure to seat fully when inserted.

1 – Left-hand keyboard, hot-swap (large): FR-4, 1.6 mm thick, 4 layers, stackup JLC04161H-3313, controlled impedance with a ±20% tolerance.

2 – USB Type-C board: FR-4, 1.6 mm thick, 2 layers, marked CON1 (large keyboards only).

3 – Trackball board: FR-4, 1.6 mm thick, 2 layers. Pay attention to the module's orientation when soldering. Marked CON3.

4 – Mouse scroll-wheel board: FR-4, 1.6 mm thick, 2 layers. A 7 mm-tall rotary encoder and 6 mm-tall switches are recommended; switch actuation force ≤ 180 gf. Marked CON2.

5 – Arrow-key board: FR-4, 1.6 mm thick, 2 layers. The ALPS yellow switches need a bit of firm pressure to seat fully when inserted. Marked CON4.

6 – Main controller board, left hand (small): FR-4, 1.6 mm thick, 2 layers.

> * Items `3-Trackball`, `4-Mouse scroll-wheel` and `5-Arrow-key` are small boards shared by all three keyboard variants.
> * `5-Arrow-key` and `1-Left-hand keyboard, soldered (small)` use ALPS yellow switches.
> * Note that the left-hand and right-hand large keyboards are not exact mirror images of each other.
> * The trackball is driven over the SPI1 peripheral, and the scroll wheel gets two dedicated signal lines. That lets you substitute a different input device without much rework.
> * The main controller is an STM32G431CBU6.
> * Works with both A-to-C and C-to-C cables.

### 3D-printed parts

Keycaps: resin, PLA, etc.

Trackball seat: resin, PLA, etc.

Left/right mouse buttons: resin, PLA, etc.

Top case: resin, PLA, etc.

Base: resin, PLA, etc.

### Cut/fabricated parts

Switch plate: POM recommended, 1.5 mm thick.

Plate gasket strips: adhesive on one side only.

Gasket sandwich foam: Poron recommended, 3.5 mm thick.

Switch-seat foam: 2 mm thick.

Case-bottom foam: Poron recommended, 4 mm thick.

Silicone pad (small keyboard only): 5 mm thick, Shore 00-10 hardness.

### Fasteners

|                    | Qty, large keyboard (pcs) | Qty, small keyboard (pcs) |
| :----------------- | :--------------: | :--------------: |
| M3×3×4 heat-set brass insert |        8        |        8        |
| M2×2×3 heat-set brass insert |        2        |        -        |
| M2×3×3 heat-set brass insert |        17        |        12        |
| M3×6 countersunk screw      |        2        |        6        |
| M3×15 countersunk screw     |        -        |        4        |
| M3×22 countersunk screw     |        6        |        -        |
| M2×8 socket-head cap screw      |        4        |        4        |
| M2×3 socket-head cap screw      |        2        |        -        |
| M2×5 socket-head cap screw      |        13        |        8        |
| M3×16 flat-head screw     |        -        |        2        |

### Other parts

Trackball: 25 mm diameter, PTFE.

Glide balls: 2 mm diameter, PTFE, 6 pcs, fitted into the printed trackball seat.

Scroll wheel: 19–20 mm diameter and 4–5 mm thick recommended, metal.

Stabilizers: 2U steel plate-mount stabilizers.

Switches: 57 ultra-small ALPS yellow switches for the small keyboard; 57 standard mechanical switches for the large keyboard.

Ribbon cables (FPC): 0.5 mm pitch, 8-position, reversed type — two 10 cm and two 15 cm.

> * The FPC connectors on the main board and on the small boards all carry a CON label; connect matching labels to each other.
> * The design uses FPC connectors that can be terminated from either the top or the bottom side. Note that if every connector is terminated on the bottom side, reversed (flipped) ribbon cables must be used.

### Model structure

![Left-hand small keyboard, exploded view](/Docs/Image/左手小键盘爆炸图.jpg "Left-hand small keyboard, exploded view")

![Left-hand large keyboard, exploded view](/Docs/Image/左手大键盘爆炸图.jpg "Left-hand large keyboard, exploded view")

### Assembly order

> The large keyboard is used as the example.

**Preparation before assembly**

* First connect the four small PCBs to the keyboard's main PCB with the ribbon cables, and flash the firmware.
* Fit three to five switches, plus the scroll wheel and the trackball. Make sure everything works before you start assembling.
* Install the correct heat-set brass inserts into the matching positions in the printed top case and base.
* Print the legends on the keycaps.
* Stick the gasket strips onto the raised sections of the switch plate (both the top and the bottom side).

> The first time you flash the firmware, hold down the button marked "B" on the back of the PCB, then plug in the USB cable to flash.
>
> To update the firmware afterwards, hold down "ESC" on the keyboard, then plug in the USB cable to flash.
>
> For more detail see [Flashing Your Keyboard (QMK)](https://docs.qmk.fm/newbs_flashing)

**Now start assembling**

1. Screw the four small boards onto the matching positions in the base (mind the ribbon cable routing and the orientation). The screws for the trackball seat are fitted from underneath.
2. Screw the left and right mouse buttons onto the keyboard PCB.
3. Into the fan-shaped area of the base, place the stack in this order from bottom to top: case-bottom foam, switch-seat foam, keyboard PCB, gasket sandwich foam, switch plate.
4. Insert the switches.
5. Put the top case in place and fasten it from underneath with the screws.
6. Fit the keycaps. Assembly is complete.

> For the screw and insert installation guide, see [here](https://github.com/htx-studio/One-Handed-Keyboard/tree/main/Model)

This is our first open-source project. It surely has shortcomings, and we welcome your criticism and corrections. Thank you.

---

## References

[Quantum Mechanical Keyboard Firmware](https://docs.qmk.fm/)

mrjohnk. ADNS-9800. [GitHub repository](https://github.com/mrjohnk/ADNS-9800/)
