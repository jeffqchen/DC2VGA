# DC2VGA

<img src="./Pics/01.jpg" width="400px" />

A SD/VGA-switchable RGBs/RGBHV Dongle for Sega Dreamcast.

This belongs to my [series of VGA adapters](https://github.com/jeffqchen/Console-VGA-Dongle-Series) for various retro consoles and video equipments.

<img src="./Pics/02.jpg" width="400px" />

This adapter plugs into the AV OUT port on a Sega Dreamcast and allows you to out put RGBS or RGBHV video signal, as well as a stereo audio signal.

------------

### Toggling Modes


There are two independent toggle switches on this dongle for choosing different modes.

<img src="./Pics/03.jpg" width="400px" />

- SD / VGA allows you to choose between 525i and 525p RGB output
- CSYNC / HV allows you to choose between attenuated CSync and 3.3V H/V-Sync

I have tested this dongle with various devices:

|              | SD+CSync | VGA+CSync | SD+HV  | VGA+HV    |
|--------------|----------|-----------|--------|-----------|
| RetroTINK 5X | **Yes**  | **Yes**   | No     | No        |
| OSSC         | **Yes**  | **Yes**   | **Yes**| **Yes**   |
| GBS Control  | **Yes**  | **Yes**   | No     | No        |
| PVM/BVM      | **Yes**  | No        | No     | No        |
| PC Monitors  | No       | No        | No     | **Yes**   |

The only compatibility issue I've encountered so far, is **VGA** mode + **CSync** on Sony BVM D series. This BVM doesn't like combined CSync and will not display it properly. **However it will work properly in SD mode.**

#### *VGA Trick*

<img src="./Pics/trick.jpg" width="400px" />
(Bust-A-Move 4 tricked to run in VGA mode)

Some games that require an SD cable can be forced into VGA mode by toggling the top switch from SD to VGA, right after booting up the game (at the VMU beep or right after game started from the ODE).

### Audio

Audio can be carried inside the VGA cable as-is, or extracted from the 3.5mm jack on the dongle.

* *Buzzing may be noticeable when audio is transmitted within the VGA cable in certain scenes in certain games. This is due to insufficient shielding in most VGA cables. If you find the buzzing to be annoying, use the 3.5mm jack on the dongle for audio output. This will ensure the cleanest possible audio.*

### Other Use Cases

Light guns work if you output to a CRT display (TV and PC monitor).

 -----------

 ## Parts

PCB (You need both)
- Vertical PCB: https://oshpark.com/shared_projects/WcKgCnij
- Horizontal PCB: https://oshpark.com/shared_projects/jPAbQ0ej

[1x] Dreamcast AV Plugs
- https://www.aliexpress.com/item/33016034152.html

[2x] Toggle Switches (SW1 & SW2):
- EG2208: https://www.digikey.com/en/products/detail/e-switch/EG2208/301963

*If you want slightly longer switch stems, use **EG2208A** instead.*

[1x] VGA Port Slim Female
- https://www.aliexpress.com/item/4000596805684.html

[1x] 3.5mm Headphone Jack PJ-325
- https://www.aliexpress.com/item/1005002983859846.html

[1x] M2x20mm screw and hex nut
- https://www.amazon.com/dp/B074FWP9HB

2.54mm-Pitched Right Angle Pin Header (at least 11-pin wide)
- Example: https://www.amazon.com/dp/B01461DQ6S/


### SMD Components:

*All SMD resistors and capacitors are in imperial 0603 size unless specified otherwise*

#### On Vertical Board
- 4-Channel XOR Logic Gate, 14TSSOP (MC74HC86ADTR2G)
 - Example: https://www.digikey.com/en/products/detail/MC74HC86ADTR2G/MC74HC86ADTR2GOSCT-ND/3487361
- **C1 C2 C3**: [3x] 220uF / 6.3V / **Imperial 1206 Size**
- **C4**: 0.1uF / 10V
- **C5 C6**: 1uF / 10V
- **R1 R2**: 150 Ohm
- **R3 R4**: 10K Ohm

**R5 and R6** can have different configurations. Choose one from the following:
- For 0.6V Vpp CSync: (common attenuation CSync level)
   - R5 25 Ohm
   - R6 680 Ohm


- For 0.3V Vpp CSync: (SCART-safe sync level)
   - R5 75 Ohm
   - R6 1K Ohm

#### On Horizontal Board
- C1 C2: 10uF / 6.3V

-----------

## 3D Printing

Print all parts in their original orientations.

The shells are printed on the 3.5mm port side to give it a flat surface on that side and better details on the top.

Try using tree support as it's easier to extract and leaves less damage to up-facing surfaces below supported surfaces.

Make sure all support material is removed before trying to fit the electronics inside, as there is zero space to spare inside.

-----------

## Preparations

### Dreamcast Video Plug

<img src="./Pics/plugprep_01.jpg" width="200px" />
<img src="./Pics/plugprep_02.jpg" width="200px" />

The original Dreamcast video plug has a cross bar to prevent the pins from falling out. You need to extract it with a sider cutter or dental pick like shown in the picture.

*IF* a pin falls out during the process, simply carefully push it back into its original place.

<img src="./Pics/plugprep_03.jpg" width="200px" />
<img src="./Pics/plugprep_04.jpg" width="200px" />

Then, put the printed "Plug Helper" piece over the pins and put it into the plug until it's flush.

This piece helps to maintain a leveled surface so the plug can be soldered to the PCB reliably.

### PCB

<img src="./Pics/Asm_01.jpg" width="400px" />

Trim extra tabs sticking outside from the PCB outline with a side-cutter and file. Otherwise you may run into issues trying to fit the assembly into the 3D printed shell.

-----------

## Assembly

<img src="./Pics/Asm_02.jpg" width="400px" />

Populate the horizontal and vertical PCBs with all the SMD components first.

Solder in the Dreamcast video plug and the switches onto the vertical board.

<img src="./Pics/Asm_03.jpg" width="400px" />

Cut a section of the pin header with 11 pins. Fit the bent end onto the horizontal PCB from the bottom side, as close as possible. Then solder in the two ends first.

You can adjust the pin header by melting the two ends. Make sure the straight part of the pin header is parallel to the PCB as much as possible.

Now start trimming out the extra length of the bent end. Make it as flush as possible to the PCB. Do the middle pins first, then solder the flush pins to the PCB.

<img src="./Pics/Asm_04.jpg" width="400px" />

Lastly, suck up any excessive solder from the two end pins, and then trim them flush as well.

<img src="./Pics/Asm_05.jpg" width="300px" /><img src="./Pics/Asm_06.jpg" width="300px" />

Using a cutter, cut and remove the black plastic piece that holds all the pins together. Try cutting in with a light angle so the cuts reach the pins for an easy removal.

Now solder in the VGA and 3.5mm port tightly onto the horizontal PCB.

Trim the 3 pins that would be blocked by the toggle switch, so you can temporarily fit the entire assembly into the top shell.

<img src="./Pics/Asm_07.jpg" width="400px" />

Position the PCBs so the 3.5mm port and VGA port fits into the cutouts on the top shell snugly, and the vertical PCB is as vertical as possible. Then, solder the 3 trimmed pins and the one on the other end, to fix the assembly.

<img src="./Pics/Asm_08.jpg" width="400px" />

Go on and trim all the rest of the excessive straight pins and solder them in place. Feed an ample amount of solder and heat up the pin long enough so the solder could seep into the vias on the vertical PCB.

<img src="./Pics/Asm_09.jpg" width="400px" />

Inspect the other side and make sure the vias are filled by solder. If not, heat it up again with a bit more solder. The internal assembly is now finished.

<img src="./Pics/Asm_10.jpg" width="400px" />

Now, fit the completed internal into the bottom shell, then put the top shell over it and close it up.

<img src="./Pics/03.jpg" width="400px" />

Secure the shells with a set of M2x20mm screw and nut.

------------
## Some Technical Nuances

This Dongle uses the native CSync signal generated by the Dreamcast itself - when it's set to SD mode. This mode has the best compatibility with SD TVs and monitors.

When set to VGA mode **AND** CSync, the circuit inside uses an XOR logic chip to combine the native HSync and VSync signals into an artificial CSync signal. This signal has a slight discrepancy from a standard CSync signal, and some equipments that rely on PLL (phase lock loop) would be thrown off (as documented in the [HDRetrovision Blog](https://www.hdretrovision.com/blog/2019/10/10/engineering-csync-part-2-falling-short)).

This issue was anticipated and since in most cases, you would not run into any issue, I opted to not dig deeper and further complicate the design.

-----------
## Special Thanks
Mike Chi
- Twitter: https://twitter.com/retrotink2
- Official Website: https://www.retrotink.com/

HDRetrovision
- Twitter: https://twitter.com/hdretrovision
- Official Website: https://www.hdretrovision.com/

Javier Rodas
- Twitter: https://twitter.com/JaviRodasG
