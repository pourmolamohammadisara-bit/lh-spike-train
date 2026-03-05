# lh-spike-train
MSc thesis pipeline (Univ. of Padova &amp; FAU Erlangen) for LH spike trains (20 kHz): point-process PSD (event periodogram) vs binned Welch/FFT; ACGs (0–100 ms) for 942 units → PCA (78 PCs, ~90% var) → cosine kNN spectral clustering with bootstrap stability + silhouette filtering (robust 2 clusters).

# LH spike-train point-process analysis (PSD + ACG)
The notebook implements point-process spectral estimation (event-periodogram; 1–100 Hz, 0.5 Hz resolution, mean-rate term λ=N/T removed) and spike-train autocorrelogram (ACG) analysis, followed by ACG-based population summarization for downstream PCA/clustering.

## What the notebook does
- **Quality control / inspection**
  - Spike-count summaries and visualization of the long-tailed spike-count distribution.
  - Selection criterion used in the thesis: keep units with **2–3000 spikes**.

- **Control analysis (why not bin + FFT)**
  - Compares 100-ms binned-count Welch spectra vs. point-process analysis.
  - Shows how binning collapses spectra and fails to reproduce short-lag ACG structure.

- **Point-process PSD (event periodogram)**
  - Computes raw point-process PSDs directly from spike times (no binning/smoothing).
  - Produces: single-neuron PSD example, mean PSD across a random subset (n=20), and a PSD heatmap.

- **Spike-train ACGs**
  - Paper-style ACGs (1 ms bins; 0–100 ms window for feature construction; optional ±100/±200 ms display).
  - Random-neuron ACG panels for qualitative inspection.

## Outputs (saved figures)
- Spike-count distribution plot (sorted spike counts).
- Control figure: binned Welch PSD + reconstructed ACF vs. true point-process ACG.
- Point-process PSD summary: example PSD, mean PSD, and PSD heatmap (subset n=20).
- Example and multi-panel ACG figures.

> Note: The dataset itself is not included in this repository.

## System requirements and dependencies
Tested with Python 3.x.

Install dependencies (pip):
- numpy
- scipy
- pandas
- matplotlib
- scikit-learn
- mne

## How to run
Open and run the notebook:
- `LH_spike_train_pipeline.ipynb`

Ensure `spike_times_per_neuron` is loaded in memory before running the analysis cells.

## Reference
Thesis: *Stochastic Modeling and Machine Learning Methods for Analyzing Neural Spike Trains* (University of Padova, Dept. of Mathematics).
