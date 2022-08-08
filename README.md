
You Don't Have to Like All the Art! -- PCBs
===========================================

PCB designs and eCAD files for the "You Don't Have to Like All the Art!" project.

This system consists of two distinct circuit boards:

* `lta-logic-module` - The "logic" that determines when it's dark out / should be active, what
  messages to light up on the sign, manages PWM or other effects when displaying the sign, and
  also handles button inputs from users. Runs on a combination of 5V and 3V3. This is designed
  around a port for installing an Adafruit Feather M4 Express (ATSAMD51 / Cortex-M4) Arduino
  device. The rest of the circuitry:
  * Provides regulated 5V0 input voltage for the rest of this module
  * Manages a wide fanout of control and sense lines via I2C
  * Uses a phototransistor to sense when it is dark out, and thus the system should be active
    vs in standby mode
  * Combines the sign control lines with a global PWM signal and buffers the output before feeding
    to the power module.
* `lta-power-module` - The high-power circuits that actually drive the LED signs. This module is
  "dumb" and contains no combinational logic or more complex circuitry. Most of the board is used
  for mounting 3rd-party PCB submodules for high-amp 12V0 voltage regulation, distributing a
  power bus, and actually driving power MOSFETs linked to each sign's power wiring. The onboard
  circuitry:
  * Provides regulated 5V0 input voltage for the rest of the onboard circuitry
  * Displays condition of regulated 12V0 input power
  * Uses SN75374 low-side drivers to send control signals to the MOSFET modules
  * Contains a small integrated protoboard for in-field repairs and modifications

The `photodiode-sim` subproject is a simplified version of the `DARK` detection circuitry for use
with `ngspice` to understand the sensitivity of the logic signal to input current levels from the
phototransistor and the variable resistance of the potentiometer used as an in-field sensitivity
calibration input.

A third PCB (`mosfet-chip`) is a mini-PCB to connect two circuits via screw-terminals, switchable by
an onboard `IRLZ24` NMOS FET transistor activated by a separate gate pin. 16 of these are mounted on
the power module by #0 machine screws.

I originally used this
[High-Power Dual MOSFET Switch Module](https://protosupplies.com/product/high-power-dual-mosfet-switch-module/)
but found the screw terminals included were too unreliable. This PCB is footprint-compatible and
uses larger-gauge, higher-quality terminal blocks by Phoenix Contact. The `mosfet-chip/` directory
includes a panelized (2x3) layout suitable for PCBA and the BOM to enable assembly at JLCPCB.

Fabrication
-----------

All models are built with KiCAD 6. Each module contains a BOM spreadsheet for assembly with MPNs to
order from DigiKey or elsewhere as noted. Per-run fabrication gerbers are kept in versioned
subdirectories of each submodule project.

All modules are fabricated with the following parameters:

* 2 layers
* 1.6mm finished board thickness
* FR4-Tg130 core
* Both layers 1 oz copper thickness
* Blue soldermask, white silkscreen (these choices made only for aesthetic reasons and do not
  affect eng or mfg)

The logic module is fabricated with ENIG finish for reflow; the power module can be finished
with RoHS Pb-free HASL.

The logic module was fabricated by Elecrow and follows their design rules. Smallest
traces are 0.20mm. All trace separation >= 0.15mm.

The power module was fabricated by JLCPCB and follows their design rules. Smallest power module
traces and trace separations are 0.25mm / 0.20mm, which more than meets their capabilities.

Assembly
--------

Boards require only single-sided assembly.

The logic module is a mixed SMD/THT board and was assembled by Elecrow. Smallest reflow components
are 0603. Logic module ICs are SOIC (1.27mm pitch). Actual LEDs, resistors, and IC decoupling
capacitors do not follow the BOM strictly but instead use house parts (except as noted `Exact MPN
Only` in the BOM). More notes about logic module assembly are in `README-fab-and-pcba.txt` in
the logic module directory.

The power module is THT-only and intended for hand-soldered assembly. (A single 7343-metric / 2917
/ "size D" tantalum SMD capacitor for the 5V0 regulator can also be hand-soldered.)

The mosfet chips are a mixed SMD/THT assembly and were assembled by JLCPCB. BOM includes SPNs
for JLC's preferred supplier. Individual mini-PCBs are too small for automated SMD assembly,
so gerbers are supplied for a panelized 2x3 PCB layout, made with the Panelizer plugin for KiCAD 6.

