
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
















## Context project
<div style="max-width:920px; margin:24px auto; padding:0 16px;">

  <div style="width:42%; margin:0 auto;">
    <a href="https://thayral.github.io/PhD-manipulation/" style="text-decoration:none; color:inherit;">
      <video autoplay loop muted playsinline style="width:100%; height:auto; display:block;">
        <source src="media/tracebot-process.mp4" type="video/mp4">
      </video>

      <div style="height:8px;"></div>

      <img src="media/grippermorphism.png" style="width:100%; height:auto; display:block;" alt="TraceBot use-case teaser">
    </a>

    <div style="margin-top:8px; display:flex; justify-content:space-between; align-items:flex-end; gap:10px;">
      <div style="font-size:0.95em; color:#444; line-height:1.2;">
        <strong>TraceBot use-case & platform context</strong><br>
        <a href="https://thayral.github.io/PhD-manipulation/" style="color:#444; text-decoration:underline;">
          Learn more on my PhD page (setup, sensors, demos)
        </a>
      </div>

      <a href="https://thayral.github.io/PhD-manipulation/" title="PhD page: platform context">
        <img src="media/TraceBOT_logo.png" style="width:78px; height:auto;" alt="TraceBot logo">
      </a>
    </div>
  </div>

</div>




Slip.gif


Slip detection must be early, reliable, and robust to perturbations.
While slip generates characteristic high-frequency tactile dynamics, real manipulation introduces many slip-like events (actuation noise, force transients) that can cause false alarms.







## Core method



### Spectro-temporal features (PzE → FFT/PSD → Spectrogram)

<div style="width:100%; margin: 0 auto;">

  <video autoplay loop muted playsinline style="width:33%; height:auto; display:block; margin: 0 auto;">
    <source src="media/fft_pze.mp4" type="video/mp4">
  </video>

  <div style="height: 5px;"></div>

  <video autoplay loop muted playsinline style="width:20%; height:auto; display:block; margin: 0 auto;">
    <source src="media/fft_frames.mp4" type="video/mp4">
  </video>

  <div style="height: 5px;"></div>

  <video autoplay loop muted playsinline style="width:33%; height:auto; display:block; margin: 0 auto;">
    <source src="media/fft_spectro.mp4" type="video/mp4">
  </video>

</div>

<em>We process high-bandwidth PzE tactile signals in short windows, extract frequency-domain PSD features via FFT, and build a spectrogram for slip classification.</em>



<table style="width:100%;">
  <tr>
    <!-- LEFT: big image -->
    <td width="50%" valign="middle" align="center">
      <img src="media/FFT_GRU.png" style="width:100%; height:auto; display:block;" alt="Method overview">
    </td>

    <!-- RIGHT: smaller image + bullets below -->
    <td width="50%" valign="top" align="center">
      <img src="media/GRU_d2lai.png" style="width:70%; height:auto; display:block; margin: 0 auto;" alt="FFT-GRU slip detection pipeline">

      <div style="height:14px;"></div>

      <div style="text-align:left; display:inline-block; width:90%;">
        <ul>
          <li>Identify <strong>spectral patterns</strong> of friction</li>
          <li>Analyse <strong>temporal evolution</strong> with recurrence</li>
          <li><strong>100Hz classification</strong> with binary classes</li>
          <li><strong>Training</strong> with binary cross-entropy (BCE)</li>
        </ul>
      </div>
    </td>
  </tr>
</table>








## Generating perturbations for training {#perturbations}

<table>
  <tr>
    <td width="55%" valign="top">
      <strong>Perturbation taxonomy</strong>
      <ul>
        <li><strong>ΔF<sub>n</sub></strong> — Grasp effort variations: normal force (tighten / release)</li>
        <li><strong>ΔF<sub>t</sub></strong> — External load variations: tangential load (shear / traction)</li>
        <li><strong>Δq</strong> — Actuation noise: structural vibrations</li>
      </ul>
      <em>Goal: reduce false alarms while preserving sensitivity to real slip.</em>
    <td width="45%" align="center" valign="top">
      <img
        src="media/perturbations_taxonomy.png"
        width="420"
        alt="Perturbation taxonomy"
        style="transform: rotate(90deg);">
    </td>
  </tr>
</table>

<p>
  <img src="media/perturbations-rarity.png" width="900" alt="Perturbations imbalance">
</p>



# BENCH RSC NANO image + signals

# BENCH LOOP




visu_carousel_31956.png

---
##  Data collection on characterization bench


