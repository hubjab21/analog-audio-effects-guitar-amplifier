# 🎛️ Analog Audio Circuits – LTspice & Hardware

This project presents analog audio circuits simulated in **LTspice XVII** and verified using real hardware measurements.

---

# 🎧 Audio Comparison (Simulation vs Real Guitar)

To evaluate the circuits, a comparison between simulation and real audio was performed.

The comparison includes:

- LTspice simulation (input.wav)
- real guitar signal

👉 https://hubjab21.github.io/

⚠️ Note:

Only **one sound sample** was directly compared with a real guitar signal.  
The remaining results presented on the website are based on **LTspice simulations only**.

This allows:

- validation of simulation against real-world behavior (for one case)  
- presentation of multiple circuit responses using simulation  

The results show how closely simulation can represent real audio, while also highlighting the limitations of purely simulated analysis.

---

## ⚠️ LTspice Version

Simulations were performed using:

* ✅ LTspice XVII (working)
* ❌ LTspice 26 – issues with `.wav` generation

---

## 🎨 Plot Colors

In all LTspice plots:

* 🟢 **Green = Input signal**
* 🔴 **Red = Output signal**

In oscilloscope measurements:

* 🟡 Input (yellow)
* 🔵 Output (blue)

---

# 🔼 High-Pass Filter

![schematic](images/LTspice/high_pass_filter_schematic.png)
![response](images/LTspice/high_pass_filter_response.png)

Simple RC filter that removes low frequencies and passes high frequencies.

---

# 🔽 Low-Pass Filter

![schematic](images/LTspice/low_pass_filter_schematic.png)
![response](images/LTspice/low_pass_filter_response.png)

Simple RC filter that passes low frequencies and attenuates high frequencies.

---

# 🔊 Single Transistor Voltage Amplifier

![schematic](images/LTspice/single_transistor_voltage_amplifier_schematic.png)
![response](images/LTspice/single_transistor_voltage_amplifier_response.png)

Common-emitter amplifier (BC337).

* voltage gain
* phase inversion
* distortion for higher amplitudes

### 🔌 Breadboard circuit (prototype)

![breadboard](images/hardware/single_transistor_voltage_amplifier_breadboard.png)

The circuit was first implemented on a **breadboard**.  
A signal generator was used as the input source, allowing initial verification and debugging of the circuit.

At this stage:

- basic functionality was tested  
- wiring and connections were verified  
- issues such as poor contacts were identified and fixed  

---

### 🔧 Physical circuit (final hardware)

![hardware](images/hardware/single_transistor_voltage_amplifier.png)

After successful testing:

- corrections were introduced in LTspice  
- the design was refined  
- and the circuit was **soldered on a universal PCB**

This workflow (LTspice → breadboard → corrections → PCB) was used for the other circuits as well, even if additional breadboard photos are not included.

### 📊 Oscilloscope measurements

![scope](images/hardware-oscilloscope/single_transistor_voltage_amplifier.png)
![fft](images/hardware-oscilloscope/single_transistor_voltage_amplifier_fft.png)

* real gain lower than simulation
* clipping appears at higher amplitudes
* harmonic distortion visible in FFT

---

# 🔊 Amplifier with Negative Feedback

![schematic](images/LTspice/single_transistor_voltage_amplifier_negative_feedback_schematic.png)
![response](images/LTspice/single_transistor_voltage_amplifier_negative_feedback_response.png)

Amplifier with feedback:

* lower gain
* better stability
* wider bandwidth

### 🔧 Physical circuit (hardware)

![hardware](images/hardware/single_transistor_voltage_amplifier_negative_feedback.png)

The same workflow was used:

* LTspice simulation
* breadboard testing
* corrections in simulation
* final soldered version

### 📊 Oscilloscope measurements

![scope](images/hardware-oscilloscope/single_transistor_voltage_amplifier_negative_feedback.png)
![fft](images/hardware-oscilloscope/single_transistor_voltage_amplifier_negative_feedback_fft.png)

Simulation and real results differ slightly → likely due to model simplifications.

---

# 🔧 Operational Amplifier (LM741 / UA741)

![schematic](images/LTspice/lm741_amplifier_schematic.png)

* Simulation: **LM741**
* Hardware: **UA741 (similar chip)**

⚠️ UA741 model did not work correctly in LTspice → LM741 used instead

### 🔧 Physical circuit (hardware)

![hardware](images/hardware/UA741_amplifier.png)

This circuit was implemented physically using UA741 after simulation.

### 📊 Oscilloscope measurements

![scope](images/hardware-oscilloscope/ua741_amplifier.png)
![fft](images/hardware-oscilloscope/ua741_amplifier_fft.png)

* stable amplification
* low distortion
* best agreement between simulation and hardware

---

# 🎸 Fuzz Effect

![schematic](images/LTspice/fuzz_effect_schematic.png)
![response](images/LTspice/fuzz_effect_response.png)

* strong nonlinear distortion
* diode clipping
* very high harmonic content

### 🔧 Physical circuit (hardware)

![hardware](images/hardware/fuzz_effect.png)

Circuit implemented after LTspice validation and tested as a standalone audio effect.

### 📊 Oscilloscope measurements

![scope](images/hardware-oscilloscope/fuzz_effect.png)
![fft](images/hardware-oscilloscope/fuzz_effect_fft.png)

Real circuit behaves similarly to simulation.

---

# 🔇 Noise Gate

![schematic](images/LTspice/noise_gate_schematic.png)
![response](images/LTspice/noise_gate_response.png)

* suppresses noise
* reduces low-level signals
* keeps main signal shape

---

# 🔬 Conclusions

* filters behave exactly as expected
* transistor amplifiers differ from simulation
* feedback improves stability
* op-amp gives most predictable results
* real measurements are essential

---

# 🚀 Future Development

* design circuits in **KiCad**
* create **dedicated PCB boards** (instead of universal)
* improve build quality
* perform more real measurements
* extend audio effects

---

# 👤 Author

Hubert Jabłoński

