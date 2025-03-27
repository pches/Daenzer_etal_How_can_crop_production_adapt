# Daenzer_etal_How_can_crop_production_adapt
This repository contains all of the code necessary to reproduce the figures for the Supplemental Information document for the manuscript "How can crop production adapt to growing groundwater restrictions in the West?" authored by Daenzer, et al.

# Code for: Bringing Hydrologic Realism to Water Markets by Grogan et al.

This code was written by: Danielle Grogan, Matt Lisk, Shan Zuidema, and Jiameng Zheng.  
This repository contains all the code to run the Water Market model, post-process the market model output, and post-process hydrologic model output described in the associated paper. This paper is submitted; if it is published, a full citation and link will be added here.

Current paper citation:
Grogan D., Lisk M., Zuidema S., Zheng J., Fisher-Vanden K., Lammers R., Olmstead S., Fowler L., and Prusevich A. Bringing Hydrologic Realism to Water Markets. _submitted_

Input and output data from this repo's code can be found here:

Input Water Rights data: Lisk, M., Grogan, D., Zuidema, S., Caccese, R., Peklak, D., Zheng, J., Fisher-Vanden, K., Lammers, R., Olmstead, S., & Fowler, L. (2023). Harmonized Database of Western U.S. Water Rights (HarDWR) (Version v1) [Data set]. MSD-LIVE Data Repository. https://doi.org/10.57931/2205619

Input data, intermediate processing steps, and output data useful for reproducing figures and tables: Grogan, D., Lisk, M., Zuidema, S., Zheng, J., Fisher-Vanden, K., Lammers, R., Olmstead, S., Fowler, L., & Prusevich, A. (2024). Data for Grogan et al. "Bringing Hydrologic Realism to Water Markets" (Version v1) [Data set]. MSD-LIVE Data Repository. https://doi.org/10.57931/2283495

The hydrologic model described in Bringing Hydrologic Realism to Water Markets is a branch of the University of New Hampshire Water Balance Model, WBM. The main branch of WBM is available here: https://github.com/wsag/WBM, DOI 10.5281/zenodo.6263096. The water rights module described in the paper is available upon request from the authors, and will soon be downloadable from https://license.unh.edu/products/Software 

Contact info: nucci@psu.edu (data curation), fpp5056@psu.edu (methods and methodologies)

## System requirements:
This code is written in standard R coding language. No special hardware or system requirements are necessary. The R code requires use of the raster package for some processing. All processing was performed on a Red Hat Enterprise Linux 8 system but should be reproduceable on a regular desktop computer.  


## How to use the data Data for (Version v1) 
The code provided here can be used on the data available at https://doi.org/to reproduce the figures and tables in the paper. Here, we describe each dataset and which piece of code they are used with:

Folder: 

File Name: 

File Name: 


File Name: Table_1.csv; Description: All data in Table 1, reproducible from WBM output files using code table_1.R
