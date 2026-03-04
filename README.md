# X-Ray Data Analysis of Black Hole Binary MAXI J1820+070

This repository contains the analysis performed for a set of **X-ray astronomy laboratory exercises** using observations of the black hole binary **MAXI J1820+070**.  
The work was carried out as part of the **MS/DD (Astronomy) laboratory coursework at the Indian Institute of Space Science and Technology (IIST)**.

The labs introduce the standard workflow used in **high-energy astrophysics data analysis**, including:

- NICER data reduction
- X-ray spectral analysis
- X-ray timing analysis

The analysis uses observations from the **NICER (Neutron Star Interior Composition Explorer)** instrument onboard the **International Space Station**.

---

# Scientific Background

**MAXI J1820+070** is a well-known **black hole X-ray binary**.  
In such systems, matter from a companion star accretes onto a black hole, producing strong X-ray emission.

Studying the X-ray spectrum and variability of these systems provides insights into:

- accretion disk physics
- corona emission
- quasi-periodic oscillations (QPOs)
- relativistic processes near black holes

---

# Instrument: NICER

The **Neutron Star Interior Composition Explorer (NICER)** is an X-ray timing instrument installed on the **International Space Station**.

Key features:

- 56 X-ray concentrator optics (XRC)
- 56 focal plane modules (FPMs)
- operating energy range: **0.2 – 12 keV**
- high time resolution for timing studies

Several detectors are known to be inactive or noisy, so they are removed during data reduction.

---

# Dataset

The analysis uses a NICER observation of **MAXI J1820+070** with observation ID:

```
1200120189
```

The repository contains the processed data products required for spectral and timing analysis.

## Data Files

### Source Spectrum
```
NICER_1200120189_nisrc_grp.pha
nicer-final-New.pha
```

These files contain the **grouped source spectrum** used for spectral fitting.

---

### Background Spectrum
```
NICER_1200120189_nibackgen3C50_bkg.pi
```

This file contains the **background spectrum** generated using the NICER background model.

---

### Instrument Response Files

These files describe the response of the detector.

```
NICER_1200120189_nixti20170601_combined_v002.rmf
NICER_1200120189_nixtionaxis20170601_combined_v004.arf
```

- **RMF (Response Matrix File)** – detector energy redistribution
- **ARF (Auxiliary Response File)** – effective area of the instrument

These are required for spectral modelling in **XSPEC**.

---

# Laboratory Sessions

The analysis was performed through **three lab sessions**, each focusing on a different aspect of X-ray data analysis.

---

# Lab 1 — NICER Data Reduction

Instruction file:

```
nicer-reduction-MS-lab-1.pdf
```

Goal: convert raw NICER observations into usable scientific products.

The following steps were performed:

### Standard NICER Processing

The NICER pipeline was executed using:

```
nicerl2
```

This step performs:

- calibration
- filtering
- screening of event files

The output includes:

- cleaned event file
- filter file
- unscreened event files

---

### Removing Noisy Detectors

Some detectors are known to have increased noise.

These detectors were removed using:

```
fselect
```

Inactive detectors such as **FPM-14 and FPM-34** were excluded.

---

### Generating Spectrum and Light Curve

Using **XSELECT**, the cleaned event file was used to generate:

- source spectrum (.pha)
- light curve (.lc)

---

### Response Generation

Instrument responses were generated using:

```
nicerarf
nicerrmf
```

This produced:

- ARF file
- RMF file

---

### Background Estimation

The NICER background was generated using:

```
nibackgen3C50
```

The resulting background spectrum:

```
nibackgen3C50_bkg.pi
```

---

### Spectrum Grouping

The spectrum was grouped and instrument systematics were added using:

```
grppha
```

Grouping improves statistical quality and prepares the spectrum for model fitting.

---

# Lab 2 — Spectral Analysis

Instruction file:

```
nicer-reduction-MS-lab-2.pdf
```

Goal: study the **energy spectrum of the X-ray source**.

The analysis was performed using **XSPEC**.

---

## Loading Data in XSPEC

The following files were loaded:

- grouped source spectrum
- background spectrum
- response matrix
- auxiliary response

Example commands:

```
data spectrum.pha
arf spectrum.arf
resp spectrum.rmf
back background.pi
```

---

## Plotting the Spectrum

The spectrum was plotted in two ways:

- counts vs detector channel
- counts vs energy (keV)

The useful energy range of the data was identified by ignoring noisy channels.

---

## Spectral Modelling

Different models were tested to understand the physical emission processes.

Examples of models used:

```
powerlaw
tbabs*powerlaw
tbabs*diskbb
tbabs*(diskbb+powerlaw)
```

Where:

- **tbabs** → interstellar absorption
- **diskbb** → accretion disk emission
- **powerlaw** → high-energy coronal emission

---

## Model Fitting

Model parameters were optimized using **chi-square minimization**.

The following were evaluated:

- χ² value
- degrees of freedom
- reduced χ²

The best-fit model parameters and errors were recorded.

---

## Flux Estimation

The X-ray flux of the source was calculated in the energy range:

```
0.8 – 10 keV
```

---

# Lab 3 — Timing Analysis

Instruction file:

```
nicer-reduction-MS-lab-3.pdf
```

Goal: study **temporal variability** in the X-ray emission.

---

## Light Curve Analysis

The source light curve was generated and analyzed to determine:

- minimum count rate
- maximum count rate
- average count rate

---

## Power Density Spectrum (PDS)

The **Power Density Spectrum** was generated using:

```
powspec
```

The PDS represents the **Fourier transform of the light curve**, showing variability power as a function of frequency.

---

## Quasi-Periodic Oscillations (QPO)

The PDS was modeled using **Lorentzian profiles** to identify peaks corresponding to **quasi-periodic oscillations (QPOs)**.

The **Q-factor** of the oscillation was calculated:

```
Q = centroid frequency / width of the peak
```

This quantity measures the coherence of the oscillation.

---

# Repository Contents

```
README.md

Data Analysis Lab Kanishk.pdf
    Final lab report and analysis results

nicer-reduction-MS-lab-1.pdf
    Lab 1 instructions: NICER data reduction

nicer-reduction-MS-lab-2.pdf
    Lab 2 instructions: spectral analysis

nicer-reduction-MS-lab-3.pdf
    Lab 3 instructions: timing analysis

NICER_1200120189_nisrc_grp.pha
nicer-final-New.pha
    Source spectrum files

NICER_1200120189_nibackgen3C50_bkg.pi
    Background spectrum

NICER_1200120189_nixti20170601_combined_v002.rmf
    Response matrix file

NICER_1200120189_nixtionaxis20170601_combined_v004.arf
    Auxiliary response file
```

---

# Summary

This project demonstrates the complete workflow used in **X-ray astronomy data analysis**:

1. **NICER data reduction**
2. **spectral modelling of X-ray emission**
3. **timing analysis and variability studies**

Using NICER observations of **MAXI J1820+070**, the analysis explores both the **spectral properties** and **temporal variability** of the accreting black hole system.

These techniques are widely used in modern **high-energy astrophysics research**.
