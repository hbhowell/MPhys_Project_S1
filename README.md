# MPhys_Project_S1

See below descriptions of each script, numbered in the correct order to be compiled necessary to execute the pipeline.

1. createNIFTY.lua: For a particular patient identifies DCM T2 and DIXON scans based on filesize, creates mask expansions and then exports images in a NifTi format for use in PyRadiomics.

2. extractRadiomics.py: Filters through scan directory including all patients and visits, identifies all masks and NifTi images and then extracts all unfiltered Radiomics features in .csv format.

3. collateCsvVisits.m: Automatically collects all feature values for a particular delineation, for a
particular patient, and collates them into an .mat array to be used by iccArrayGen.m.

4. iccArrayGen.m: Takes patient .mat and calculates ICC values along with their 95% confidence intervals (CIs). Finds means and standard deviations for each feature across all 4 visits and calculates range and errors by adding the CI-derived standard errors in quadrature.

5. exportICCsArrays.m: Exports.mat arrays generated by iccArrayGen.m in .csv format for use in ICC_Counter.py.

6. ICC_Counter.py: Loops through all patients, finds particular features within each delineation .csv and then allocates a ‘score’ depending on mean ICC value, standard deviation across visits and range.
