---
layout: default
title: Home
permalink: /
---

# Remote Photoplethysmography (rPPG)
## Contactless Heart Rate Estimation from Facial Videos
---

##  Team Members

- **Yi Du** - yidu@umich.edu
- **Lingxiao Yang** - yanglx@umich.edu
- **Yijie Liao** - lyjie@umich.edu

**Course**: EECS 351 - Digital Signal Processing  
**Institution**: University of Michigan  
**Semester**: Fall 2025

---
## Project Idea: rPPG-Based Heart Rate Extraction from Facial Videos

This project aims to extract heart rate (HR) and full rPPG waveforms from facial videos using both signal-processing pipelines and machine-learning baselines.

---

# Algorithm

We investigate two complementary approaches for remote photoplethysmography (rPPG) extraction:

1. A **conventional signal-processing pipeline**
2. A **machine-learning baseline pipeline**

Both approaches process facial ROI color signals and aim to recover accurate HR estimates.

---

## 1. Conventional (Signal-Processing) Pipeline

Let the mean ROI color at each frame \(t\) be

\[
\mathbf{c}(t) = [R(t),\, G(t),\, B(t)]^\top,
\]

sampled at \(f_s\) Hz.

The pipeline consists of:

1. Raw signal selection  
2. Signal filtering  
3. Heart-rate extraction

---

### **Stage 1: Raw Signal Selection**

The goal is to derive a 1-D temporal signal reflecting blood-volume pulse variation.

---

#### **Option A: Green Channel**

We detect the face (OpenCV or MediaPipe), extract a fixed ROI (cheeks or forehead), and compute mean RGB values per frame.  
Use the green channel as the raw rPPG signal:

\[
s_{\mathrm{raw}}(t) = G(t).
\]

Green provides strongest hemoglobin absorption → best pulsatile contrast.

---

#### **Option B: CHROM Method**

CHROM constructs chrominance components robust to illumination and motion.

\[
X(t) = 3R(t) - 2G(t),
\]
\[
Y(t) = 1.5R(t) + G(t) - 1.5B(t).
\]

Compute  
\[
\alpha = \frac{\sigma(X)}{\sigma(Y)},
\]

then form

\[
s_{\mathrm{raw}}(t) = X(t) - \alpha Y(t).
\]

This enhances pulse-related chrominance while compensating for lighting drift.

---

### **Stage 2: Signal Filtering**

The raw signal contains noise from motion, illumination, and compression.  
We isolate the cardiac band (0.7–3 Hz = 42–180 BPM).

---

#### **A. Bandpass Filter**

We apply a digital bandpass filter using zero-phase forward–backward filtering:

\[
\tilde{s}(t) = \text{filtfilt}(H,\, s_{\mathrm{raw}}(t)).
\]

Removes drift + high-frequency noise while preserving phase.

---

#### **B. Savitzky–Golay Filter**

A polynomial smoothing filter preserving signal shape.  
After smoothing, we still apply the physiological bandpass.

Good for mild motion distortion.

---

#### **C. Wavelet Denoising**

Use discrete wavelet transform (DWT):

\[
s_{\mathrm{raw}}(t) \xrightarrow{\text{DWT}} \{A_j, D_j\}_{j=1}^J,
\]

- \(A_j\): approximations (slow trends)  
- \(D_j\): detail coefficients (localized fluctuations)

rPPG lies primarily in mid-scale bands corresponding to 0.7–3 Hz.

We typically use Daubechies (`db4–db8`) or Symlet wavelets due to similarity with cardiac waveforms.

---

### **Stage 3: Heart-Rate Extraction**

After filtering, the HR is computed in the frequency domain.

---

#### **A. FFT Peak**

Power spectrum:

\[
S(f) = |\mathcal{F}\{ \tilde{s}(t) \}|^2.
\]

Peak frequency \(f^\*\) → HR estimate:

\[
\widehat{\mathrm{HR}} = 60 f^\*.
\]

---

#### **B. Welch Power Spectral Density**

Welch reduces variance by averaging multiple windowed FFTs:

\[
P_{\text{Welch}}(f)
= 
\frac{1}{K}
\sum_k 
\frac{1}{U}
\left|
\sum_n \tilde{s}_k[n]\, h[n]\, e^{-j2\pi fn/f_s}
\right|^2.
\]

More stable peak detection.

---

#### **C. STFT Ridge Tracking**

Short-time Fourier transform:

\[
\text{STFT}\{\tilde{s}\}(t,f)
= 
\sum_n \tilde{s}[n]\, w[n-t] \, e^{-j2\pi fn/f_s}.
\]

Track the dominant frequency ridge \(f^\*(t)\) over time; estimate:

\[
\widehat{\mathrm{HR}}
=
60 \cdot \text{median}_t f^\*(t).
\]

Handles non-stationary HR variations.

---

# 2. Machine-Learning Baseline Track

While our main focus is DSP, ML models serve as comparative baselines.

---

## Overview

Deep neural networks can learn spatial–temporal patterns corresponding to pulse-induced color changes.

We implement two well-known models:

- **TSCAN** – lightweight temporal CNN with temporal-shift modules  
- **DeepPhys** – two-stream network separating appearance and motion  

Both produce HR predictions from video sequences.

---

## Datasets

We use two public rPPG datasets with synchronized videos + physiological signals:

### **UBFC-rPPG**
- 42 subjects  
- 30 fps  
- Natural illumination  
- Ground-truth finger PPG

### **PURE**
- 10 subjects  
- Controlled motion (steady, rotation, talking)  
- Stable lighting  

---

## Preprocessing

For ML and DSP pipelines:

1. Face detection  
2. Crop a stable ROI  
3. Normalize color signals per frame  
4. Feed raw frames or mean RGB traces into models  

Training and evaluation follow identical preprocessing to ensure fairness across methods.

---
---

<div class="note">
<strong> Note:</strong> This project is part of the EECS 351 coursework at the University of Michigan. All work is original and conducted in accordance with academic integrity policies.
</div>

---

*Last Updated: November 17, 2025*
