# **Human Connectome Project (HCP) — Lifespan Studies**

The **Human Connectome Project (HCP)** has expanded from its original young-adult study into a family of **lifespan datasets** spanning prenatal development through late adulthood. All datasets use HCP-style acquisition and processing principles to provide a coherent, cross-age resource for studying human brain connectivity across development, maturation, and aging.

This repository provides curated, tractography-ready **derived diffusion MRI datasets** (FIB, QSDR, GQI, SRC when permitted, QC tables).  
**Raw MRI data are not hosted here** and must be obtained through ConnectomeDB, NDA, or dHCP under each dataset’s data-use agreement.

---

## **Table of Contents**

- [Overview](#overview)
- [How to Run Download Commands](#how-to-run-download-commands)
  - [Linux / macOS (bash)](#linux--macos-bash)
  - [Windows (PowerShell 5.x)](#windows-powershell-5x)
- [Included HCP Datasets](#included-hcp-datasets)
  - [HCP Young Adult (HCP-YA)](#hcp-young-adult-hcp-ya)
  - [HCP Young Adult Retest (HCP-YA-Retest)](#hcp-young-adult-retest-hcp-ya-retest)
  - [HCP Development (HCP-D)](#hcp-development-hcp-d)
  - [HCP Aging (HCP-A)](#hcp-aging-hcp-a)
  - [Developing Human Connectome Project (dHCP & dHCP-Retest)](#developing-human-connectome-project-dhcp--dhcp-retest)
  - [Baby Connectome Project (BCP)](#baby-connectome-project-bcp)
- [Licenses](#licenses)
- [Citations](#citations)
- [Disclaimer](#disclaimer)

---

## **Overview**

The HCP Lifespan initiative aims to:

- Map **connectivity trajectories** from the prenatal period through 100+ years  
- Maintain **HCP-level acquisition quality** using age-appropriate MRI protocols  
- Enable **cross-sectional and longitudinal** modeling of brain development  
- Support **genetics, behavior, multimodal imaging**, and lifespan integration  
- Provide harmonized derivatives to accelerate reproducible neuroscience  

This repository distributes **DSI Studio–ready diffusion derivatives** to reduce preprocessing load and standardize tractography workflows.


## **Included HCP Datasets**

---

## **HCP Young Adult (HCP-YA)**

High-quality multishell diffusion MRI from healthy adults (ages 22–35).

**Highlights**

* Ages: 22–35
* Acquisition: b = 1000 / 2000 / 3000 s/mm² multishell
* Derivatives: SRC, GQI FIB, QSDR FIB, demographics
* License: WU-Minn HCP Open Access
* Source: [https://www.humanconnectome.org/study/hcp-young-adult](https://www.humanconnectome.org/study/hcp-young-adult)

### **Download (Linux / macOS — bash)**

```bash
curl -s https://api.github.com/repos/data-hcp/lifespan/releases/tags/hcp-ya \
  | jq -r '.assets[].browser_download_url' \
  | xargs -n1 -P4 curl -LO
```

### **Download (Windows PowerShell 5.x)**
In File Explorer you can go to a folder, click in the address bar, type `powershell` and press **Enter** to open PowerShell directly in that folder.

```powershell
$tag = 'hcp-ya'
$api = "https://api.github.com/repos/data-hcp/lifespan/releases/tags/$tag"

(Invoke-RestMethod $api).assets |
  ForEach-Object {
    $url = $_.browser_download_url
    Invoke-WebRequest $url -OutFile (Split-Path $url -Leaf)
  }
```

---

## **HCP Young Adult Retest (HCP-YA-Retest)**

A scan–rescan subset of HCP-YA for reproducibility and reliability studies.

**Highlights**

* Same protocol as HCP-YA
* Designed for test–retest analysis, harmonization benchmarks
* Includes SRC, GQI, QSDR, QC

### **Download (Linux / macOS — bash)**

```bash
curl -s https://api.github.com/repos/data-hcp/lifespan/releases/tags/hcp-ya-retest \
  | jq -r '.assets[].browser_download_url' \
  | xargs -n1 -P4 curl -LO
```

### **Download (Windows PowerShell 5.x)**
In File Explorer you can go to a folder, click in the address bar, type `powershell` and press **Enter** to open PowerShell directly in that folder.

```powershell
$tag = 'hcp-ya-retest'
$api = "https://api.github.com/repos/data-hcp/lifespan/releases/tags/$tag"

(Invoke-RestMethod $api).assets |
  ForEach-Object {
    $url = $_.browser_download_url
    Invoke-WebRequest $url -OutFile (Split-Path $url -Leaf)
  }
```

---

## **HCP Development (HCP-D)**

Participants ages 5–21 scanned with HCP developmental protocols.
Raw MRI data are under **NDA restricted access**; only derived files can be shared.

**Highlights**

* Ages: 5–21
* Large developmental cohort
* Derivatives: FIB, tractography, QC
* License (derived files here): CC BY-SA 4.0
* Raw data: NDA (DUA required)

### **Download (Linux / macOS — bash)**

```bash
curl -s https://api.github.com/repos/data-hcp/lifespan/releases/tags/hcp-d \
  | jq -r '.assets[].browser_download_url' \
  | xargs -n1 -P4 curl -LO
```

### **Download (Windows PowerShell 5.x)**
In File Explorer you can go to a folder, click in the address bar, type `powershell` and press **Enter** to open PowerShell directly in that folder.

```powershell
$tag = 'hcp-d'
$api = "https://api.github.com/repos/data-hcp/lifespan/releases/tags/$tag"

(Invoke-RestMethod $api).assets |
  ForEach-Object {
    $url = $_.browser_download_url
    Invoke-WebRequest $url -OutFile (Split-Path $url -Leaf)
  }
```

---

## **HCP Aging (HCP-A)**

Adults ages 36–100+ scanned using protocols optimized for aging.

**Highlights**

* Ages: 36–100+
* Multimodal MRI
* Derivatives: FIB, tractography, QC
* License (derived files here): CC BY-SA 4.0
* Raw data: NDA

### **Download (Linux / macOS — bash)**

```bash
curl -s https://api.github.com/repos/data-hcp/lifespan/releases/tags/hcp-a \
  | jq -r '.assets[].browser_download_url' \
  | xargs -n1 -P4 curl -LO
```

### **Download (Windows PowerShell 5.x)**
In File Explorer you can go to a folder, click in the address bar, type `powershell` and press **Enter** to open PowerShell directly in that folder.

```powershell
$tag = 'hcp-a'
$api = "https://api.github.com/repos/data-hcp/lifespan/releases/tags/$tag"

(Invoke-RestMethod $api).assets |
  ForEach-Object {
    $url = $_.browser_download_url
    Invoke-WebRequest $url -OutFile (Split-Path $url -Leaf)
  }
```

---

## **Developing Human Connectome Project (dHCP & dHCP-Retest)**

Neonatal and preterm brain imaging, 20–44 weeks post-conception.

**Highlights**

* Ages: 20–44 weeks post-conception
* Modalities: T2-weighted, multishell dMRI
* Derivatives: hundreds of SRC and FIB datasets
* Additional scan–rescan subset: **dHCP-Retest**
* License: dHCP Data Sharing Agreement
* Source: dHCP Release 3

### **Download (dHCP — Linux / macOS — bash)**

```bash
curl -s https://api.github.com/repos/data-hcp/lifespan/releases/tags/dhcp \
  | jq -r '.assets[].browser_download_url' \
  | xargs -n1 -P4 curl -LO
```

### **Download (dHCP — Windows PowerShell 5.x)**
In File Explorer you can go to a folder, click in the address bar, type `powershell` and press **Enter** to open PowerShell directly in that folder.

```powershell
$tag = 'dhcp'
$api = "https://api.github.com/repos/data-hcp/lifespan/releases/tags/$tag"

(Invoke-RestMethod $api).assets |
  ForEach-Object {
    $url = $_.browser_download_url
    Invoke-WebRequest $url -OutFile (Split-Path $url -Leaf)
  }
```

### **Download (dHCP-Retest — Linux / macOS — bash)**

```bash
curl -s https://api.github.com/repos/data-hcp/lifespan/releases/tags/dhcp-retest \
  | jq -r '.assets[].browser_download_url' \
  | xargs -n1 -P4 curl -LO
```

### **Download (dHCP-Retest — Windows PowerShell 5.x)**
In File Explorer you can go to a folder, click in the address bar, type `powershell` and press **Enter** to open PowerShell directly in that folder.

```powershell
$tag = 'dhcp-retest'
$api = "https://api.github.com/repos/data-hcp/lifespan/releases/tags/$tag"

(Invoke-RestMethod $api).assets |
  ForEach-Object {
    $url = $_.browser_download_url
    Invoke-WebRequest $url -OutFile (Split-Path $url -Leaf)
  }
```

---

## **Baby Connectome Project (BCP)**

Infancy through age 5, imaged using infant-optimized HCP-style protocols.

**Highlights**

* Ages: 0–5
* Longitudinal accelerated design
* Modalities: structural MRI, resting-state fMRI, dMRI
* Derivatives (when permitted): FIB, QC
* Raw data: BCP access portal
* License: BCP data-use agreement (DUA)

### **Download (Linux / macOS — bash)**

```bash
curl -s https://api.github.com/repos/data-hcp/lifespan/releases/tags/bcp \
  | jq -r '.assets[].browser_download_url' \
  | xargs -n1 -P4 curl -LO
```

### **Download (Windows PowerShell 5.x)**
In File Explorer you can go to a folder, click in the address bar, type `powershell` and press **Enter** to open PowerShell directly in that folder.

```powershell
$tag = 'bcp'
$api = "https://api.github.com/repos/data-hcp/lifespan/releases/tags/$tag"

(Invoke-RestMethod $api).assets |
  ForEach-Object {
    $url = $_.browser_download_url
    Invoke-WebRequest $url -OutFile (Split-Path $url -Leaf)
  }
```

---

## **Licenses**

Each dataset follows its source policy:

* **HCP-YA:** WU-Minn Open Access
* **HCP-D / HCP-A:** NDA-restricted (derived files here = CC BY-SA 4.0)
* **dHCP / dHCP-Retest:** dHCP Data Sharing Agreement
* **BCP:** BCP data-use agreement

Dataset folders include the appropriate license text where applicable.

---

## **Citations**

When using these datasets:

1. Cite the **original HCP / Lifespan / dHCP / BCP** publications and DOIs.
2. Cite ConnectomeDB, NDA, dHCP, or BCP portals as required by their policies.
3. If using derivatives from this repository, please add:

> “Derived diffusion MRI datasets were prepared by the Pittsburgh Fiber Data Hub (`data-hcp/lifespan`).”

---

## **Disclaimer**

* This repository **does not** contain raw MRI data.
* Users must comply with all original dataset regulations and data-use agreements.
* Derivatives aim to accelerate research but should still undergo independent QC and validation.
