# Spatial Segregation of Stellar Rotation and Superflare Energetics in Open Cluster NGC 2516

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/MustakimSaron/NGC2516-Rotation-Flares/blob/main/NGC_2516_data_extraction_code.ipynb)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.22819834.svg)](https://doi.org/10.5281/zenodo.22819834)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)

**End-to-End Observational Astrophysics Reduction & Statistical Analysis Pipeline** accompanying the manuscript:  
> **Md Mustakim Bin Alam**, *"Spatial Segregation of Stellar Rotation and Superflare Energetics in Open Cluster NGC 2516: A Joint Gaia DR3 and TESS Investigation"*, **Astronomy Letters** (*Pis'ma v Astronomicheskii Zhurnal*), 2026[cite: 19, 30].

---

## Overview

This repository provides the reproducible Python pipeline and Jupyter Notebook (`NGC_2516_data_extraction_code.ipynb`) used to investigate stellar axial rotation periods and magnetic superflare energetics across the virialized core and extended outer envelope of the benchmark southern open cluster **NGC 2516** ($\sim 150\text{ Myr}$, $d \approx 412.6\text{ pc}$)[cite: 30, 46].

### Pipeline Architecture

1. **Phase 1 — Astrometric Isolation & King Profile Structural Modeling (*Gaia* DR3)**:
   * Queries a 5-tile spatial grid centered on NGC 2516 ($\alpha_{\rm J2000} = 119.52^\circ$, $\delta_{\rm J2000} = -60.75^\circ$, $G \le 16.2\text{ mag}$) via the Harvard VizieR mirror (`I/355/gaiadr3`)[cite: 32, 46].
   * Employs an empirical 2D proper-motion histogram peak-finder ($\mu_\alpha \cos\delta = -4.79\text{ mas yr}^{-1}$, $\mu_\delta = +11.38\text{ mas yr}^{-1}$, $\varpi = 2.431\text{ mas}$) and a 3D Mahalanobis distance metric ($P_{\rm mem} \ge 0.60$, $\mathrm{RUWE} \le 1.4$) to isolate **293 confirmed cluster members**[cite: 30, 32, 46].
   * Fits a non-linear empirical [King (1962)](https://doi.org/10.1086/108756) surface density profile ($r_c = 0.393^\circ \pm 0.105^\circ$ / $2.82\text{ pc}$, $r_t = 1.579^\circ \pm 0.287^\circ$ / $11.34\text{ pc}$), partitioning the cluster into **122 Core** and **171 Outer Envelope** members[cite: 30, 34, 44, 46].
2. **Phases 2 & 3 — TESS Photometry & Stellar Gyrochronology**:
   * Extracts and cleans 2-minute cadence PDCSAP light curves from TESS Sector 9 (supplemented by Sector 10) for a flux-limited cohort of **190 bright members** ($G \le 14.5\text{ mag}$, $\mathrm{CROWDSAP} \ge 0.75$)[cite: 30, 34].
   * Computes Generalized Lomb-Scargle (GLS) periodograms across $P \in [0.2, 20.0]\text{ days}$ with analytical [Baluev (2008)](https://doi.org/10.1111/j.1365-2966.2008.13009.x) False Alarm Probabilities ($\mathrm{FAP} < 0.01$, $P_{\rm LS} \ge 0.18$), recovering **94 reliable rotators** (42 Core, 52 Outer Envelope)[cite: 30, 34, 35, 43].
3. **Phases 4 & 5 — Automated Superflare Detection, Completeness & MLE Power Laws**:
   * Applies two-stage Savitzky-Golay detrending ($W = 361\text{ cadences}$) to isolate flares exceeding $3.5\sigma$ across $\ge 3$ consecutive cadences, integrating Equivalent Duration ($\mathcal{ED}$) and bolometric flare energies ($E_{\rm flare}$)[cite: 37, 39].
   * Calibrates detection sensitivity via synthetic [Davenport et al. (2014)](https://doi.org/10.1088/0004-637X/797/2/122) flare injection-recovery simulations, establishing a 90% completeness limit of $E_{\min} = 10^{35.00}\text{ erg}$ ($1.01 \times 10^{35}\text{ erg}$)[cite: 30, 39, 44].
   * Identifies **92 superflares** ($10^{35.0}\text{--}10^{38.5}\text{ erg}$) across **38 active stars** and derives unbiased Maximum Likelihood Estimator (MLE) power-law indices ($\alpha_{\rm core} = 1.231 \pm 0.033$, $\alpha_{\rm outer} = 1.297 \pm 0.046$)[cite: 30, 39, 40].

---

## Quick Start

### Option 1: Run Directly in Google Colab (Recommended)
Click the badge below to launch the notebook immediately in Google Colab with zero local setup:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/MustakimSaron/NGC2516-Rotation-Flares/blob/main/NGC_2516_data_extraction_code.ipynb)

### Option 2: Run Locally
1. **Clone the repository:**
   ```bash
   git clone [https://github.com/MustakimSaron/NGC2516-Rotation-Flares.git](https://github.com/MustakimSaron/NGC2516-Rotation-Flares.git)
   cd NGC2516-Rotation-Flares
