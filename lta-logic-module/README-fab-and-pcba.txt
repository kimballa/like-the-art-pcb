Hello,

Thank you for making my PCBA! I'm looking forward to the results. This data package includes gerbers, drill file (TXT), drill map (PDF), pick-and-place file (POS), a complete schematic (PDF), a 3-d render of the fully-assembled system, BOM (Excel), and these notes.

This is a 2-layer, 1.6mm, immersion gold (ENIG)-finished 1oz board, 90x125mm. Standard FR4 board OK. Please use blue solder mask, white silkscreen. Please put any needed house silkscreen marks only on bottom side. All parts are on top side. Standard delivery time okay; please ship via ShenZhenDHL.

Please fab 5 boards, assemble 3. Total 119 THT pads, 269 SMD pads per board.

Here are some notes about fab and PCBA that may be helpful:

* Gerbers were generated with solder mask minimum web width 0.25mm. If you want I can regenerate with 0mm min solder dam width. Gerber format 4.6 X2, mm units. 
* Holes are specified as finished hole size. Test point pads (TP1, TP2...) require 0.3mm (+0.04/-0.03mm) finished through-hole diameter. Please adjust drill file as needed. All holes should be PTH.
* Excellon drill file coordinates are relative to upper-left corner of board rectangle (before adding fillet), mm units.
* POS file is only SMD components; I can regenerate with THT components also if you want.
* I don't know if you use wave, selective or manual solder for THT; I tried to plan for either case.
* A suggested wave-soldering direction for THT assembly (bottom-to-top) is indicated in silkscreen on the back side. Components Q2, C5, and adjacent pins of D2 and U2 should be visually inspected for bridging. D2/U2 bridging may be OK since they are on the same net. A solder thief pad has been added above Q2.
* If wave soldered right-to-left (not preferred), solder thief pads trail behind both rows of U1 and J2--J4 to aid correct assembly.
* Unnecessary solder thief pads may be removed by the PCB engineer if you prefer.
* Component U1 refers to a complete Adafruit Feather M4 Express assembly (as shown in rendering) but I will install this later. Please assemble 1x12 and 1x16 female headers per BOM comments.
* Transistor Q1 is an external module, to be wired in post-assembly. Assemble as 2-pin (2.54mm) male header.
* U2, C5, L1, J1, D1, and D2 are very tall THT parts (see image). There are some low-profile SMD parts near U2 and L1 which I assume are assembled first. Please let me know if this placement is impossible and I will see what I can do to adjust.
* If using house parts, please ensure all specifications in "Comments" column of BOM are met. Some parts are marked "Exact MPN"; please do not substitute those.
* Adjusting MPNs to use more convenient shipping packagings (reel vs tape, etc) is of course okay.
* 3 board fiducials have been added to corners. Please feel free to move or adjust as needed.

Thank you again for your work. If you have any questions please reach out -- akimball83@gmail.com.

Best,
- Aaron Kimball