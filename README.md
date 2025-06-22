# Bubble Analysis in NGC628

This project analyzes bubble properties in the NGC628 galaxy using JWST data. The analysis is structured in milestones, each building on the previous one to create a comprehensive analysis of the bubble catalog.

## Project Structure

- `bubble_analysis.ipynb`: Main Jupyter notebook containing all analysis code
- `jwst_bubble_properties_A.csv`: Original bubble catalog data
- `jwst_bubble_properties_A_updated.csv`: Modified bubble catalog with additional columns
- `TASKS.md`: List of milestones and tasks for the project
- `README.md`: This file, providing an overview of the project
- `copilot_log.txt`: Log of prompts and responses from GitHub Copilot

## Implementation Details

### Milestone 0: Basics
- Using Jupyter Notebook for all analysis
- Following PEP-8 style guidelines
- Documentation in README.md and code comments
- Maintaining a prompt history in copilot_log.txt

### Milestone 1: Modifying and Updating Bubbles Data File
- Reading data from `jwst_bubble_properties_A.csv` using Astropy Tables
- Converting coordinates from sexagesimal (DMS) to degrees
- Adding new columns:
  - `RA_DEG`: Right ascension in degrees
  - `DEC_DEG`: Declination in degrees
  - `SEMI_MAJ_ARCSEC`: Semi-major axis in arcseconds
  - `SEMI_MIN_ARCSEC`: Semi-minor axis in arcseconds

#### Coordinate Conversion
The original RA_DMS and DEC_DMS coordinates are in degrees, minutes, seconds format. We use Astropy's SkyCoord to convert these to decimal degrees for easier mathematical operations.

#### Size Conversion
The bubble sizes (semi-major and semi-minor axes) are given in parsecs. To convert to angular sizes in arcseconds, we use:
- Distance to NGC628: 9.84 Mpc
- Small angle approximation: angle (rad) = size / distance
- Convert to arcseconds: angle (arcsec) = angle (rad) * 206265

### Milestone 2: Displaying Bubbles as Overlays on JWST FITS Files
- Loading FITS files using `astropy.io.fits`
- Converting celestial coordinates to pixel coordinates using `astropy.wcs.WCS`
- Visualizing the bubbles as elliptical overlays on the JWST image using `matplotlib`
- Adding bubble IDs as labels for easier identification

### Milestone 3: Generating DS9 Region Files
- Creating DS9-compatible region files for visualizing bubbles in external astronomy software
- Format: `ellipse(RA, DEC, SEMI_MAJ", SEMI_MIN", PA)`
- Generated files:
  - `ngc628_all_bubbles.reg`: Contains all 1694 bubbles
  - `top_15_bubbles.reg`: Contains only the 15 largest bubbles
- Also created a visualization focusing on the top 15 largest bubbles
- Saved data for the top 15 largest bubbles in `top_15_largest_bubbles.csv`

## Data Description

The bubble catalog contains:
- Positions in sexagesimal coordinates (RA_DMS, DEC_DMS)
- Bubble sizes in parsecs (SEMI_MAJ_PC, SEMI_MIN_PC, AVG_RAD_PC)
- Position angle in degrees (PA_DEG)
- Which spiral arm the bubble is closest to (ARM)
- Distance to nearest arm (DIST_ARM_PC)
- Galactocentric distance (GAL_RAD_KPC)

## Usage

1. Ensure you have the required Python packages installed: astropy, numpy, matplotlib, jupyter
2. Open `bubble_analysis.ipynb` in Jupyter Notebook or JupyterLab
3. Run the cells in order to perform the analysis
