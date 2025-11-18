---
layout: default
title: Progress Report
permalink: /progress
---

# rPPG Project Progress – 17 Nov 2025

## Current Update

- Built the three-stage pipeline described in the proposal: `extraction.py` (MediaPipe Face Mesh ROI tracking + CHROM/green traces), `filter.py` (band-pass + Savitzky-Golay/wavelet options), and `hr_calc.py` (FFT/Welch/STFT estimators) all orchestrated through `main.py`/`config.json`.
- Verified the end-to-end flow on UBFC trial `5-gt`, generating plots and `output/metrics.csv` entries that log estimated vs. ground-truth BPM, MAE, and correlation.
- Documented repo layout, configuration schema, and run instructions in `README.md` so future visitors can reproduce the demo run quickly.
- **Challenges:** face_detection drift when subjects move off-axis, occasional MediaPipe tracking dropouts when subjects move too much, and a real learning curve for mediapipe graph tuning; We're mitigating all three by tightening ROI smoothing, adding motion-triggered re-detection/fallback ROIs, experimenting with frame decimation, and logging more diagnostics (PSD snapshots per block) to catch failures early.

## Task Plan (Next 3 Weeks → Due 10 Dec)

1. **Week of 25 Nov:** Automate dataset sweeps (multiple UBFC trials) and append batch metrics to characterize variance across subjects.
2. **Week of 2 Dec:** Baselines for Machine Learning approaches (e.g., DeepPhys) using existing implementations; compare accuracy and runtime vs. our CHROM+Welch pipeline.
3. **Week of 10 Dec:** Polish deliverables—final figures for the website, comparative table (CHROM vs. green, Welch vs. FFT), and a short video demo embedded in the site.

## Key Learning

- Dug into Welch power spectral density estimation from `scipy.signal.welch` and tuned segment lengths/overlap so the HR peak becomes cleaner than with a single FFT. This matters because rPPG traces are noisy and transient; averaging multiple windowed spectra suppresses artifacts from face_detection jitter and yields a more stable BPM estimate for the website demo.

**Example**: [Provide a concrete example if applicable]



