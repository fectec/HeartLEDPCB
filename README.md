# HeartLED PCB

<p align="justify">A collection of Valentine's Day-themed PCB designs featuring LED animations in the shape of a heart. Perfect for pendants or keyrings!</p>

## Main Branch

<p align="justify">The main branch features a design built around the ICM7555 timer IC, configured in astable operation mode. The timer output drives a CD4017B decade counter, which sequences through LEDs to create an animated pattern. Power is supplied by a CR2032 battery through a TPS6122 boost converter.</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/7033c1c2-a9ad-401c-9bbb-1c8c57f93b21" alt = "Main PCB" width="400" height="380"/>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/3627f321-ba2a-4ee9-8b50-e2f7a13963b0" alt = "Main Front" width="324" height="285"/>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/db89d19b-3ef4-46da-9dcc-ff0e0b5dccf1" alt = "Main Back" width="324" height="285"/>
</p>

### Components Overview

#### ICM7555IBAZ-T

<p align="justify">The ICM7555 is a CMOS RC timer that provides significantly improved performance over the standard SE/NE 555/556 and 355 timers. It is a direct replacement for these devices in most applications. Enhanced features include low supply current (60 μA), a wide operating supply voltage range (2V to 18V), higher frequency performance, and no requirement to decouple the Control Voltage pin for stable operation.</p> 

<p align="justify">Although the ICM7555 itself consumes very little current, the total system supply current can increase unless high-impedance timing components are used. To address this, a high value for R and a low value for C were selected.</p> 

<p align="justify">The frequency of the astable operation is determined by the formula:</p> 

<div align="center">
	
$`f=\frac{1}{RC}`$

</div>

<p align="justify">To achieve a period of approximately one second, R was set to 100 kΩ and C to 4.7 μF.</p> 

<p align="center">
  <img src="https://github.com/user-attachments/assets/de4c9fd7-8dc7-401c-b42b-5cd8ceac5797" alt = "ICM7555 Astable Operation"/>
</p>

#### CD4017BM96

<p align="justify">The CD4017B is a decade counter with 10 decoded outputs. Each output remains high for the duration of one full clock cycle, sequentially cycling through the outputs with each clock pulse. It operates over a wide supply voltage range of 3V to 18V, making it compatible with various applications.</p>

#### TPS61222DCKR

<p align="justify">The TPS6122x family devices provide a power-supply solution for products powered by single-cell, two-cell, or three-cell alkaline, NiCd, or NiMH batteries, or a single-cell Li-Ion or Li-polymer battery. They offer up to 95% efficiency under typical operating conditions.</p>

<p align="justify">In this design, the specific application of the device is a fixed output voltage supply of 5V at up to 60 mA. The TPS61222 DC/DC converter is suitable for systems powered by a total typical input voltage between 0.7 V and 5.5 V.</p>

<p align="justify">In the fixed-voltage version, the output is set by an internal resistor divider. To ensure proper operation, a suitable inductor must be connected between pin VIN and pin L. Inductor values of 4.7 μH provide good performance across the full input and output voltage range. Using inductor values below 2.2 μH is not recommended.</p>

<p align="justify">An input capacitor with a value of at least 10 μF is recommended to improve the transient behavior of the regulator and reduce EMI in the total power supply circuit. A ceramic capacitor placed as close as possible to the VIN and GND pins of the IC is advised.</p>

<p align="justify">For the output capacitor (C2), small ceramic capacitors are recommended, placed as close as possible to the VOUT and GND pins of the IC. A minimum capacitance value of 4.7 μF should be used; 10 μF is preferred.</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/f0dd6829-5bdd-4c14-a8f3-b3e7a6c8c89c" alt = "Typical Application Circuit For Fixed Output Voltage Option"/>
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
  <img src="https://github.com/user-attachments/assets/d9e5e888-bb15-48da-88fb-5081e12e24d7" alt = "Main HeartLED PCB"/>
</p>
