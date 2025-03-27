# Daenzer_etal_How_can_crop_production_adapt
This repository contains all of the code necessary to reproduce the figures for the Supplemental Information document for the manuscript "How can crop production adapt to growing groundwater restrictions in the West?" authored by Daenzer, et al.

# Code for: How can crop production adapt to growing groundwater restrictions in the West? by Daenzer et al.

This code was developed by Pandara Valappil Femeena and Kathryn Daenzer.  

This repository contains all the code to regenerate the figures described in the associated supplemental information document for the paper, "How can crop production adapt to growing groundwater restrictions in the West?" 

Current paper citation:
Kathryn Daenzer, Pandara Valappil Femeena, Steve Frolking, Danielle Grogan, Jeff Nucciarone, Kate Calvin, Richard B. Lammers, Karen Fisher-Vanden

This supplemental information document and its associated paper are in preparation for submission; a full citation and link for both will be added here if it is accepted for publication.

The input data that is required for this repo's code can be found here:

"Supporting Information - How Will Crop Production Adapt with Greater Groundwater Restrictions in the West?", authors: Daenzer, Kathryn; Femeena, Pandara Valappil; Frolking, Steve; Grogan, Danielle; Nucciarone, Jeffrey; Calvin, Kate; Lammers, Richard; Fisher-Vanden, Karen 

