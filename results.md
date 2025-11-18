# Experimental Results: CHROM vs Green-channel Performance Comparison

## Configuration Sweep Results
### Visual Plots
![Result Configuration 1](images/5-gt(2).png)
*Figure 1:green_bandpass_fft

![Result Configuration 1](images/5-gt(1).png)
*Figure 1:chrom_savgol_welch

![Result Configuration 1](images/5-gt(3).png)
*Figure 1:chrom_bandpass_fft



### Performance Metrics Table

| est_bpm | gt_bpm | hr_mae | signal_corr | trial | raw_method | filter_method | hr_method |
|---------|--------|--------|-------------|-------|------------|---------------|-----------|
| 76.44 | 76.44 | 0.0 | 0.2637 | 5-gt | chrom | bandpass | fft |
| 83.59 | 76.44 | 7.14 | -0.0397 | 5-gt | green | bandpass | fft |
| 75.12 | 75.12 | 0.0 | -0.0397 | 5-gt | green | bandpass | welch |
| 75.12 | 75.12 | 0.0 | -0.0397 | 5-gt | green | bandpass | stft |
| 48.58 | 76.44 | 27.86 | -0.0037 | 5-gt | green | savgol | fft |
| 52.59 | 75.12 | 22.54 | -0.0037 | 5-gt | green | savgol | welch |
| 75.12 | 75.12 | 0.0 | -0.0037 | 5-gt | green | savgol | stft |
| 83.59 | 76.44 | 7.14 | 0.0057 | 5-gt | green | wavelet | fft |
| 75.12 | 75.12 | 0.0 | 0.0057 | 5-gt | green | wavelet | welch |
| 75.12 | 75.12 | 0.0 | 0.0057 | 5-gt | green | wavelet | stft |
| 76.44 | 76.44 | 0.0 | 0.2631 | 5-gt | chrom | bandpass | fft |
| 75.12 | 75.12 | 0.0 | 0.2631 | 5-gt | chrom | bandpass | welch |
| 75.12 | 75.12 | 0.0 | 0.2631 | 5-gt | chrom | bandpass | stft |
| 76.44 | 76.44 | 0.0 | 0.2100 | 5-gt | chrom | savgol | fft |
| 75.12 | 75.12 | 0.0 | 0.2100 | 5-gt | chrom | savgol | welch |
| 75.12 | 75.12 | 0.0 | 0.2100 | 5-gt | chrom | savgol | stft |
| 76.44 | 76.44 | 0.0 | 0.1064 | 5-gt | chrom | wavelet | fft |
| 75.12 | 75.12 | 0.0 | 0.1064 | 5-gt | chrom | wavelet | welch |
| 75.12 | 75.12 | 0.0 | 0.1064 | 5-gt | chrom | wavelet | stft |

**Legend:**
- `est_bpm`: Estimated heart rate (beats per minute)
- `gt_bpm`: Ground truth heart rate (beats per minute)
- `hr_mae`: Heart rate mean absolute error (bpm)
- `signal_corr`: Signal correlation coefficient
- `trial`: Video identifier
- `raw_method`: Raw signal extraction method (chrom/green)
- `filter_method`: Filtering method (bandpass/savgol/wavelet)
- `hr_method`: Heart rate estimation method (fft/welch/stft)

---

## Conclusions

We completed the sweep over all **raw × filter × HR configurations** (18 total but only three of them here due to the content limitaion) using the **UBFC Dataset1 5-gt video**. The results show a clear trend: **CHROM-based methods consistently outperform Green-channel methods**. 

All CHROM combinations achieve a heart-rate MAE of **0 bpm**, with waveform correlations reaching up to **0.26** (highest with CHROM + bandpass). In contrast, Green-channel combinations yield very low or negative correlations and large heart-rate errors (up to **20–28 bpm**). 

Overall, **CHROM + bandpass provides the most stable and accurate performance** on this clean video.

---

**Dataset:** UBFC Dataset1 5-gt video  
**Total configurations tested:** 18  
