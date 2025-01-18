# HeartLED PCB

<p align="justify">A collection of Valentine's Day themed PCB designs featuring LED animations in the shape of a heart. Perfect for pendants or keyrings!</p>

## Main Branch

<p align="justify">The main branch features a design built around the ICM7555 timer IC, configured in astable operation. The timer output drives a CD4017B decade counter, which sequences through LEDs to create an animated pattern. Power is supplied by a CR2032 battery through a TPS6122 boost converter.</p>

### Components Overview

#### ICM7555

<p align="justify">The ICM7555 is a CMOS RC timer providing significantly improved performance over the standard SE/NE 555/556 and 355 timers, while at the same time being direct replacements for those devices in most applications. Improved parameters include low supply current (60 μA), wide operating supply voltage range (2V to 18V), higher frequency performance and no requirement to decouple Control Voltage for stable operation.</p>

<p align="justify">Although the supply current consumed by the ICM7555 device is very low, the total system supply current can be high unless the timing components are high impedance. Therefore, a high value for R and low value for C were chosen.</p>

<p align="justify">The astable operation frequency is given by the following formula: </p>

<div align="center">
	
$`f = \frac{1}{1.4RC}`$

</div>

<p align="justify">Thus, to obtain a period of about one second, R equals to 100 kΩ and C to 4.7 μF.</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/de4c9fd7-8dc7-401c-b42b-5cd8ceac5797" alt = "ICM7555 Astable Operation"/>
</p>