MSD-LIVE Data Repository. [https://doi.org/1x/x](https://doi.org/10.57931/2530930)

Contact info: 
- Jeffrey Nucciarone, [https://orcid.org/0000-0002-1092-9142] https://orcid.org/0000-0002-1092-9142 (data curation),
- Femeena Pandara Valappil, [https://orcid.org/0000-0002-9120-8493] https://orcid.org/0000-0002-9120-8493 (code)

## System requirements:
This code is written in standard R coding language. No special hardware or system requirements are necessary. The R code requires the use of the following libraries for processing:

|              |            |               |
| ------------ | ---------- | ------------- |
| RColorBrewer | lattice    | rgeos         |
| data.table   | maps       | rnaturalearth |
| dplyr        | ncdf4      | sf            |
| ggplot2      | raster     | sp            |
| ggspatial    | rgdal      | tidyr         |

All processing was performed on a Red Hat Enterprise Linux 8 system but should be reproducible on a regular Windows/Mac/Linux computer.  


## Scripts:

The code provided here to reproduce the figures and tables in the paper requires the data available on MSD-Live at https://doi.org/. A description file available in this repo, in the form of a spreadsheet, lists the required input files for each script. The output file description lists each associated figure generated in the paper.

Here, we describe each dataset:

File name: script_and_file_description.xlsx

A Microsoft XL spreadsheet with a list of all scripts and their:
- required input files and  descriptions 
- listing of each output file and description 

---

File Name: summary_by_iteration.R	

This script creates summary files for each state and crop combination and derives the values for the following variables:

- Gross irrigation water demand
- Irrigation deficit (% of gross irr not met)
- Yield deficit due to irrigation deficit
- Irrigated area
- Rainfed area
- Irrigated production (area x yield)
- Rainfed production (area x yield)

This script must be run first as these generated summary files are used in the other scripts to create plots provided in the submitted manuscript (including the supplemental information).	

Output written to folders: results/crop_state_tables

Note: I'm thinking o putting this into a section titles "Detailed Description" -- either as images or a recreation of the table. Tell me your thoughts, please.
Test image, tell me what you think:

![image](https://github.com/user-attachments/assets/5d1c5f5b-c044-484d-934a-3ead3230318b)

alternate view:

![image](https://github.com/user-attachments/assets/0cfd4d2d-27e0-4121-9faf-9a5a4e5c1eec)

![image](https://github.com/user-attachments/assets/5c26f8fc-2837-4361-ba28-680b21de1ef5)


| Input File	                                                                 | Input File Description                        	          | 
| -------------------------------------------------------                      | ------------------------------------------------         |
| /data/WoCD_DNDC_CropSystem_id_name_WBM_crop_id_name.csv	                     | Provides mapping from WBM crops to DNDC crops.         	| 
|	/data/alpha_i_j_s_SprWinWht_WECC.csv                                         | Provides mapping from DNDC crops to IMPLAN/DREM crops.	| 
|	/data/wecc_merra2_full_sw_c13_2006-2015_YieldVsDefIrrig_QuadFitParams_v1.csv | DNDC-emulator quadratic curve fit parameters, relating irrigation deficit to yield deficit by crop and state. This is for all 11 Western Electricity Coordinating Council (WECC) states and all 26 DNDC crops.	| 
| /data/GCAM/GCAM_2010_reference_land.csv	                                     | GCAMland starting point for rainfed and irrigated cropland areass, created from FAO GAEZ 2010 data (units are in 2.4 thousand hectares). |
|/data/GCAM/GCAM_2015_reference_land.csv                                       | GCAMland starting point for rainfed and irrigated cropland areass, created from FAO GAEZ 2015 data (units are in 2.4 thousand hectares). |
|/data/DNDCe/IrrGross_mmYr_states_ iteration_X.csv	                           | Total crop irrigation water usage (mm/year), by crop and state, for each iteration X. |
|/data/DNDCe/UGW_mmYr_states_ iteration_X.csv	                                 | Unsustainable ground water usage (mm/year) for irrigation, by crop and state, for each iteration X. |
|/data//DNDCe/DNDCe_to_IMPLAN_yield_deficit_STATE_ iteration_X.csv	           | DNDC emulator output per iteration X for IMPLAN defined crops: values represent the proportion of maximum yield achieved.  A value of 1 = 100% of maximum yield achieved indicating no reduction due to water shortages.  All values < 1 indicate that deficit irrigation caused a reduction in yields. |
|/data/DNDCe/DNDC_yield_deficit_ iteration_X.csv	                             | DNDC emulator output per iteration X for DNDC defined crops:  crop yield deficit based on irrigation deficits. A value of 1 = 100% of maximum yield achieved indicating no reduction due to irrigation shortages.  All values < 1 indicate that deficit irrigation caused a reduction in yields. |
|/data/DNDCe/DNDC_yield_kg.C.ha_ iteration_X.csv	                             | DNDC absolute yield values in kg Carbon/hectare per iteration X. |
|/data/GCAM/DREM_land_ iteration_X.csv	                                       | GCAM calculated irrigated and rainfed land allocation (x 2.4 thousand ha) and crop yields (kg C/ha). Output is by crop and state for 2010 and 2015, with separate files created for each iteration step X. This output from GCAM is what is sent to DREM for each iteration. | 
	
| Output File	                                              | Output File Description                        	          | 
| --------------------------------------------------------- | -----------------------------------------------------------|
| /results/gross_irr_ long.csv	                            | Gross irrigation water (km^3/yr) |
| /results/ugw_km3_long.csv	                                | Unsustainable ground water (km^3/yr) |
| /results/sust_irr_km3_ long.csv	                          | Sustainable irrigation water (km^3/yr) |
| /results/sust_irr_frac_ long.csv	                        | Fraction of irrigation water sourced from sustainable groundwater |
| /results/unsust_irr_frac_ long.csv	                      | Fraction of irrigation water sourced from unsustainable groundwater |
| /results/deficit_yld_ long.csv	                          | Yield deficit or fraction of maximum yield |
| /results/irr_land_area_ long.csv	                        | Irrigated land area (x 2.4 thousand hectares)Note: GCAM gives land area outputs in units that are different from other models. A factor of 2.4 is used to convert them to thousand hectares and report it in the final summary tables inside the ""crop_state_tables"" folder" |
| /results/rfd_land_area_ long.csv	                        | Rainfed land area (x 2.4 thousand hectares)  Note: GCAM gives land area outputs in units that are different from other models. A factor of 2.4 is used to convert them to thousand hectares and report it in the final summary tables inside the ""crop_state_tables"" folder" |
| /results/yield_max_matrix.csv	                            | Matrix of max irrigated yields (kg C/ha), crop x state |
| /results/max_yield_kg.C.ha.csv	                          | Maximum yield in kg Carbon/hectare (kgC/ha) |
| /results/sust_yld_kg.C.ha_long.csv	                      | Yield corresponding to susytainable irrigation water in kgC/ha |
| /results/unsust_yld_kg.C.ha_ long.csv	                    | Yield corresponding to unsustainable irrigation water in kgC/ha |
| /results/crop_state_tables/[state]_[crop]_all_models.csv	| Per iteration output for all crops for all models |

---

File Name: irr_def_map.R	

This script creates irrigation deficit maps. 	

Creates output folder: figures/irr_def_maps_by_crop

test image, tell me what you think:

![image](https://github.com/user-attachments/assets/24c4cab9-0bab-4005-9b49-38df6fb0c3e3)

---

File name: gcamland_plots.R	

This script creates plots for the GCAM change in land. 	

Creates output folder: figures/gcam_delta_land

---

File name: DNDCe_yield_def_figures.R	

This script creates plots of crop yield deficits.  	

Creates output folder: figures/DNDCe_yield_def

---

File name: WBM_irrigation_analysis.R	

This script creates plots of grid-scale unsustainable irrigation fraction.	

Creates output folder: /figures/WBM_irrigation_maps

---

File name: Yield_irr_def_plot.R	

This script creates a plot of sustainable irrigation fraction versus fraction of maximum yield.	

---

ag_bar_chart.R:	

This script creates a stacked bar chart displaying the economic value of agricuture output for three crops across the western region.

---


