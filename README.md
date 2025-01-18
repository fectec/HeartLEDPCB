# HeartLED PCB

<p align="justify">A collection of <b>Valentine's Day-themed PCB designs</b> featuring LED animations in the shape of a heart. Perfect for pendants or keyrings!</p>

## Main Branch

<p align="justify">The main branch features a design built around the <b>ICM7555</b> timer IC, configured in astable operation mode. The timer output drives a <b>CD4017B</b> decade counter, which sequences through LEDs to create an animated pattern. Power is supplied by a <b>CR2032</b> battery through a <b>TPS6122</b> boost converter.</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/7033c1c2-a9ad-401c-9bbb-1c8c57f93b21" alt = "Main PCB" width="400" height="300"/>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/3627f321-ba2a-4ee9-8b50-e2f7a13963b0" alt = "Main Front" width="324" height="285"/>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/db89d19b-3ef4-46da-9dcc-ff0e0b5dccf1" alt = "Main Back" width="324" height="285"/>
</p>

### Components Overview

#### ICM7555IBAZ-T

<p align="justify">The ICM7555 is a CMOS RC timer that provides significantly improved performance over the standard SE/NE 555/556 and 355 timers. It is a direct replacement for these devices in most applications. Enhanced features include low supply current (<i>60 μA</i>), a wide operating supply voltage range (<i>2V to 18V</i>), higher frequency performance, and no requirement to decouple the Control Voltage pin for stable operation.</p> 

<p align="justify">Although the ICM7555 itself consumes very little current, the total system supply current can increase unless high-impedance timing components are used. To address this, a high value for R and a low value for C were selected.</p> 

<p align="justify">The frequency of the astable operation is determined by the formula:</p> 

<div align="center">
	
$`f=\frac{1}{RC}`$

</div>

<p align="justify">To achieve a period of approximately one second, R was set to <i>100 kΩ</i> and C to <i>4.7 μF</i>.</p> 

<p align="center">
  <img src="https://github.com/user-attachments/assets/de4c9fd7-8dc7-401c-b42b-5cd8ceac5797" alt = "ICM7555 Astable Operation"/>
</p>

#### CD4017BM96

<p align="justify">The CD4017B is a decade counter with 10 decoded outputs. Each output remains high for the duration of one full clock cycle, sequentially cycling through the outputs with each clock pulse. It operates over a wide supply voltage range of <i>3V to 18V</i>, making it compatible with various applications.</p>

#### TPS61222DCKR

<p align="justify">The TPS6122x family devices provide a power-supply solution for products powered by single-cell, two-cell, or three-cell alkaline, NiCd, or NiMH batteries, or a single-cell Li-Ion or Li-polymer battery. They offer up to 95% efficiency under typical operating conditions.</p>

<p align="justify">In this design, the specific application of the device is a fixed output voltage supply of <i>5 V at up to 60 mA</i>. The TPS61222 DC/DC converter is suitable for systems powered by a total typical input voltage between 0.7 V and 5.5 V.</p>

<p align="justify">In the fixed-voltage version, the output is set by an internal resistor divider. To ensure proper operation, a suitable inductor must be connected between pin VIN and pin L. Inductor values of <i>4.7 μH</i> provide good performance across the full input and output voltage range. Using inductor values below 2.2 μH is not recommended.</p>

<p align="justify">An input capacitor with a value of at least <i>10 μF</i> is recommended to improve the transient behavior of the regulator and reduce EMI in the total power supply circuit. A ceramic capacitor placed as close as possible to the VIN and GND pins of the IC is advised.</p>

<p align="justify">For the output capacitor (C2), small ceramic capacitors are recommended, placed as close as possible to the VOUT and GND pins of the IC. A minimum capacitance value of 4.7 μF should be used; <i>10 μF</i> is preferred.</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/f0dd6829-5bdd-4c14-a8f3-b3e7a6c8c89c" alt = "TPS61222DCKR Application Circuit For Fixed Output Voltage Option"/>
</p>

### BOM & Schematic Diagram

