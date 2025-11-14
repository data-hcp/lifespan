# Human Connectome Project (HCP) — Lifespan Studies

The **Human Connectome Project (HCP)** has expanded from its original young-adult initiative to a set of coordinated **lifespan studies** that map human brain connectivity from the prenatal stage through late adulthood. These efforts use HCP-style acquisition and processing pipelines to create a coherent, cross-age resource for studying brain development, maturation, and aging.

This repository provides curated, tractography-ready derivatives (FIB files, QSDR reconstructions, SRC files when allowed, and QC tables) for multiple HCP Lifespan datasets. Raw MRI data remain hosted at ConnectomeDB, NDA, or dHCP servers and must be accessed under the original data-use agreements.

---

## Download via `curl`

You can download all files for a given dataset using the following examples (Linux environments): 

```bash
# General pattern (replace <TAG> with a release tag, e.g. hcp-ya)
curl -s https://api.github.com/repos/data-hcp/lifespan/releases/tags/<TAG>   | jq -r '.assets[].browser_download_url'   | xargs -n1 -P4 curl -LO
```

### Examples

```bash
# HCP Young Adult (main release)
curl -s https://api.github.com/repos/data-hcp/lifespan/releases/tags/hcp-ya   | jq -r '.assets[].browser_download_url'   | xargs -n1 -P4 curl -LO

# HCP Young Adult — Retest sample
curl -s https://api.github.com/repos/data-hcp/lifespan/releases/tags/hcp-ya-retest   | jq -r '.assets[].browser_download_url'   | xargs -n1 -P4 curl -LO

# HCP Development (HCP-D)
curl -s https://api.github.com/repos/data-hcp/lifespan/releases/tags/hcp-d   | jq -r '.assets[].browser_download_url'   | xargs -n1 -P4 curl -LO

# HCP Aging (HCP-A)
curl -s https://api.github.com/repos/data-hcp/lifespan/releases/tags/hcp-a   | jq -r '.assets[].browser_download_url'   | xargs -n1 -P4 curl -LO

# Developing Human Connectome Project (dHCP)
curl -s https://api.github.com/repos/data-hcp/lifespan/releases/tags/dhcp   | jq -r '.assets[].browser_download_url'   | xargs -n1 -P4 curl -LO

# Baby Connectome Project (BCP)
curl -s https://api.github.com/repos/data-hcp/lifespan/releases/tags/bcp   | jq -r '.assets[].browser_download_url'   | xargs -n1 -P4 curl -LO
```

Replace the tag names as needed to match the releases listed on the GitHub “Releases” page.

---

## Table of Contents

* [Overview](#overview)
* [Included Datasets](#included-datasets)
  * [HCP Young Adult (HCP-YA)](#hcp-young-adult-hcp-ya)
  * [HCP Development (HCP-D)](#hcp-development-hcp-d)
  * [HCP Aging (HCP-A)](#hcp-aging-hcp-a)
  * [Developing Human Connectome Project (dHCP)](#developing-human-connectome-project-dhcp)
  * [Baby Connectome Project (BCP)](#baby-connectome-project-bcp)
* [Licenses](#licenses)
* [Citations](#citations)
* [Disclaimer](#disclaimer)

---

## Overview

The HCP Lifespan collections aim to:

* **Characterize brain connectivity trajectories** from prenatal life to 100+ years
* **Provide age-appropriate acquisition protocols** while maintaining HCP-level data quality
* **Enable cross-sectional and longitudinal analyses** of structural, functional, and diffusion MRI
* **Support genetics, behavior, and multimodal integration** across development and aging

This repository distributes **derived diffusion MRI files** that can be used directly in DSI Studio for tractography, connectometry, group averaging, and reproducible pipeline development.

---

## Included Datasets

### HCP Young Adult (HCP-YA)

High-quality dMRI and structural MRI from healthy adults (ages 22–35).  
The releases here include DSI Studio–compatible **SRC**, **GQI FIB**, and **QSDR FIB** files constructed from the minimally processed WU-Minn HCP dMRI data.

* Ages: 22–35
* Acquisition: Multishell (b = 1000 / 2000 / 3000 s/mm²)
* Derivatives: SRC, FIB (native), FIB (MNI), demographics
* License: WU-Minn HCP Open Access Data Terms
* Source: <https://www.humanconnectome.org/study/hcp-young-adult>

---

### HCP Development (HCP-D)

Children, adolescents, and young adults (ages 5–21).  
Raw MRI access is restricted by NDA; this repository shares **derived diffusion measures, FIB files, and tractography**, which are permitted.

* Ages: 5–21
* Design: 1,300+ participants (planned), developmental cohort
* Derivatives shared: FIB, tractography, QC tables
* License: CC BY-SA 4.0 (for derived files)
* Raw data: Access through NDA (Data Use Agreement required)

---

### HCP Aging (HCP-A)

Healthy aging cohort (ages 36–100+).  
As with HCP-D, only derivatives allowed under NDA are included.

* Ages: 36–100+
* Design: 1,500+ participants (planned)
* Derivatives shared: FIB, tractography, QC tables
* License: CC BY-SA 4.0 (for derived files)
* Raw data: Access through NDA

---

### Developing Human Connectome Project (dHCP)

Neonatal and preterm brain imaging (20–44 weeks post-conception).  
The derivatives here include preprocessed **SRC**, **GQI/QSDR FIB**, **scan–rescan pairs**, and connectometry databases.

* Ages: 20–44 weeks post-conception
* Modalities: T2w, dMRI (multishell), behavioral metadata
* Derivatives: 642 SRC files, 642 FIB files, 164 scan–rescan datasets
* License: dHCP Data Sharing Agreement
* Source: dHCP Release 3

---

### Baby Connectome Project (BCP)

Infancy to early childhood (0–5 years).  
This repository summarizes the study and hosts allowed derivative files.

* Ages: 0–5 years
* Design: Sequential accelerated longitudinal (n=500 planned)
* Modalities: Structural MRI, resting-state fMRI, dMRI
* Derivatives: FIB, QC tables (where permitted)
* Raw data: Access via original BCP data portal
* License: Per BCP data-use agreement

---

## Licenses

Different lifespan studies use different data-use policies:

* **WU-Minn HCP-YA:**  
  WU-Minn Open Access Data Use Terms
* **HCP-D / HCP-A:**  
  Raw data restricted under *NDA*. Derived data in this repo are shared under **CC BY-SA 4.0**.
* **dHCP:**  
  Distributed under the **dHCP Data Sharing Agreement**.
* **BCP:**  
  Follow original BCP data-use terms.

Each release folder includes a license statement specific to that dataset.

---

## Citations

When using any dataset:

1. Cite the **original HCP / Lifespan / dHCP / BCP publication and DOI**.
2. Cite the **WU-Minn HCP**, **CCF**, or **NDA** resource as required.
3. If using derivatives provided here, please add:

> “Derived diffusion MRI files were prepared by the Pittsburgh Fiber Data Hub (`data-hcp/lifespan`).”

---

## Disclaimer

* This repository does **not** host raw MRI data.
* Users must comply with **NDA**, **HCP**, and **dHCP** data-use constraints.
* Derivatives provided here are intended to accelerate research but may not capture all information available in full raw datasets.
* Quality varies by site, cohort, and age group; users should perform independent QC before analysis.
