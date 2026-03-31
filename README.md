# 🎛️ Analog Audio Circuits – LTspice & Hardware

This project presents analog audio circuits simulated in **LTspice XVII** and verified using real measurements.

---

## ⚠️ LTspice Version

Simulations were performed in:

* ✅ LTspice XVII (working)
* ❌ LTspice 26 – issues with `.wav` generation

Downloads (31.03.2026):

* XVII: https://ltspice.analog.com/software/LTspice64.exe
* 26: https://ltspice.analog.com/software/LTspice64.msi
* https://www.analog.com/en/resources/design-tools-and-calculators/ltspice-simulator.html

---

# 🔼 High-Pass Filter

![schematic](images/LTspice/high_pass_filter_schematic.png)
![response](images/LTspice/high_pass_filter_response.png)

A simple RC high-pass filter.

* Removes low frequencies
* Cutoff frequency ≈ 4 Hz
* Expected -3 dB point observed

The simulation matches theoretical behavior.

---

# 🔽 Low-Pass Filter

![schematic](images/LTspice/low_pass_filter_schematic.png)
![response](images/LTspice/low_pass_filter_response.png)

RC low-pass filter with reversed configuration.

* Passes low frequencies
* Attenuates high frequencies
* Same cutoff as high-pass

Response is complementary to the high-pass filter.

---

# 🔊 Single Transistor Voltage Amplifier

![schematic](images/LTspice/single_transistor_voltage_amplifier_schematic.png)
![response](images/LTspice/single_transistor_voltage_amplifier_response.png)

![hardware](images/hardware/single_transistor_voltage_amplifier.png)
![breadboard](images/hardware/single_transistor_voltage_amplifier_breadboard.png)
![scope](images/hardware-oscilloscope/single_transistor_voltage_amplifier.png)
![fft](images/hardware-oscilloscope/single_transistor_voltage_amplifier_fft.png)

Common-emitter amplifier using BC337.

* Gain ≈ 3×
* Phase inversion (180°)
* Visible distortion for larger signals

FFT confirms harmonic distortion.

---

# 🔊 Amplifier with Negative Feedback

![schematic](images/LTspice/single_transistor_voltage_amplifier_negative_feedback_schematic.png)
![response](images/LTspice/single_transistor_voltage_amplifier_negative_feedback_response.png)

![hardware](images/hardware/single_transistor_voltage_amplifier_negative_feedback.png)
![scope](images/hardware-oscilloscope/single_transistor_voltage_amplifier_negative_feedback.png)
![fft](images/hardware-oscilloscope/single_transistor_voltage_amplifier_negative_feedback_fft.png)

Modified amplifier with feedback.

* Lower gain
* Wider bandwidth
* Reduced noise

However:

* THD increased in simulation (~3.3%)
* Better behavior for real audio

This discrepancy may result from LTspice audio modeling limitations.

---

# 🔧 Operational Amplifier (LM741)

![schematic](images/LTspice/lm741_amplifier_schematic.png)

![hardware](images/hardware/UA741_amplifier.png)
![scope](images/hardware-oscilloscope/ua741_amplifier.png)
![fft](images/hardware-oscilloscope/ua741_amplifier_fft.png)

Inverting amplifier using LM741.

* Gain ≈ -3.4
* Phase inversion
* Low distortion for small signals

⚠️ Observation:

The frequency response was almost identical to the input signal.

Possible reasons:

* incorrect or simplified model
* limitations of simulation

---

## 📦 Model Information

Used model:

* https://www.ti.com/product/LM741
* https://www.ti.com/lit/zip/snom211

⚠️ UA741 model (not working):

* https://www.ti.com/product/UA741
* https://www.ti.com/lit/zip/sloj138

LM741 was used because UA741 model failed.

---

# 🎸 Fuzz Effect

![schematic](images/LTspice/fuzz_effect_schematic.png)
![response](images/LTspice/fuzz_effect_response.png)

![hardware](images/hardware/fuzz_effect.png)
![scope](images/hardware-oscilloscope/fuzz_effect.png)
![fft](images/hardware-oscilloscope/fuzz_effect_fft.png)

* Strong nonlinear distortion
* Diode clipping
* Very high THD (>200%)

Expected behavior for fuzz effect.

---

# 🔇 Noise Gate

![schematic](images/LTspice/noise_gate_schematic.png)
![response](images/LTspice/noise_gate_response.png)

* Reduces noise
* Output follows input
* Slight attenuation

---

# 🧠 Conclusions

* Filters behave exactly as theory predicts
* Transistor amplifiers show realistic distortion
* Feedback improves bandwidth but affects THD
* Op-amp results may be affected by model inaccuracies
* Audio effects behave as expected

---

# 👤 Author

Hubert Jabłoński

