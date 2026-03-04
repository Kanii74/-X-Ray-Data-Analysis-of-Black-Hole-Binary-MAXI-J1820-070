# X-Ray Data Analysis of Black Hole Binary MAXI J1820+070

This repository contains the analysis performed for an **X-ray astronomy laboratory exercise** focused on timing studies of the black hole binary **MAXI J1820+070**.

The work was carried out as part of the **MS/DD (Astronomy) laboratory coursework at the Indian Institute of Space Science and Technology (IIST)**. The lab introduces the basic workflow used in **high-energy astrophysics data analysis**, including light curve generation and timing analysis using Fourier techniques.

---

# Objective

The goal of this lab was to study **time variability in X-ray observations** of the black hole binary MAXI J1820+070.

The analysis focuses on answering the following questions:

- Is there **time variability** present in the data?
- What is the **timescale of variability**?
- How can the variability be **characterized using power spectral analysis**?

---

# Dataset

The data used in this analysis corresponds to **X-ray observations of MAXI J1820+070** obtained using the **NICER X-ray telescope** onboard the **International Space Station**.

The dataset contains **light curve data** representing the X-ray count rate as a function of time.

---

# Analysis Workflow

The analysis follows the standard workflow used in **X-ray timing studies**.

## 1. Light Curve Generation

The light curve of the source was generated using the `lcurve` tool.

This produces a **time series of X-ray count rate versus time**, which allows visual inspection of variability in the source.

Key steps included:

- Selecting the light curve file
- Choosing an appropriate **time bin**
- Plotting the light curve using the **PGPLOT interface**
- Saving the resulting data for further analysis

From the generated light curve, the following quantities were examined:

- Maximum count rate
- Minimum count rate
- Average count rate

These provide a first indication of variability in the source.

---

## 2. Power Density Spectrum (PDS)

To study variability in the **frequency domain**, a **Power Density Spectrum (PDS)** was generated using the `powspec` tool.

The PDS is obtained by computing the **Fourier transform of the light curve**, which converts the time series into **power as a function of frequency**. :contentReference[oaicite:0]{index=0}

This helps identify characteristic frequencies in the variability of the source.

The analysis included:

- Choosing an appropriate **time bin**
- Selecting the number of **new bins per interval**
- Generating and plotting the **power spectrum**

Different **rebinning strategies** were tested to study how binning affects the resulting power spectrum.

---

## 3. Effect of Time Binning

Two different time binning choices were tested:

- **Minimum possible bin time**
- **Ten times the minimum bin time**

The resulting PDS from both cases were compared to understand how **time resolution influences the frequency range and power distribution**.

---

## 4. Modeling the Power Spectrum

The PDS was modeled to identify potential **Quasi-Periodic Oscillations (QPOs)** in the signal.

The power spectrum was fitted using models such as:

- Lorentzian profiles
- Power law components
- Constant background terms

The Lorentzian model was used to characterize peaks in the PDS that correspond to QPO features. :contentReference[oaicite:1]{index=1}

---

## 5. XSPEC Modeling

The PDS data was also modeled using **XSPEC**, a widely used software package for X-ray astronomy.

The workflow included:

1. Generating the PDS using `powspec`
2. Converting the data into a **PHA file**
3. Generating the response file
4. Fitting the model spectrum in XSPEC

The fitted model parameters and statistical values were recorded.

---

# Quasi-Periodic Oscillation (QPO)

From the modeled PDS, the **QPO frequency** was determined.

The **significance of the QPO** is characterized using the **Q-factor**, defined as:

\[
Q = \frac{\text{centroid frequency}}{\text{width of the peak}}
\]

A higher Q-factor indicates a more coherent oscillation in the source.

---

# Repository Contents

```
README.md                         → Overview of the project
Data Analysis Lab Kanishk.pdf     → Report containing the analysis
nicer-reduction-MS-lab-3.pdf      → Lab manual for the timing analysis
```

---

# Conclusion

This lab demonstrated the workflow used in **X-ray timing analysis of compact astrophysical sources**.

Starting from a light curve of MAXI J1820+070, the analysis involved:

- Studying variability in the time domain
- Generating a **power density spectrum**
- Investigating the effect of time binning
- Modeling the PDS to identify **quasi-periodic oscillations**

These techniques are widely used in the study of **accreting black holes and neutron stars**, where variability provides insights into the physics of accretion disks and relativistic environments.
