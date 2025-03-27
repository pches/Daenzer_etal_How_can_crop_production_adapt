# Daenzer_etal_How_can_crop_production_adapt
This repository contains all of the code necessary to reproduce the figures for the Supplemental Information document for the manuscript "How can crop production adapt to growing groundwater restrictions in the West?" authored by Daenzer, et al.

# Code for: How can crop production adapt to growing groundwater restrictions in the West? by Daenzer et al.

This code was developed by Pandara Valappil Femeena and Kathryn Daenzer.  

This repository contains all the code to regenerate the figures described in the associated supplemental information document for the paper, "How can crop production adapt to growing groundwater restrictions in the West?" 

Current paper citation:
Kathryn Daenzer, Pandara Valappil Femeena, Steve Frolking, Danielle Grogan, Jeff Nucciarone, Kate Calvin, Richard B. Lammers, Karen Fisher-Vanden

This supplemental information document and its associated paper are in preparation for submission; a full citation and link for both will be added here if it is accepted for publication.

The input data that is required for this repo's code can be found here:

TITLE data: (Author). Harmonized Database of Western U.S. Water Rights (HarDWR) (Version v1) [Data set]. MSD-LIVE Data Repository. https://doi.org/1x/x

Contact info: nucci@psu.edu (data curation), fpp5056@psu.edu (methods and methodologies)

## System requirements:
This code is written in standard R coding language. No special hardware or system requirements are necessary. The R code requires the use of the following libraries for processing:

- RColorBrewer
- data.table
- dplyr
- ggplot2
- ggspatial
- lattice
- maps
- ncdf4
- raster
- rgdal
- rgeos
- rnaturalearth
- sf
- sp
- tidyr

All processing was performed on a Red Hat Enterprise Linux 8 system but should be reproducible on a regular desktop computer.  


## Scripts:

The code provided here to reproduce the figures and tables in the paper requires the data available on MSD-Live at https://doi.org/. A description file available in this repo, in the form of a spreadsheet, lists the required input files for each script. The output file description lists each associated figure generated in the paper.

Here, we describe each dataset:

File name: script_and_file_description.xlsx

A Microsoft XL spreadsheet containing a list of all scripts along with their required input files and their description along with a listing of each output file and description for each script.

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

These summary files are used in the other scripts to create plots provided in the submitted manuscript (including the supplemental information).	

Output written to folders: results/ 

---

File Name: irr_def_map.R	

This script creates irrigation deficit maps. 	

Creates output folder: figures/irr_def_maps_by_crop

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

File Name: Table_1.csv; Description: All data in Table 1, reproducible from WBM output files using code table_1.R

Filename	Description	Notes


 	![image](https://github.com/user-attachments/assets/6c420bf6-0983-48b5-b4f5-f7a8e1e26562)

