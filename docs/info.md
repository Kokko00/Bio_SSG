<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->

## How it works

This project is a mixed-signal System-on-Chip (SoC) that generates, converts, and filters a sine wave using a fully synthesizable, standard-cell-based analog design approach. The entire signal chain is built to demonstrate how standard digital logic cells (like inverters) can be utilized to create high-performance analog circuitry.

The signal chain consists of the following main blocks:

Direct Digital Synthesizer (DDS): A digital block that generates a sine wave using a 128-value internal Look-Up Table (LUT). It uses a counter to step through the LUT and outputs the digital representation of the wave.

Differential Buffer & DAC: The digital values are passed through a buffer network that decodes the signals into thermometric and binary formats. These drive a differential Digital-to-Analog Converter (DAC), which converts the digital sine wave into a differential analog signal (out_1 and out_2).

Continuous-Time Low-Pass Filter (lpf_2ord): The analog signal is fed into an inverter-based continuous-time low-pass filter. Relying on the transconductance of standard-cell inverters (similar to a Nauta transconductor), this stage smooths the DAC output, removing high-frequency quantization noise.

Dual Inverter-Based OTA (DUALKOKKO): The filtered signals are finally buffered/amplified by two inverter-based Operational Transconductance Amplifiers (OTAs). To ensure robustness against process, voltage, and temperature (PVT) variations and to provide high common-mode rejection, the OTAs feature a local feedback loop utilizing an auxiliary error amplifier.

By utilizing standard digital cells for the analog blocks, this design significantly reduces layout time and footprint while maintaining excellent performance, making it highly suitable for ultra-low-voltage IoT applications.

## How to test

Explain how to use your project

## External hardware

List external hardware used in your project (e.g. PMOD, LED display, etc), if any
