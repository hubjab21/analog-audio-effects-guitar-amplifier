# 🎛️ Analog Audio Circuits – LTspice & Hardware Implementation

This project presents a set of basic analog audio circuits including filters, amplifiers, and audio effects.
All circuits were simulated in **LTspice XVII** and later verified using real hardware measurements.

The work is based on my engineering thesis:
📄 *"Guitar amplifier with acoustic effects"* 

---

## ⚠️ LTspice Version Note

All simulations were performed using:

* ✅ **LTspice XVII (working version)**
* ❌ LTspice 26 – caused issues with audio (.wav) file generation

Downloads (valid as of 31.03.2026):

* LTspice XVII: https://ltspice.analog.com/software/LTspice64.exe
* LTspice 26: https://ltspice.analog.com/software/LTspice64.msi
* Official page: https://www.analog.com/en/resources/design-tools-and-calculators/ltspice-simulator.html

---

## 📁 Project Structure

```text
images/
├── hardware/                # real circuits (breadboard, PCB)
├── hardware-oscilloscope/   # oscilloscope measurements (time & FFT)
└── LTspice/                 # schematics and simulation results

LTspice/                     # simulation files (.asc, .wav)
input.wav                    # base input signal
```

---

# 🔍 Circuits Overview

---

## 🔼 High-Pass Filter

![Image](https://i.sstatic.net/lgDiRE9F.png)

![Image](https://i.sstatic.net/hsO2w.png)

A simple passive RC high-pass filter was implemented.

* Removes low-frequency components
* Cutoff frequency ≈ 4 Hz
* Output amplitude drops by 3 dB at cutoff

Simulation results confirm expected behavior — attenuation of low frequencies and preservation of higher frequencies.

---

## 🔽 Low-Pass Filter

![Image](https://i.sstatic.net/cSViA.png)

![Image](https://sc-b.digikeyassets.com/-/media/MakerIO/Images/Tutorials/2024/How%20to%20Simulate%20an%20RC%20Low-Pass%20Filter%20in%20LTspice%20and%20Analyze%20Frequency%20Response/fig_a.jpg?la=en\&ts=3a0201f3-d571-42c2-8e86-c6fd2bef75c8)

The circuit is identical to the high-pass filter with swapped components.

* Passes low frequencies
* Attenuates high frequencies
* Same cutoff frequency (~4 Hz)

The frequency response is inverted compared to the high-pass filter, exactly as expected from theory.

---

## 🔊 Single Transistor Voltage Amplifier

![Image](https://www.researchgate.net/profile/Antoniu-Miclaus/publication/381297471/figure/fig2/AS%3A11431281250775762%401718016196597/Common-emitter-tuned-amplifier-breadboard-connections.png)

![Image](https://www.allaboutcircuits.com/uploads/articles/undistorted-output-current.jpg)

A basic common-emitter amplifier using a **BC337 transistor**.

* Voltage gain ≈ 3×
* Phase shift: 180°
* Moderate distortion at higher amplitudes

The circuit amplifies small signals effectively but introduces distortion when the input amplitude is too large.
FFT analysis shows harmonic distortion, especially for complex audio signals.

---

## 🔊 Amplifier with Negative Feedback

![Image](https://ecstudiosystems.com/discover/textbooks/basic-electronics/amplifiers/images/transistor-amplifier-with-feedback.jpg)

![Image](https://i.sstatic.net/qsi6x.jpg)

Negative feedback was added to improve performance.

* Lower gain (~2.5×)
* Wider bandwidth
* Reduced noise

However, simulation results showed:

* Higher THD (~3.3%) for sine signals
* Better behavior for real audio signals

This may be caused by **LTspice simplifications in audio modeling**, as also observed during analysis in the thesis.

---

## 🔧 Operational Amplifier (LM741)

![Image](https://www.allaboutcircuits.com/uploads/articles/741schem.png)

![Image](https://i.sstatic.net/M1toq.png)

An inverting amplifier based on **LM741**.

* Gain ≈ -3.4
* Phase shift: 180°
* Very low distortion for small signals (~0.07% THD)

⚠️ Important observation:

The frequency response plots were **almost identical to the input signal**, which may indicate:

* incorrect or simplified model behavior
* limitations of the simulation model

---

### 📦 Model Information

The LM741 model used:

* Source: https://www.ti.com/product/LM741
* Download (working): https://www.ti.com/lit/zip/snom211

⚠️ The **UA741 model did not work properly**:

* Page: https://www.ti.com/product/UA741
* Model: https://www.ti.com/lit/zip/sloj138

Because of this, the LM741 model was used instead.

---

## 🎸 Audio Effects

### Fuzz Effect

![Image](https://d6a2e7ghqts3o.cloudfront.net/AcuCustom/Sitename/DAM/519/2020GPXSymmetricalAsymmetricalClippingCircuit700.jpg)

![Image](https://media.sweetwater.com/m/insync/2022/07/Boost-Overdrive-Distortion-Fuzz-Figure-02-scaled.jpg)

* Strong nonlinear distortion
* Signal clipping using diodes
* Very high THD (>200%)

This distortion is intentional and produces the characteristic guitar fuzz sound.

---

### Noise Gate

![Image](https://ro-che.info/img/better-noise-gate/fig1.png)

![Image](https://www.eevblog.com/forum/testgear/oscilloscope-input-noise-comparison/?action=dlattach%3Battach%3D546428%3Bimage)

* Reduces noise and unwanted signals
* Output signal closely follows input
* Slight attenuation

The circuit effectively suppresses low-level noise without heavily distorting the signal.

---

# 📊 Measurements

Oscilloscope results:

```text
images/hardware-oscilloscope/
```

Include:

* time-domain signals
* FFT analysis

---

# 🔬 Conclusions

* LTspice simulations closely match theoretical expectations for filters
* Transistor amplifiers show realistic distortion behavior
* Negative feedback improves bandwidth but reduces gain
* Op-amp simulation results may be affected by model inaccuracies
* Audio effects (fuzz, noise gate) behave as expected

---

# 🧠 Author

Hubert Jabłoński