Data collection on a robotic bench
• Piezoelectric sensor on a flat surface
• Robotic probe applying normal force
• Sliding motion generated

Slippage timing from ground-truth position



Randomly parametrized slip trajectories
• 2–10 N force
• 10–32 mm travel
• 200–2000 mm/min speed
Dataset
• 3,200 recordings
• ∼ 1.5s slip duration






collect_animation.mp4  (video of probe moving on sensor) + collect_signal.mp4 (the corresponding signals, animated)


data_collect_mosaic.mp4  (shows repetition, automated, random trajectories)

results : 

Acc. 98.73%
delay 8.5ms
F1score 0.9787 


---


##  Data collection with the gripper (embodied)

bench_nanoslip.png

run_20240306_200307_signals.png-1.png
bench_collect_nano.mp4


Segments:
2056 total (5 s)
∼50% slip / 50% no-slip
extra 300 perturbation-only.
Slip duration: 330 ± 193 ms on average


Grasped object secured to actuated slide
Randomized slip tajectories
• accel/velocity/duration
• grasp configurations
• object shapes and textures
→ Slip and perturbation ground-truth



accuracy  98.1 delay 16.8 ± 8.7 f1score 1.00


---



### Automated data collection bench
We rely on automated and parameterized benches to generate labeled slip events under controlled variability (object, speed, force, grasps) and to collect **non-slip perturbations** that mimic slip-like dynamics.

<!-- TEMPLATE: GIF for bench -->
<p>
  <img src="assets/gifs/bench.gif" width="820" alt="Automated slip bench">
</p>
<em>Automated bench for slip trajectory generation with ground-truth signals.</em>








## GIF CAROU + SIGNALS -> timing labels

## GIF MULTI MOSAIC + DATASET FACTS

## VISU  IMAGE RESULTS DELAY + ACC



run_20240314_170830_split_slip_velres.png
-> successive slip events are correctly detected



## PERTURB TAXO TRANSIENT AMBIENT

## - > robust how ?

weighted loss equations

Data fusion

<p>
  <img src="media/motor_haptics.png" width="820" alt="Haptic signal">
</p>



## Results


### VISU ROBUST delta FN 

DeltaFn_run_20240312_191700_1757.png


### Robustness via targeted supervision (FFT–GRU)

<div style="max-width:920px; margin:0 auto; padding:0 16px;">

  <div style="width:85%; margin:0 auto;">
    <table style="width:100%; border-collapse:collapse;">
      <thead>
        <tr>
          <th align="left">Model</th>
          <th align="right">Delay (ms)</th>
          <th align="right">Clean F1</th>
          <th align="right">Δq</th>
          <th align="right">ΔF<sub>n</sub></th>
          <th align="right">ΔF<sub>t</sub></th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>FFT–GRU <em>baseline</em></td>
          <td align="right">17.8 ± 9.5</td>
          <td align="right">1.000</td>
          <td align="right">52.8</td>
          <td align="right">43.9</td>
          <td align="right">19.6</td>
        </tr>
        <tr>
          <td>FFT–GRU <em>focal</em> (γ = 2)</td>
          <td align="right">25.3 ± 21.2</td>
          <td align="right">0.998</td>
          <td align="right">65.0</td>
          <td align="right">50.7</td>
          <td align="right">36.8</td>
        </tr>
        <tr>
          <td>FFT–GRU <em>weighted</em> (ω)</td>
          <td align="right">22.5 ± 16.2</td>
          <td align="right">1.000</td>
          <td align="right"><strong>96.8</strong></td>
          <td align="right">56.7</td>
          <td align="right"><strong>97.0</strong></td>
        </tr>
        <tr>
          <td>FFT–GRU <em>haptic</em> (ω + τ)</td>
          <td align="right">24.1 ± 18.0</td>
          <td align="right">1.000</td>
          <td align="right"><strong>96.8</strong></td>
          <td align="right"><strong>79.4</strong></td>
          <td align="right">95.1</td>
        </tr>
      </tbody>
    </table>
  </div>

  <div style="height:10px;"></div>

  <ul>
    <li><strong>Weighting</strong> improves robustness under Δq / ΔF<sub>t</sub> (specificity ≈ 97%).</li>
    <li><strong>Focal loss</strong> is a lower-performing alternative without perturbation labels.</li>
    <li><strong>Haptic data</strong> improves robustness under ΔF<sub>n</sub> (up to <strong>79.4%</strong>).</li>
  </ul>

</div>






