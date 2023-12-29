# ModbusRTU Test Shield
![ModbusRTU Test Shield Top View](extras/ModbusRTU-Test-Shield-Top-View.png)

A shield for Arduino boards that provides an RS-485 transceiver, RS-232 transceiver, and a selection of buttons, lights, and knobs.
This board was designed to aid in testing the [ModbusRTUSlave](https://github.com/CMB27/ModbusRTUSlave) and [ModbusRTUMaster](https://github.com/CMB27/ModbusRTUMaster) libraries.

- This shield is designed to work with both 5V and 3.3V Arduino boards.
- A 3-position removable screw terminal is used as the RS-485 interface.
- A RJ12 connector is used as the RS-232 inteface. The pinout of this connector is designed to make it compatible with Automation Direct products.
- The potentiomter knobs can be easily removed so you can stack other shields on top of this one.
- There is a switch to easily change between using a `HardwareSerial` port or a `SoftwareSerial` port.
- The selected serial port is connected to both the RS-485 and RS-232 transceivers, so not confugration changes are needed to switch between them.

> [!NOTE]
> This design is distributed WITHOUT ANY EXPRESS OR IMPLIED WARRANTY, INCLUDING OF MERCHANTABILITY, SATISFACTORY QUALITY AND FITNESS FOR A PARTICULAR PURPOSE.
> 
> This board is designed to use only one serial interface (RS-485 or RS-232) at a time.
> Attempting to use both at the same time is unlikely to damage the board, but could lead to unexpected behavior.


### Pinouts
#### Arduino Pin Usage
| Pin | Function              | pinMode                                           |
|-----|-----------------------|---------------------------------------------------|
| 0   | HardwareSerial RX     | INPUT (Set by HardwareSerial)                     |
| 1   | HardwareSerial TX     | OUTPUT (Set by HardwareSerial)                    |
| 2   | Button1 (BTN1)        | INPUT_PULLUP                                      |
| 3   | Button2 (BTN2)        | INPUT_PULLUP                                      |
| 5   | LED1 (L1)             | OUTPUT                                            |
| 6   | LED1 (L2)             | OUTPUT                                            |
| 7   | LED1 (L3)             | OUTPUT                                            |
| 8   | LED1 (L4)             | OUTPUT                                            |
| 10  | SoftwareSerial RX     | INPUT (Set by SoftwareSerial)                     |
| 11  | SoftwareSerial TX     | OUTPUT (Set by SoftwareSerial)                    |
| 13  | Driver Enable (DE)    | OUTPUT (set by ModbusRTUSlave or ModbusRTUMaster) |
| A0  | Potentiometer1 (POT1) | INPUT                                             |
| A1  | Potentiometer2 (POT2) | INPUT                                             |

_Unused Pins: 4, 9, 12, A2, A3, A4, A5_

#### RS-485 Interface
| Pin | Function  | Electrical Type |
|-----|-----------|-----------------|
| 1   | RS-485 D+ | Bidirectional   |
| 2   | RS-485 D- | Bidirectional   |
| 3   | GND       | Passive         |

#### RS-232 Interface
| Pin | Function  | Electrical Type |
|-----|-----------|-----------------|
| 1   | GND       | Passive         |
| 2   | 5V        | Power Output    |
| 3   | RS-232 RX | Input           |
| 4   | RS-232 TX | Output          |
| 5   | VBUS      | Power Input     |
| 6   | GND       | Passive         |


### Documentation
- [Schematic](ModbusRTU-Test-Shield.pdf)
- [KiCAD Source Files](src)
- [STEP 3D Model](extras/ModbusRTU-Test-Shield.step)



## Components

### Circuit Board
#### Specifications
- Board Length: __68.58mm__
- Board Width: __53.34mm__
- Board Thickness: __1.6mm__
- Substrate Material: __FR4__
- Copper Layers: __2__
- Copper Thickness: __1oz__
- Soldermask Color: __Any__ (Blue Suggested)
- Smallest Hole Diameter: __0.6mm__
- Smallest Trace Width: __0.2mm__ (7.8mil)
- Smallest Trace Spacing: __0.2mm__ (7.8mil)

#### Suppliers
Below are some circuit board manufacturers I have used in the past.
Generally you will need to upload the upload the [gerber and drill files](gerbers) to their websites in a .zip folder.

- [OSH Park](https://oshpark.com) is a US based circuit board fabrication service.
  They tend to be more expensive than other manufacturers and the number of options they give you are limited (If you use this manufacturer, I hope you like purple).

- [Seeed Studio Fusion](https://www.seeedstudio.com/fusion_pcb.html) makes circuit boards in China.
  They have a lot of options when ordering; please refer to the [specifications](#specifications) above when making your choices.
  They do have a circuit board assembly service as well, but I am not especially familiar with it.


### Purchase Components
#### Bill of Materials

| Reference    | Qty | Manufacturer           | Part Number           | Description                         | Notes                                                                                         |
|--------------|----:|------------------------|-----------------------|-------------------------------------|-----------------------------------------------------------------------------------------------|
| C1-C6        |   6 | KEMET                  | ESS105M050AB2EA       | 1uF Aluminum Electrolytic Capacitor |                                                                                               |
| D1-D4, D6-D8 |   7 | Würth Elektronik       | 151031YS06000         | Yellow LED                          | These are used for various indicators.                                                        |
| D5           |   1 | Würth Elektronik       | 151031VS04000         | Green LED                           | This is used to indicate that 5V is present.                                                  |
| D9, D10      |   2 | Vishay                 | BAT43-TAP             | Schottky Diode                      | These diodes are used to `AND` and level convert the `RX` signals from the transceivers.      |
| D11          |   1 | Vishay                 | SB260S-E3/54          | Schottky Diode                      | This diode allows the Arduino board to be powered through the RS-232 interface.               |
| J1-J4        |   1 | SparkFun Electronics   | PRT-11417	            | Stacking Socket Header Kit          | This kit contains multiple parts.                                                             |
| J5           |   1 | Phoenix Contact        | 5434557               | 3-Position Terminal Block Plug      | This screw terminal works with a special pin header and is not soldered to the circuit board. |
| J6           |   1 | Amphenol ICC (FCI)     | 54601-906WPLF         | RJ12 Jack                           |                                                                                               |
| R1-R8        |   8 | Stackpole Electronics  | CFM14JT330R           | 330 Ohm Resistor                    | These are generic 330 Ohm resistors; smilarly sized components of the same value should work. |
| R9           |   1 | Stackpole Electronics  | CFM14JT10K0           | 10K Ohm Resistor                    | This is a generic 10K Ohm resistor; a smilarly sized component of the same value should work. |
| RV1, RV2     |   2 | Piher/Amphenol         | PT10MV10-103A2020-E-S | 10K Ohm Potentiometer               |                                                                                               |
| RV1, RV2     |   2 | Piher/Amphenol         | JPEPL6052INI          | Potentiometer Knob                  |                                                                                               |
| SW1-SW3      |   3 | TE Connectivity        | 1825910-6             | 6mm Pushbutton Switch               | This is a generic 6mm pushbutton switch. Feel free to substitute.                             |
| SW4          |   1 | C&K                    | OS202011MS2QN1        | DPDT Slide Switch                   |                                                                                               |
| U1           |   1 | Analog Devices         | LT1785ACN8#PBF        | RS-485 Half-Duplex Transceiver      | This part is used with a socket; DO NOT solder this part to the circuit board.                |
| U2           |   1 | Texas Instruments      | MAX232N               | RS-232 Transceiver                  | This part is used with a socket; DO NOT solder this part to the circuit board.                |
| XJ5          |   1 | Phoenix Contact        | 5430438               | 3-Position Terminal Block Header    | This is the socket for the RS-485 screw terminal and is soldered to the circuit board.        |
| XU1          |   1 | Assmann WSW Components | AR 08-HZL/01-TT       | 8-Position DIP Socket               | This is the socket for the RS-485 transceiver and is soldered to the circuit board.           |
| XU2          |   1 | Assmann WSW Components | AR 16-HZL/01-TT       | 16-Position DIP Socket              | This is the socket for the RS-232 transceiver and is soldered to the circuit board.           |


#### Suppliers
Below are some electronics suppliers I have used in the past:

- [Digi-Key](https://www.digikey.com/) is my usual go-to supplier for electronic components.
  Their website makes it pretty easy to sort through parts.

- [Mouser](https://www.mouser.com/) is very similar to Digi-Key in a lot of ways.
  They sometimes have better pricing, and they have excellent customer support.

- [Newark](https://www.newark.com/) tends to have a bit different selection than Digi-Key and Mouser, especially in the area of connectors.

- [Octopart](https://octopart.com/) is not a supplier per se; it is essenitally an electronic component search engine.
  This can be a very helpful tool when looking for parts, especially somewhat unusual ones, like extended socket headers.

All of these suppliers have a feature on their respective websites where you can upload a spreadsheet file, such as [ModbusRTU-Test-Shield-BOM.csv](ModbusRTU-Test-Shield-BOM.csv), to populate the cart or find parts.


## Assembly
### Tools and Supplies
If you are assembling the ModbusRTU Test Shield yourself, you will need the following tools and supplies:

| Item              | Optional | Notes                                                                                                                                              |
|-------------------|----------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| Soldering Iron    | No       | Make sure you use a good quality soldering iron. A poor quality soldering iron will give you a miserable soldering experience.                     |
| Flush Cutters     | No       | These are used to trim component leads.                                                                                                            |
| Flux Core Solder  | No       | Leaded solder is easier to work with, but lead-free solder is better for the environment.                                                          |
| Solder Flux       | Yes      | Extra flux will make the solder flow better. I don't usually use it when through-hole soldering, but it can be helpful.                            |
| Solder Wick       | Yes      | This is used to remove solder from places you don't want it.                                                                                       |
| Solder Sucker     | Yes      | If you need to de-solder a component, this, along with solder wick, is the tool you want. This can quickly remove most of the solder from a joint. |
| Arduino Shield    | Yes      | This can be used to hold the stacking socket headers in place while being assembled.                                                               |
| Isopropyl Alcohol | Maybe    | This is used to remove flux. It is not needed if you are using no-clean flux.                                                                      |
| Dish Soap         | Maybe    | This is used to remove flux residue. It is not needed if you are using no-clean flux.                                                              |

> **Note on Flux**  
> Traditional flux if left on the assembled circuit board could cause some serious issues.
> It can potentially cause shorts or significant [parasitic capacitance](https://en.wikipedia.org/wiki/Parasitic_capacitance).
> It is also somewhat corrosive and can, over time, damage your circuit board.
> This sort of flux must be cleaned off the board after assembly.
> 
> To address these issues there are no-clean fluxes, that can be left on the circuit board assembly and are unlikly to cause these issues.
> There are also water-soluble fluxes that can be cleaned off with hot water, though I have found that some isopropyl alcohol can speed up the process.
> There are also fluxes that are both no-clean and water soluble; this is what I like to use.


### Assembly Steps
Except for the socketed parts, all the components are placed on the front side of the board and solderd on the back side of the board.
These steps go through soldering each component, starting with the shortest.

> The [interactive HTML BOM](https://github.com/CMB27/ModbusRTU-Test-Shield/blob/main/extras/ModbusRTU-Test-Shield-interactive-BOM.html) may be helpful to you in this process.
> It graphically shows where each component goes on the board.
> You will need to download it in order to view it; GitHub does not render HTML files in repositories.

#### 1. R1-R9 (Resistors)
> [!NOTE]
> There are two (2) resistor values used.
> 
> The 8 resistors furthest from the diode footprints (D1-D8) are 330 Ohm resistors.  
> The color code on these will be orange, orange, brown, gold.
> 
> The resistor right next to the diode footprints (D9) is a 10K Ohm resistor.  
> The color code on this resistor will be brown, black, orange, gold.

- Bend the resistor leads so that the part will fit in the footprint.
- Place the resistors and bend the leads on the backside of the board to hold them in place.
- On the backside of the board, solder the leads to the pads.
- Trim the leads using the flush cutters.

#### 2. D9-D11 (Diodes)
> [!NOTE]
> Two different diode parts are used on this board.  
> The smaller signal diodes are placed next to the resistors.  
> The larger power diode is placed right next to the RJ12 footprint.

- Bend the diode leads so they will fit their respective footprints.
- Place the diodes, making sure that the side with the line closest to it (the cathode) is facing the squarish pad.
- Bend the leads on the backside of the board to hold the diodes in place.
- Solder the diode leads to the pads then trim the leads.

#### 3. SW1-SW3 (Push-button Switches)
- Place the switches; these have kinked leads, so they should stay once placed.
- Turn the board over and solder the switch leads to the board.

#### 4. XU1-XU2 (Integrated Circuit Sockets)
_You will likely need to install the sockets one at a time._
- Place the socket so that the notch matches up with the notch shown on the circuit board.
- Flip the board over and solder two pins in opposite corners of the socket.
- Check that the socket is straight and seated correctly on the board.
  If everything looks good proceed, otherwise, reheat your solder joints one at a time and adjust the socket position until it looks good.
- Solder the remaining pins.

#### 5. D1-D8 (LEDs)
> [!NOTE]
> D5, the `ON` LED, is green, all the other ones are yellow.

- Place the LEDs in their respective footprints with the short lead (cathode) going through the squarish pad, and bend the leads on the backside of the board to hold them in place.
- Solder the leads, then trim them.

#### 6. RV1-RV2 (Potentiometers)
_You will likely need to install the potentiometers one at a time._
- Place the potentiometer.
- Flip the board over and solder the pins.

#### 7. C1-C6 (Capacitors)
- Place the capacitors, ensuring the `-` symbol on the capacitors is facing away from the `+` symbol on the board.
  For capacitors, the positive lead goes through the squarish pad and the negative lead goes through the circular pad.
- Bend the leads on the backside of the board to hold the capacitors in place.
- Solder the leads, then trim them.

#### 8. XJ5 (Terminal Block Header)
- Place the terminal block header.
- Solder one of the pins.
- Check the placement of the header; reheat the solder joint and make adjustments if necessary.
- Solder the remaining pins.

#### 9. J1-J4 (Arduino UNO Interface)
- If you have a shield for the Arduino UNO, place the stacking socket headers on its pins, then place the socket header pins through the holes in the circuit board.
  This will make it easier and faster to install the sockets.
  If you don't have a shield you will likely need to install the sockets one at a time.
- Carefully flip the board over the board, holding the socket headers in place.
- Tack solder the end pins of each socket header.
- Check the placement of the headers and make adjustments as needed.
- Solder the remaining pins.
- If you used a shield, remove it now.

#### 10. SW4 (Slide Switch)
- Place the slide switch.
- Flip the board over and solder two of the smaller pins in opposite corners.
- Check the placement of the switch, making adjustments as needed.
- Solder the remaining pins.

#### 11. J6 (RJ12 Jack)
- Place the jack; it should snap in place.
- Flip the board over and solder all the pins.

#### 12. Clean Flux Off Board
_If you only used no-clean flux, you can skip this step._

> [!NOTE]
> This step was written with water-soluble flux in mind.  
> If you used non-water-soluble flux, you may need to use a different cleaning process.

- Use isopropyl alcohol with a toothbrush to remove the bulk of the flux.
- Clean the board with dish soap and warm water using the same toothbrush.
- Dry the board thoroughly. I like to use compressed air for this step.

#### 13. U1-U2 (Integrated Circuits)
- Carefully bend the pins on the ICs so that they are straight up and down.
  I usually use a table surface to bend all the leads on one side of the chip at a time.
- Carefully instert the chips into the sockets on the board.
  Make sure you don't crumple any pins in this process.

#### 14. Finishing Touches
- Insert the screw terminal block (J5) into its header.
- Insert the potentiometer knobs.
