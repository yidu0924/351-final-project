---
layout: default
title: Data
permalink: /data
---

# Data Description

## Datasets Used

### UBFC-rPPG Dataset
- **Subjects**: 42 individuals
- **Frame Rate**: 30 fps
- **Ground Truth**: Finger PPG sensor
- **Characteristics**: Moderate motion and natural illumination variations

### PURE Dataset
- **Subjects**: 10 individuals
- **Characteristics**: Controlled head movements, clean recordings
- **Purpose**: Model benchmarking

## Data Processing Pipeline

1. **Face Detection**: Detect face in each video frame
2. **ROI Selection**: Select stable region of interest (cheeks or forehead)
3. **Signal Extraction**: Extract mean RGB signals frame by frame
4. **Preprocessing**: Normalize and preprocess for rPPG estimation

---

