---
layout: default
title: Home
permalink: /
---

# Remote Photoplethysmography (rPPG)
## Contactless Heart Rate Estimation from Facial Videos

---

## 👥 Team Members

- **Yi Du** - yidu@umich.edu
- **Lingxiao Yang** - lxyang@umich.edu
- **Yijie Liao** - lyjie@umich.edu

**Course**: EECS 351 - Digital Signal Processing  
**Institution**: University of Michigan  
**Semester**: Fall 2025

---

## 🎯 Project Overview

This project explores **remote photoplethysmography (rPPG)** technology, which enables **contactless heart rate measurement** from ordinary facial videos captured by standard cameras.

### The Challenge

Traditional heart rate monitoring requires physical contact through sensors or wearables. Our goal is to develop a **non-invasive alternative** that analyzes subtle color changes in facial skin caused by blood circulation.

### Our Approach

We combine **classical digital signal processing** techniques with **machine learning methods** to:

1. Extract physiological signals from facial videos
2. Process and filter the signals to isolate heart rate information
3. Estimate accurate heart rate measurements
4. Compare different algorithmic approaches

---

## 🔬 Technical Methodology

### Signal Processing Pipeline
#### Key Techniques

**1. Green Channel Method**
- Direct extraction from green color channel
- Leverages higher sensitivity to blood volume changes

**2. CHROM Method**
- Advanced chrominance-based signal processing
- Reduces illumination effects and motion artifacts

**3. Filtering & Analysis**
- Bandpass filtering (0.7-3 Hz / 42-180 BPM)
- FFT-based peak detection
- Welch power spectral density estimation

### Machine Learning Baselines

- **TSCAN**: Temporal Shift Convolutional Attention Network
- **DeepPhys**: Two-stream appearance-motion CNN architecture

---

## 📊 Datasets

We utilize two publicly available benchmark datasets:

### UBFC-rPPG Dataset
- **42 subjects** with diverse characteristics
- **30 fps** video recording
- **Finger PPG** ground truth signals
- Natural lighting and moderate motion conditions

### PURE Dataset
- **10 subjects** performing controlled movements
- High-quality, stable recordings
- Ideal for algorithm benchmarking
- Multiple motion scenarios

---

## 📅 Project Timeline

| Phase | Timeline | Key Deliverables |
|-------|----------|------------------|
| **Week 1** | Nov 4-10 | Data preprocessing, face detection pipeline |
| **Week 2** | Nov 11-17 | Signal extraction, classical DSP implementation |
| **Week 3** | Nov 18-24 | ML baseline training, initial comparisons |
| **Week 4** | Nov 25-Dec 1 | Performance evaluation, optimization |
| **Week 5** | Dec 2-10 | Final analysis, documentation, presentation |

---

## 🎓 Learning Objectives

Through this project, we aim to:

- Apply DSP concepts to real-world biomedical signals
- Understand frequency domain analysis and filtering techniques
- Compare classical vs. modern ML approaches
- Develop practical skills in signal processing and computer vision
- Create reproducible research with proper documentation

---

## 🚀 Expected Outcomes

1. **Functional rPPG System**: Working implementation of multiple heart rate estimation methods
2. **Comparative Analysis**: Quantitative evaluation of different approaches
3. **Comprehensive Documentation**: Detailed progress reports and results
4. **Academic Presentation**: Final poster and project demonstration

---

## 📖 Navigation

Use the navigation bar above to explore:

- **Data**: Detailed dataset descriptions and preprocessing steps
- **Progress Report**: Weekly updates and development milestones
- **Results**: Experimental findings and performance metrics
- **Future Plan**: Upcoming tasks and improvement strategies
- **References**: Academic papers and resources

---

<div class="note">
<strong>📌 Note:</strong> This project is part of the EECS 351 coursework at the University of Michigan. All work is original and conducted in accordance with academic integrity policies.
</div>

---

*Last Updated: November 17, 2025*
