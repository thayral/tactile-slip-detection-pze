# Tactile Slip Detection from High-Bandwidth Tactile Sensing

Learning-based detection of incipient slip from piezoelectric tactile vibrations,
with robustness to manipulation perturbations and real-time performance.

<p align="center">
  <img src="media/sensor_fft_gru_overview.png" width="820" alt="Piezoelectric tactile sensor and FFT-GRU pipeline">
</p>


### Publications

**AIM 2023 (published)**  
*Spectro-Temporal Recurrent Neural Network for Robotic Slip Detection with Piezoelectric Tactile Sensor*  
Théo Ayral, Saifeddine Aloui, Mathieu Grossard  
IEEE/ASME International Conference on Advanced Intelligent Mechatronics (AIM), 2023  
Seattle, USA

**CoDIT 2026 (submitted)**  
*Robust Tactile Slip Detection under Manipulation Perturbations*  
Théo Ayral, Saifeddine Aloui, Mathieu Grossard



### Main contributions

**C1 — Early slip detection from tactile vibrations**  
Detect **incipient slip** using a *piezoelectric tactile sensor* capturing friction-induced vibrations.  
Slip cues are extracted through **learning-based spectro-temporal analysis** and classified in **real time (100 Hz)** with short reaction delay.

**C2 — Data-driven robustness to perturbations**  
Improve robustness to transient events and actuation noise through **perturbation-aware training**.  
This significantly reduces **false alarms** (robustness: 38.77 % → 90.43 %) while preserving **perfect recall** on slip events and **low detection latency** (24.1 ms average).

➡️ This work is part of the PhD thesis  
**Learning-based slip detection for adaptive grasp control**  
CEA (Leti & List) · Université Paris-Saclay

