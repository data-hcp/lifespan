The data are originally from the minimally-preprocessed dMRI data from WU-Minn HCP Consortium and converted to DSI Studio SRC files format. The SRC file stores the minimum information needed for diffusion MRI processing, including the DWI data, image resolution, and the b-table. The SRC file can be converted back to 4D NIFTI in DSI Studio.

# License

The data are shared under the WU-Minn HCP open access data use term (4) at <https://www.humanconnectome.org/study/hcp-young-adult/document/wu-minn-hcp-consortium-open-access-data-use-terms>

Please acknowledge the source to the WU-Minn HCP.

# Download

| File Format | Modality/Content | Link | Details |
|-------------|---|---|---------|
| FIB 1-mm native space | Fiber orientation maps| [OneDrive](https://pitt-my.sharepoint.com/:f:/g/personal/yehfc_pitt_edu/EhAofmkwtjlMlSku3_vniFEBkStumkY2i5y2YtoqIAOMBQ?e=US4888) | 1-mm GQI reconstructed FIB file in the native space. The FIB files are track-ready files for DSI Studio to run fiber tracking. |
| FIB 2-mm native space | Fiber orientation maps| [OneDrive](https://pitt-my.sharepoint.com/:f:/g/personal/yehfc_pitt_edu/EvFAkXbKPjVCjuTuWcuyGyYBZRAUi4ytmwi9jDI1kFtguA?e=8p3AdS) [Zenodo](https://zenodo.org/record/6307812) | 2-mm GQI reconstructed FIB file in the native space. The FIB files are track-ready files for DSI Studio to run fiber tracking. |
| FIB 1.25-mm MNI space | Fiber orientation maps| [OneDrive](https://pitt-my.sharepoint.com/:f:/g/personal/yehfc_pitt_edu/EqdBttDkWOREjqlB3Ql1KVkBgAueXUbqIdJWi1RpHSEiyg?e=bDcFTe) | 1.25-mm QSDR reconstructed FIB file in the ICBM152 space. The FIB files are track-ready files for DSI Studio to run fiber tracking. |
| SRC | DWI and b-table | [OneDrive](https://pitt-my.sharepoint.com/:f:/g/personal/yehfc_pitt_edu/EmL_WkIkt3pFilc6MeqRoX0Bwhvs0Lr7X9LAoIucajLUwQ?e=c0w9xQ) | The SRC files contains raw dMRI signals for modeling. They can be reconstructed in DSI Studio to generate FIB files. The original NIFTI files can be downloaded from the HCP's connectome db website. |
| NIFTI file | 0.7mm T1W | [OneDrive](https://pitt-my.sharepoint.com/:f:/g/personal/yehfc_pitt_edu/Et_Ih4k8GyxLiEGi7j9XkQ8Bc3m93SdhGYZyZ8OCWda6cg?e=GnYO9e) | |
| NIFTI file | 0.7mm T2W | [OneDrive](https://pitt-my.sharepoint.com/:f:/g/personal/yehfc_pitt_edu/EpwwFq_KM0NHmAAq5dv0QqYB_vV8DLqbSoeSH6k-uuSYxw?e=fZriUW) | |
| NIFTI file | 1.0mm T1W | [OneDrive](https://pitt-my.sharepoint.com/:f:/g/personal/yehfc_pitt_edu/EkPCanH2hTBEh47ZFHXIHuUBaYhGS5lcz3Hi1lAGoeqMcw?e=vCSidk) | |
| Text file | demographics | [ConnectomeDB](https://db.humanconnectome.org/) | |

  **Methods**
  > A group average template was constructed from a total of 930 subjects. A multishell diffusion scheme was used, and the b-values were 1000, 2000, and 3000 s/mm2. The number of diffusion sampling directions were 90, 90, and 90, respectively. The in-plane resolution was 1.25 mm. The slice thickness was 1.25 mm. The diffusion data were reconstructed in the MNI space using q-space diffeomorphic reconstruction (Yeh et al., Neuroimage, 58(1):91-9, 2011) to obtain the spin distribution function (Yeh et al., IEEE TMI, ;29(9):1626-35, 2010). A diffusion sampling length ratio of 2.5 was used, and the output resolution was 1 mm. The analysis was conducted using DSI Studio (http://dsi-studio.labsolver.org). The analysis was conducted using the resource allocation (TG-CIS200026) at Extreme Science and Engineering Discovery Environment (XSEDE) resources (Towns, J. et al. Computing in science & engineering 16, 62-74  2014).

  [1] Yeh F-C, Vettel JM, Singh A, Poczos B, Grafton ST, Erickson KI, et al. (2016) Quantifying Differences and Similarities in Whole-Brain White Matter Architecture Using Local Connectome Fingerprints. PLoS Comput Biol 12(11): e1005203. https://doi.org/[10.1371/journal.pcbi.1005203](http://dx.doi.org/10.1371/journal.pcbi.1005203)


## MGH-USC 

This data set was originally from the connectome db website (https://db.humanconnectome.org/). The MGH HCP team has released diffusion imaging and structural imaging data acquired from 35 young adults using the customized MGH Siemens 3T Connectome scanner, which has 300 mT/m maximum gradient strength for diffusion imaging.

| File Format | Modality/Content | Link | Details |
|-------------|---|---|---------|
| NIFTI | DWI | | |
| SRC | DWI and btable | [Zenodo](https://zenodo.org/record/6315871) |  |

  **Methods**
  > A multishell diffusion scheme was used, and the b-values were 1000 ,3000 ,5000 and 10000 s/mm2. The number of diffusion sampling directions were 64, 64, 128, and 256. The in-plane resolution was 1.5 mm. The slice thickness was 1.5 mm.

## Release Link
https://github.com/data-hcp/lifespan/releases/tag/hcp-ya