| Component   | Value/Model        | Qty | LCSC #      | Notes                          |
|-------------|--------------------|-----|-------------|--------------------------------|
| BT1         | Keystone 1060      | 1   | C5370859    | CR2032 holder                  |
| C1          | 4.7 µF             | 1   | C1705       | ICM7555 capacitor              | 
| C2, C3      | 10 µF              | 2   | C1691       | TPS61222 Input/output caps     |
| L1          | 4.7 µH             | 1   | C576538     | LQH3NPN series                 |
| R1          | 100 kΩ             | 1   | C15458      | Timer RC network               |
| R2          | 10 kΩ              | 1   | C25531      | Timer RC network               |
| R3-R12      | 3.3 kΩ             | 10  | C25936      | LED current limit              |
| U1          | ICM7555IBAZ-T      | 1   | C357816     | CMOS timer                     |
| U2          | CD4017BM96         | 1   | C11349      | Decade counter                 |
| U3          | TPS61222DCKR       | 1   | C116461     | Boost converter                |
| U4          | HX SS12F44G4       | 1   | C5149844    | Power switch                   |
| TP1-TP3     | 1.0 mm             | 3   | -           | Test points                    |

<p align="center">
  <img src="https://github.com/user-attachments/assets/d9e5e888-bb15-48da-88fb-5081e12e24d7" alt = "Main HeartLED PCB Schematic Diagram"/>
</p>

## HT7750A Branch

<p align="justify">In this branch, the TPS61222DCKR converter is replaced by the <b>HT7750A</b>. The HT77XXA series is a family of step-up DC/DC converters known for their high efficiency and low ripple. These converters feature an extremely low start-up voltage and high output voltage accuracy. They require only three external components to provide a fixed output voltage of 2.7 V, 3.0 V, 3.3 V, or <i>5.0 V</i>.</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/95fb1a03-551f-4ee0-9991-b6b9fc9149e4" alt = "HT7750A Application Circuit For Fixed Output Voltage Option" width="680" height="300"/>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/5d998e11-d37f-417b-856e-1fd25c7e912b" alt = "HT7750A PCB" width="330" height="340"/>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/c4a911d8-f770-4f14-bff0-22f641577605" alt = "HT7750A Front" width="324" height="285"/>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/8349025f-a099-4cc0-af7d-2c9add18c4cb" alt = "HT7750A Back" width="324" height="285"/>
</p>

### BOM & Schematic Diagram

| Component   | Value/Model        | Qty | LCSC #      | Notes                          |
|-------------|--------------------|-----|-------------|--------------------------------|
| BT1         | Keystone 1060      | 1   | C5370859    | CR2032 holder                  |
| C1          | 4.7 µF             | 1   | C1705       | ICM7555 capacitor              | 
| C2          | 47 µF (Tantalum)   | 1   | C7190       | HT7750A input capacitor        |
| C3          | 22 µF (Tantalum)   | 1   | C7183       | HT7750A output capacitor       |
| L1          | 47-100 µH          | 1   | C1034       | HT7750A inductor               |
| S1          | 1N5817             | 1   | C727113     | HT7750A schottky diode         |
| R1          | 100 kΩ             | 1   | C15458      | Timer RC network               |
| R2          | 10 kΩ              | 1   | C25531      | Timer RC network               |
| R3-R12      | 3.3 kΩ             | 10  | C25936      | LED current limit              |
| U1          | ICM7555IBAZ-T      | 1   | C357816     | CMOS timer                     |
| U2          | CD4017BM96         | 1   | C11349      | Decade counter                 |
| U3          | HT7750A            | 1   | C25988      | Boost converter                |
| U4          | HX SS12F44G4       | 1   | C5149844    | Power switch                   |
| TP1-TP3     | 1.0 mm             | 3   | -           | Test points                    |

<p align="center">
  <img src="https://github.com/user-attachments/assets/85330887-3bbe-4a60-8581-5100caf57b6e" alt = "HT7750A HeartLED PCB Schematic Diagram"/>
</p>

## MCU Branch

<p align="justify">This branch replaces the timer and decade counter with an <b>ATtiny816</b> microcontroller. The ATtiny816 is a member of the tinyAVR® 1-series family featuring advanced analog features and core independent peripherals. This design allows for more sophisticated LED control and animations through programmable patterns.</p>

