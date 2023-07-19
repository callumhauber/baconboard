# Baconboard Build Guide - Amoeba Variant

## Parts List
Here is everything you'll need to build your very own baconboard.

### Keyboard Files
Download the [baconboard files](https://anchovie.art/baconboard-build-kit.zip). This zip folder contains the case and firmware files.

### Keycaps
- 69x 1U  
- 9x 1.75U
- 1x 2U
- 1x vertical 2U (for numpad, only different if using non-uniform profile keycaps)
- 1x 2.25U
- 1x 2.75U
Uniform profile keycaps (e.g. DSA) are recommended, as the baconboard layout is highly nonstandard.

### Switches
- 82x switches  
The Amoeba PCBs support MX or Alps style switches, but we highly recommended MX for the Amoeba Variant due to stabilizer compatibility.

### Stabilizers
- 4x 2U PCB-mount stabilizers

### Electronics
- 79x 1U [Amoeba PCBs](https://keeb.io/products/amoeba-single-switch-pcbs)
- 3x 2U [Amoeba PCBs](https://keeb.io/products/amoeba-single-switch-pcbs)
- 100x [1N4148 Diodes](https://keeb.io/products/1n4148-diodes)  
Remember to choose SMD (0805) for the Amoeba Variant, as it is **not** compatible with thru-hole diodes! You don't actually need 100 of these, but it's good to have extras. **A heat gun and soldering paste are highly recommended** for soldering these onto the Amoeba PCBs.
- 1x [Stampy RP2040 Microcontroller](https://keeb.io/collections/diy-parts/products/stampy-rp2040-usb-c-controller-board-for-handwiring)  
You may elect to use a different microcontroller, but this guide and our firmware is written for the Stampy. Proceed at your own risk, and remember to modify the case files and firmware as needed for your chosen controller. The controller needs to support 5 rows and 18 columns, for a total of 23 GPIO (unless you want to change the wiring as well to combine multiple rows/columns).

### Hardware
- 22 or 24 GA solid-core wire [Amazon example](https://www.amazon.com/dp/B07JNB712X)
- [Chip Quik NC191LTA10 low temp solder paste](https://www.amazon.com/gp/product/B096BMCXHX/) or equivalent
- 12x M3x10 standoffs [Amazon example](https://www.amazon.com/dp/B07Y1JD8DC)
- 12x M3x10 machine screws [Amazon example](https://www.amazon.com/uxcell-Alloy-Socket-Button-Screws/dp/B019ZC3MD0/)
- 12x M3x6 machine screws [Amazon example](https://www.amazon.com/uxcell-M3x6mm-Thread-Button-Socket/dp/B01B1OD0IC/)
- 24x M3 washers (recommended) [Amazon example](https://www.amazon.com/M3x6mmx0-5mm-Stainless-Steel-Washer-100Pcs/dp/B015A39NCC/)
- 4x [SKUF rubber feet](https://keeb.io/products/skuf-silicone-rubber-keyboard-feet)

## Making the Case
If you'd like to manufacture your own baconboard case, you'll need access to the following tools:
- Laser cutter (450 x 150mm minimum bed size)
- 3D printer (76 x 76 mm minimum bed size)

If you don't own these tools, see if there is a makerspace near you. Most will have 3D printers and/or laser cutters for use by members. Alternatively, services such as [sendcutsend](https://sendcutsend.com/) will manufacture the plates for you in exchange for currency. Here's a [big list of vendors](https://www.keebtalk.com/t/list-of-laser-cutting-services/2500).

Note: if you are opting to use a microcontroller other than the Stampy, you will need to modify the case files so that you can mount the controller to it directly.

### Plate Materials and Dimensions
**Switch Plate**
- Width: 1.5mm
- Material: metal  
Note: Acrylic will suffice in a pinch, but will be fragile and prone to deck flex - we highly recommend aluminum or steel.

**Top Plate**
- Width: 7mm maximum
- Material: acrylic, wood, or metal  
Note: You can stack multiple thinner top plates to reach this height, or keep it thinner for a skeletonized look. If you opt for a thinner top plate, you'll need to substitute the M3x10 screws for smaller ones so they fit into the standoffs.

**Bottom Plate**
- Width: 1.5mm minimum
- Material: acrylic, wood, or metal  
Note: for more flexible materials e.g. acrylic, wood, we recommend a thicker bottom plate to avoid deck flex. If you opt for a thicker bottom plate, you may need to substitute the M3X6 screws for longer ones so the fit into the standoffs.

### Baconboard Feet
You can 3D print the baconboard feet with any plastic you choose. We recommend PLA or PETG.

## Assembly
Once your case parts are finished, you're ready to start soldering and assembling your baconboard!

### Solder Diodes
If you purchased Amoeba PCBs from [keeb.io](https://keeb.io/products/amoeba-single-switch-pcbs), they should come in grids of 30. You probably purchased 3x grids. This is very convenient for soldering the diodes in batches.

Take your solder paste and apply a small amount onto each diode pad of the Amoeba PCBs.

Take the 1N4148 diodes (we recommend using tweezers) and place them across the pads. Ensure the orientation of each diodes matches [this diagram](/images/amoeba.jpg).

Set the heat gun to ~350 C and solder each diode.

### Assemble Switch Plate
Place your switches in the switch plate. Orient them so that the pins face the backside of the keyboard, like so:

![image](/images/switch-orientation.jpg)

### Solder Stampy Microcontroller
Flip the switch plate upside-down. Place the Stampy onto the three most upper-right switches with the USB-C side up. Solder these switches to the microcontroller.

### Solder Switches
Now it's time to break apart your Amoeba PCB grids. Separate them such that they remain attached in rows, as the spacing between each PCB across a row matches the row spacing of switches. Then break off singletons as needed.

![image](/images/amoeba-rows.jpg)

Place the Amoeba PCBs on top of each switch. The bottom-right switch a.k.a. the Numpad Enter will use a 1U Amoeba PCB even though it's a 2U key. This is because a 2U Amoeba switch will not fit properly when oriented at such an angle.

Using a soldering iron and wire, solder each Amoeba PCB onto each switch.

### Solder Matrix
Here you'll be creating the rows and columns of the keyboard. On the Amoeba PCBs, row wires are soldered to the pads labeled "SR". Column wires are soldered to the pads labeled "SC". You only need to solder one column pad on the top of each Amoeba PCB, and one on the bottom. There are two column pads on each side to aid with routing the column wires. You do **not** need to solder matrix wires to the three switches that are already soldered directly to the Stampy microcontroller. Follow the wiring diagram below.

![image](/images/matrix-wiring.jpg)

### Solder Microcontroller Wires
Here you'll wire the ends of each row and column into the Stampy controller. It is important to connect each row and column to the appropriately-labelled GPIO pin on the controller, as the firmware is based on this. **Tip: solder C0, C1, and C2 first. Then solder all of the rows. Then solder the remaining columns.** This is the easiest order of operations. Follow the wiring diagram below.

![image](/images/controller-wiring.jpg)

### Flash Firmware
The time has finally come! Your baconboard is ready for programming. To flash the baconboard, all you will need is the `baconboard_default.uf2` file included in the keyboard files you downloaded earlier.

1. Plug your baconboard into your computer.
2. Hold down the reset button on the Stampy controller for ~10 seconds, until you hear the device disconnect and reconnect with your computer. It should appear as a USB disk containing no files.
3. Copy `baconboard_default.uf2` onto the USB disk.
4. The device should disconnect, and then reconnect as an input device.

If you ever need to re-flash your baconboard's firmware, simply reset the Stampy controller and repeat this process.

### Test Switches
Now that your baconboard has been flashed, you should test every switch to ensure it's functioning correctly. We recommend using a keyboard switch testing software such as EK Switch Hitter. Online alternatives exist but provide less functionality. Note: the layer keys (FN1, FN2, FN3) will not register on their own. You can test each layer by holding down a layer key and pressing another mapped key on that layer, e.g. FN1 + 1 should illuminate F1 on Switch Hitter.

[archive.org direct link](https://web.archive.org/web/20190428204254/https://elitekeyboards.com/suppdata/doc/EK_Switch_Hitter_Installer_v1.0.msi)

[mirror link](https://ek-switch-hitter.software.informer.com/download/)

### Case Assembly
Once your baconboard is fully tested, it's time for the pièce de résistance: final assembly.
1. Place the top plate(s) on top of the switch plate, aligning the screw holes.
2. Fasten the M3x10 standoffs to the underside of the switch plate with the M3x10 screws, sandwiching the top plate(s) and switch plate between them.

![image](/images/baconboard-standoff-view.jpg)

3. Flip the baconboard over.
4. Align the bottom plate with the standoffs.
5. Stick the SKUF keyboard feet into the oval indents of the 3D printed keyboard feet.
6. Align the keyboard feet with the middle and upper standoffs. See image below for reference.

![image](/images/baconboard-bottom-view.jpg)

7. Use the M3x6 screws to fasten the keyboard feet and bottom plate to the M3x10 standoffs.
8. Add keycaps.

...And that's it! Congratulations on completing your very own baconboard. We hope you have a tantalizingly tasty time typing :D