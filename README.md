# rgd-yaml

This repository stores YAML files for the run group D, both for cooking and simulation.

In the inital_yamls folder, there is :
- `rgd_data-ai.yaml`: for regular data processing using AI tracking
- `rgd_data-aicv.yaml`: for luminosity scan processing and comparison of conventional and AI-assisted tracking 
- `rgd_data-cv.yaml`: for regular data processing using conventional tracking
- `rgd_data-trigger.yaml`: for trigger validation (requires the new release), uses conventional tracking and no denoising
- `rgd_denoise.yaml`: for luminosity scan processing and comparison of AI-assisted tracking and AI-assisted tracking+denoising


These yamls use the RG-C CCDB variation to load the RG-C alignment. The `rgd_fall2023` variation should be used for cooking, and `rgd_fall2023_mc` for simulation.
The RG-B networks are used for AI-assisted tracking since the background should be similar. Now that RG-D has its AI networks, the `MLTD run` in `services` should be set to 18305 to use the correct network for RG-D.
Since the change on the farm to ALMA9, the schema_dir should be changed to `/scigroup/cvmfs/hallb/clas12/sw/noarch/clara/5.0.2_11.0.1/plugins/clas12/etc/bankdefs/hipo4/singles/*XXX*`

The change and activity of the data processing of RG-D can be found in the wiki under the [Data Processing tab](https://clasweb.jlab.org/wiki/index.php/Run_Group_D#tab=Data_Processing_2):  
Initial & current coatjava (CJ) version: 10.0.4 & 11.0.1
- As of September 4, the reconstruction for the timelines is done with the following changes to the AI-assisted yaml; otherwise, the rest is the same as of August 24 yaml:
    - schema directory set to the new CJ 11.0.1: /scigroup/cvmfs/hallb/clas12/sw/noarch/clara/5.0.2_11.0.1/plugins/clas12/etc/bankdefs/hipo4/singles/mon, for MON reconstruction;
    - timestamp set to 09/04/24-13:00:00 to take into account the CCDB changes for beam offset and CVT z-offset;

- As of August 24, the reconstruction is done with the following changes to the RG-D AI-assisted yaml; otherwise, the rest is the same as of June 24 yaml:
    - schema directory set to the new CJ 11.0.0: /scigroup/cvmfs/hallb/clas12/sw/noarch/clara/5.0.2_11.0.0/plugins/clas12/etc/bankdefs/hipo4/singles/dst, for DST reconstruction;
    - row 74 uncommented, and row 76 commented out to use the AI-assisted tracking w/o. the denoising option; 

- As of June 24, the Physics reconstruction yaml file: AI-assisted yaml with this adopted changes:
    - variation set to rgd_fall2023;
    - timestamp set to 06/12/24-18:30:00 to take into account the CCDB target position change for RG-D; see the related June 12th update under the Calibration & Alignment tab.
    - schema directory set to the new CJ 10.1.1 installation in AL9 node, ifarm9: /scigroup/cvmfs/hallb/clas12/sw/noarch/clara/5.0.2_10.1.1/plugins/clas12/etc/bankdefs/hipo4/singles/dst, for DST reconstruction;
    - row 74 commented out, and row 76 uncommented to use the AI denoising option; 
    - MLTD run number set to 18305 to use the RG-D trained network
