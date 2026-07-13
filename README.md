# GW Data Hands-On Session

This directory contains three Jupyter notebooks for the gravitational-wave data hands-on session. They are designed to be run in the order listed below.

## Tutorials

### 1. `data_tutorial.ipynb` — GW Strain Data Analysis
Explore real gravitational-wave strain data from the LIGO detectors for the event **GW250114_082203**. Topics covered:
- Discovering and downloading open data from [GWOSC](https://gwosc.org)
- Inspecting raw strain data in the time domain
- Estimating the noise Power Spectral Density (PSD) with Welch's method
- Whitening and band-pass filtering to reveal the GW signal by eye

### 2. `template_tutorial.ipynb` — Templates, Matched Filtering & Parameter Estimation
Continues from `data_tutorial.ipynb`, moving from qualitative detection to quantitative analysis. Topics covered:
- Generating theoretical waveform templates and understanding chirp parameters
- Noise-weighted inner product and matched filtering (SNR time series)
- Setting up a short Bayesian parameter estimation run with `bilby` and interpreting the posterior

### 3. `catalog_tutorial.ipynb` — GWTC-5.0 Catalog Overview
Work with the full GWTC-5.0 catalog and the GW250114 posterior samples. Topics covered:
- Loading and exploring the PESummary table for ~104 events
- Visualising population trends (masses, spins, distances, SNRs)
- Loading full posterior samples for GW250114, making corner plots, and comparing waveform models

---

## Environment Setup

### 1. Install conda
You will need a conda distribution (Anaconda, Miniconda, or similar). If you do not have one, install Miniconda following the instructions here:
https://www.anaconda.com/docs/getting-started/miniconda/install/overview

### 2. Create the IGWN conda environment
All required software is provided through the IGWN (International Gravitational-Wave Network) conda environment.

> **Note:** Environment files are platform-specific (Linux, macOS, Windows). You should have received an email with setup instructions before the school — if you already created the environment, you can skip this step.

Download the environment file for **your platform** from:
https://computing.docs.ligo.org/conda/environments/igwn/

Then create the environment with:
```bash
conda env create --file <downloaded-file.yaml>
```
(replace `<downloaded-file.yaml>` with the actual filename).

### 3. Activate the environment
```bash
conda activate igwn-py312
```

### 4. Launch Jupyter
```bash
jupyter lab
```

---

## Required Data Files

The following data files must be present in this directory before running the notebooks:

| File | Used by | Notes |
|---|---|---|
| `GW250114_082203_H1.txt` | `data_tutorial.ipynb`, `template_tutorial.ipynb` | LIGO Hanford strain data |
| `GW250114_082203_L1.txt` | `data_tutorial.ipynb`, `template_tutorial.ipynb` | LIGO Livingston strain data |
| `IGWN-GWTC5p0-59d160a18_25-PESummaryTable.hdf5` | `catalog_tutorial.ipynb` | GWTC-5.0 summary table (all events) |
| `IGWN-GWTC5p0-29ebe06b7_25-GW250114_082203-combined_PEDataRelease.hdf5` | `catalog_tutorial.ipynb` | GW250114 full posterior samples |

The strain text files (`H1.txt`, `L1.txt`) and the summary table are fetched automatically within the notebooks if not present. However, the **GW250114 PE data release file** (the large HDF5 with full posterior samples) must be downloaded manually from:

**[Download GW250114 PESummary file (Google Drive)](https://drive.google.com/file/d/1T3teGgI-TmjOKGQYaC2iIx_w2-6VWSFj/view?usp=sharing)**

Place the downloaded file in this directory before running `catalog_tutorial.ipynb`.
