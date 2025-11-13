### **Lifespan Human Connectome Project Development (HCP-D) Study**

The [HCP-D Study](https://www.humanconnectome.org/study/hcp-lifespan-development) planned to enroll 1,300+ healthy children, adolescents, and young adults (ages 5-21). The purpose is to discover how different parts of a child's brain are connected and how these connections (the "connectome") change as the brain develops.

# License

The [NDA](https://nda.nih.gov/) agreement prohibits me from sharing raw MRI data (e.g. T1W, DWI, and SRC.GZ files). After discussion with the NDA program lead, I am allowed to share the "derived" data, including the anisotropy, diffusivities, local fiber orientations, and tractography. This includes the FIB file and the tractography. For other data, you may request access at [NDA](https://nda.nih.gov/).

The FIB files and tractography files are shared using [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/).  For those using FIB and tractography files, I would appreciate your mentioning of the contribution of XSEDE resources: TG-CIS200026.

### Demographics

- [Demographics](https://www.humanconnectome.org/storage/app/media/documentation/LS2.0/HCD_LS_2.0_subject_completeness.csv)
- [Behavioral data "Crosswalk" Data Dictionary](https://www.humanconnectome.org/storage/app/media/documentation/LS2.0/LS2.0_Crosswalk_Behavioral_Data_Dictionary.xlsx): excel spreadsheet to translate NDA data structures/elements to HCP behavioral variables and instruments
- [Behavioral & Clinical Instrument Details](https://www.humanconnectome.org/storage/app/media/documentation/LS2.0/LS_2.0_Release_Appendix_2.pdf "https://www.humanconnectome.org/storage/app/media/documentation/LS2.0/LS_2.0_Release_Appendix_2.pdf")

### Methods

> A multishell diffusion scheme was used, and the b-values were 1500 and 3000 s/mm². The number of diffusion sampling directions was 93 and 92, respectively. The in-plane resolution was 1.5 mm. The slice thickness was 1.5 mm. The susceptibility artifact was estimated using reversed phase-encoding b0 by TOPUP from the Tiny FSL package (http://github.com/frankyeh/TinyFSL), a re-compilied version of FSL TOPUP (FMRIB, Oxford) with multi-thread support. The correction was conducted through the integrated interface in DSI Studio's ("Chen" release). The diffusion MRI data were rotated to align with the AC-PC line. The accuracy of b-table orientation was examined by comparing fiber orientations with those of a population-averaged template (Yeh et al. Neuroimage, 2018). The restricted diffusion was quantified using restricted diffusion imaging (Yeh et al., MRM, 77:603--612 (2017)). The diffusion data were reconstructed using generalized q-sampling imaging (Yeh et al., IEEE TMI, ;29(9):1626-35, 2010) with a diffusion sampling length ratio of 1.25. The tensor metrics were calculated. The analysis was conducted using the resource allocation (TG-CIS200026) at Extreme Science and Engineering Discovery Environment (XSEDE) resources (Towns, J. et al. Computing in science & engineering 16, 62-74  2014).

### Processing Scripts

**1. generate SRC files from NIFTI files**

First, copy all NIFTI, bval, bvec files in the same folder and run this script to generate SRC files (one for AP, one for PA)

```
#!/bin/bash
for sub in $(ls HCD8*98_AP.nii.gz)
do    
    dsi_studio --action=src --source=${sub}--other_source=${sub:0:25}99_AP.nii.gz
    dsi_studio --action=src --source=${sub:0:25}98_PA.nii.gz --other_source=${sub:0:25}99_PA.nii.gz
done
```

**2. TOPUP/EDDY and save corrected SRC files**

Correct artifacts using AP and PA SRC files and generate corrected AP-PA combined SRC files.
The script needs a number input that allows for running the task using clusters job arrary

```
#!/bin/bash
subs_ap=$(ls -Lr *AP.nii.gz.src.gz)
subs_ap=(${subs_ap// /})
subs_pa="${subs_ap[$1]:0:28}PA.nii.gz.src.gz"
if [ ! -e $sub_pa ]; then
     echo "." > ${sub_pa}_not_found.txt
else    
     echo "processing ${subs_ap[$1]}"
     dsi_studio --action=rec --source=${subs_ap[$1]} --rev_pe=${subs_pa} --cmd="[Step T2][File][Save Src File]=${subs_pa:0:10}.src.gz"
fi
```

The following is the job array to run the above script using sbatch. The script needs an the file name of the script to run the job array.

```
#!/bin/bash
#SBATCH -t 24:00:00
#SBATCH -p RM-shared
#SBATCH -N 1
#SBATCH --ntasks-per-node 8
#SBATCH --mem=15GB
#SBATCH --array=0-999
set -x
sh $1 $SLURM_ARRAY_TASK_ID
```

**3. reconstruction**

The following command generate native space FIB files for automatic fiber tracking
```
dsi_studio --action=rec --source=*.src.gz
```

The following command generate template space FIB files for correlational tractography
```
dsi_studio --action=rec --source=*.src.gz --method=7 --template=0 --record_odf=1 --dti_no_high_b=1
```


**4. automatic fiber tracking**

The following script for a job arrary to runs fiber tracking on all native-space FIB file. 

```
#!/bin/bash
subs=$(ls -L *.fib.gz)
subs=(${subs// /})
echo "processing ${subs[$1]}"
dsi_studio --action=atk --export_template_trk=1 --source=${subs[$1]}
```

**5. create connectometry database for correlation tractography**

The following command create connectometry database from template-space FIB file

```
dsi_studio --action=atl --source=. --cmd=db --template=../../HCP1065.1mm.fib.gz 
```
## Release Link
https://github.com/data-hcp/lifespan/releases/tag/hcp-d
