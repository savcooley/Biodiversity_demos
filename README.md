# Biodiversity_demos

# ARSET | Assessing Biodiversity Using Forest Structure from Spaceborne Lidar
## Part 2 – Demo 2: Comparing Forest Structure Across the BDFFP Landscape with GEDI

**Goal:** Derive GEDI forest-structure metrics for the Biological Dynamics of Forest Fragments Project (BDFFP), north of Manaus, Brazil. Then map vertical structural complexity and compare forest fragments, secondary forest and continuous mature forest.

**Tools:** Python (`earthaccess`, `h5py`, `numpy`, `pandas`, `geopandas`, `scipy`, `matplotlib`) in Google Colab

**Data products:** GEDI L2A (relative height metrics) and GEDI L2B (canopy cover, Plant Area Index (PAI), Foliage Height Diversity (FHD), Plant Area Volume Density (PAVD) profiles). Optional: GEDI L4A aboveground biomass density.

**Data inputs:** GEDI L2A/L2B (NASA LP DAAC, requires a free Earthdata Login) and the 2022 camera-trap and AudioMoth locations from Luther et al. (2026), `BDFFP_TERRESTRIALCameraARD2022_unit_locations.xlsx`

**What you will do**
1. Load the biodiversity sampling units (camera traps + acoustic recorders) and map the study design
2. Search and stream GEDI L2A/L2B footprints over the BDFFP study area, and apply quality filtering
3. Calculate footprint metrics: canopy height, PAI, FHD (and recompute FHD from the PAVD profile), number of canopy layers, overstory/understory ratios
4. Calculate **height diversity** across the landscape and generate **vertical structure complexity maps**
5. Compare structure across forest types and export a site table for Demo 3

> **Presenter note:** Downloading/streaming GEDI granules can take 20–60 minutes, depending on the date range. Run Sections 1–4 before the live session with `SAVE_CACHE = True`. During the live demo, run with `USE_CACHE = True` so the notebook starts from the saved footprint table.

## Part 2 – Demo 3: Linking GEDI Forest Structure with Bird and Mammal Diversity
**Goal:** Reproduce the core analysis of Luther et al. (2026), Satellite-based forest structure metrics as a predictive tool for biodiversity in hyperdiverse tropical forests (Environmental and Sustainability Indicators 30: 101212). We test whether GEDI forest structure predicts bird and mammal occupancy at the Biological Dynamics of Forest Fragments Project (BDFFP), then interpret the model diagnostics and outputs.

**Tools:** Python (pymc + numpyro for Bayesian models, statsmodels, pandas, matplotlib) in Google Colab

**Data:**  (Luther et al. 2026, shared by D. Luther):

Daily detection/non-detection of 184 species from 31 AudioMoth recorders and 41 species from 73 camera traps (June–October 2022)
GEDI forest-structure metrics for the 18 sampling units with GEDI coverage (unit means of quality-filtered footprints, as produced in Demo 2)
Acoustic space use (ASU) and observed species richness per sampling unit

**What you will do:** 
1. Load the in situ detection data and the site-level GEDI metrics
2. Check collinearity among GEDI metrics (why each metric gets its own model)
3. Quick look: does the soundscape (ASU) track species richness and forest structure?
4 Fit the integrated community occupancy model that combines audio and camera detections
5 Rank 12 GEDI predictors plus a null model with WAIC
6 Interpret community and species-level responses to FHD, and compare forest types

About the code: The original analysis was run in R with spOccupancy::intMsPGOcc() (scripts shared by the authors). This notebook re-implements the same model structure in Python with PyMC, so participants do not need R. Priors and the sampler differ from spOccupancy, so numbers will be close to, but not identical with, the published values.
