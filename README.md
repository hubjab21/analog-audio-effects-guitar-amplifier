# Analog Audio Circuits – LTspice & Hardware

This project presents a set of analog audio circuits designed and analyzed in LTspice XVII and verified using real hardware measurements.

---

## Audio comparison (simulation vs real guitar)

To evaluate the circuits, a comparison between simulation and real audio was performed.

The comparison includes:

- LTspice simulation (input.wav)
- real guitar signal

Link:
https://hubjab21.github.io/

Note:

Only one sound sample was directly compared with a real guitar signal.
All other results presented on the website are based on LTspice simulations.

This allows:

- basic validation of simulation against real behavior (for one case)
- comparison of multiple circuits using simulation results

The results show that simulation can approximate real audio behavior, but also highlight its limitations.

---

## LTspice version

Simulations were performed using:

- LTspice XVII (working correctly)
- LTspice 26 – issues with `.wav` generation

---

## Plot colors

In all LTspice plots:

- 🟢 **Green = Input signal** 
- 🔴 **Red = Output signal**

In oscilloscope measurements: 
- 🟡 Input (yellow) 
- 🔵 Output (blue)
- 🔴 FFT - frequency domain (red)

---

## High-pass filter

![schematic](images/LTspice/high_pass_filter_schematic.png)
![response](images/LTspice/high_pass_filter_response.png)

Simple RC filter that removes low-frequency components.

---

## Low-pass filter

![schematic](images/LTspice/low_pass_filter_schematic.png)
![response](images/LTspice/low_pass_filter_response.png)

Simple RC filter that attenuates high-frequency components.

---

## Single transistor voltage amplifier

![schematic](images/LTspice/single_transistor_voltage_amplifier_schematic.png)
![response](images/LTspice/single_transistor_voltage_amplifier_response.png)

Common-emitter amplifier (BC337).

- voltage gain
- phase inversion
- distortion at higher amplitudes

### Breadboard prototype

![breadboard](images/hardware/single_transistor_voltage_amplifier_breadboard.png)

The circuit was first implemented on a breadboard and tested using a signal generator.

At this stage:

- basic functionality was verified
- wiring and connections were checked
- contact issues were identified and corrected

---

### Final hardware implementation

![hardware](images/hardware/single_transistor_voltage_amplifier.png)

After initial testing:

- the LTspice model was corrected
- the design was refined
- the circuit was soldered on a universal PCB

The same workflow was used for other circuits.

---

### Oscilloscope measurements

![scope](images/hardware-oscilloscope/single_transistor_voltage_amplifier.png)
![fft](images/hardware-oscilloscope/single_transistor_voltage_amplifier_fft.png)

- real gain lower than in simulation
- clipping appears at higher amplitudes
- harmonic distortion visible in FFT

---

## Amplifier with negative feedback

![schematic](images/LTspice/single_transistor_voltage_amplifier_negative_feedback_schematic.png)
![response](images/LTspice/single_transistor_voltage_amplifier_negative_feedback_response.png)

Amplifier with feedback:

- lower gain
- improved stability
- wider bandwidth

### Hardware implementation

![hardware](images/hardware/single_transistor_voltage_amplifier_negative_feedback.png)

Workflow:

- LTspice simulation
- breadboard testing
- model corrections
- final PCB version

### Oscilloscope measurements

![scope](images/hardware-oscilloscope/single_transistor_voltage_amplifier_negative_feedback.png)
![fft](images/hardware-oscilloscope/single_transistor_voltage_amplifier_negative_feedback_fft.png)

Simulation and measurements differ slightly, most likely due to model simplifications.

---

## Operational amplifier (LM741 / UA741)

![schematic](images/LTspice/lm741_amplifier_schematic.png)

- simulation: LM741
- hardware: UA741

UA741 model was not usable in LTspice, so LM741 was used instead.

### Hardware implementation

![hardware](images/hardware/UA741_amplifier.png)

Circuit implemented and tested using UA741.

### Oscilloscope measurements

![scope](images/hardware-oscilloscope/ua741_amplifier.png)
![fft](images/hardware-oscilloscope/ua741_amplifier_fft.png)

- stable amplification
- low distortion
- best agreement between simulation and hardware

---

## Fuzz effect

![schematic](images/LTspice/fuzz_effect_schematic.png)
![response](images/LTspice/fuzz_effect_response.png)

- strong nonlinear distortion
- diode clipping
- high harmonic content

### Hardware implementation

![hardware](images/hardware/fuzz_effect.png)

Circuit tested as a standalone audio effect.

### Oscilloscope measurements

![scope](images/hardware-oscilloscope/fuzz_effect.png)
![fft](images/hardware-oscilloscope/fuzz_effect_fft.png)

Measured response is close to simulation.

---

## Noise gate

![schematic](images/LTspice/noise_gate_schematic.png)
![response](images/LTspice/noise_gate_response.png)

- suppresses noise
- attenuates low-level signals
- preserves main signal shape

---

## Conclusions

- filters behave as expected
- transistor amplifiers differ from simulation
- feedback improves stability
- operational amplifier gives the most predictable results
- real measurements are necessary

---

## Future development

- design circuits in KiCad
- create dedicated PCB boards
- improve build quality
- perform more measurements
- extend audio effects

---

## Author

Hubert Jabłoński