<p align="justify">Programming is accomplished via the Unified Program and Debug Interface (<i>UPDI</i>, a one-wire interface for external programming and debugging. The circuit incorporates a tactile button connected to a GPIO pin for user interaction.</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/4d2a6d3e-4b0b-4cea-951a-3f0ca250b6cf" alt = "MCU PCB" width="330" height="340"/>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/216bcdd0-fc1f-49b6-9df2-2e00aa4bc732" alt = "MCU Front" width="324" height="285"/>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/fa88f846-20db-409a-aaf4-dc29a34dcc54" alt = "MCU Back" width="324" height="285"/>
</p>

### BOM & Schematic Diagram

| Component   | Value/Model        | Qty | LCSC #      | Notes                          |
|-------------|--------------------|-----|-------------|--------------------------------|
| BT1         | CR2032-BS-6-1      | 1   | C70377      | CR2032 holder                  |
| C1          | 100 nF             | 2   | C301918     | MCU decoupling capacitors      |
| C2          | 100 nF             | 2   | C301918     | Button debounce capacitor      |
| D1          | LED (Blue)         | 1   | C7496819    | Status LED                     |
| D2-D10      | LED (Red)          | 9   | C7496820    | Animation LEDs                 |
| J1          | 1x03 2.54 mm       | 1   | -           | UPDI programming header        |
| R1-R11      | 1 kΩ               | 11  | C25543      | LED current limit              |
| SW1         | TS-1187A-B-A-B     | 1   | C318884     | Tactile switch                 |
| U1          | HX SS12F44G4       | 1   | C5149844    | Power switch                   |
| U2          | ATTINY816-MN       | 1   | C617908     | Main MCU                       |
| TP1         | 1.5 mm             | 1   | -           | Test point                     |

<p align="center">
  <img src="https://github.com/user-attachments/assets/3a8101af-63fe-4fc1-8729-ac897de6248b" alt = "MCU HeartLED PCB Schematic Diagram"/>
</p>

## Simple NE555 Branch

<p align="justify">Finally, this branch replaces the ICM7555 timer IC with a conventional <b>NE555</b>, offering a cost-effective alternative that requires only one SMD component - the IC itself. This design imitates a popular DIY kit, where the NE555 generates a <i>1 Hz signal</i> at pin 3, alternating between high and low levels. When pin 3 is low, the upper row of LEDs illuminates, and when high, the bottom row lights up instead, creating an appealing visual effect.</p>

<p align="justify">While the circuit can operate with a CR2032 3V battery, one LED row will appear dimmer due to the NE555's minimum voltage requirements. For optimal brightness across both rows, a 5V power supply connector can be soldered to the board as an alternative power source.</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/ac20ff40-7e81-4c68-b103-9fd3fb49b721" alt = "NE555 PCB" width="400" height="300"/>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/347f33d7-5a2f-4cae-8e2e-eb162c639313" alt = "NE555 Front" width="324" height="285"/>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/f944993c-12d7-470f-9a76-efd6b1f0e087" alt = "NE555 Back" width="324" height="285"/>
</p>

### BOM & Schematic Diagram

| Component   | Value/Model                    | Qty | Notes                          |
|-------------|--------------------------------|-----|--------------------------------|
| U1          | NE555DR                        | 1   | RC Timer                       |
| U2          | 1066                           | 1   | CR2032 holder                  |
| SW1         | SS12D00G3                      | 1   | Power switch                   |
| D1-D10      | LED 3.00 mm                    | 10  | LEDs                           |
| R1-R10      | 1 kΩ 6.3 x 2.5 x 7.62 mm       | 10  | LED current limit              |
| R11-R12     | 10 kΩ 6.3 x 2.5 x 7.62 mm      | 2   | Timer RC network               |
| C1          | 47 µF 5.00 x 7.00 x 2.00 mm    | 1   | NE555 capacitor                |
| J1          | 1x02 2.54 mm                   | 1   | Power supply header            |

<p align="center">
  <img src="https://github.com/user-attachments/assets/14caecd8-7e32-412a-b838-e0dd9af7d776" alt = "NE555 HeartLED PCB Schematic Diagram"/>
</p>
