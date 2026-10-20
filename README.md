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
