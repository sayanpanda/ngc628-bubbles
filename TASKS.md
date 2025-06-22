# Tasks

## Milestone 0: Basics
1. Use Jupyter Notebook
2. Adhere to PEP-8
3. Generate a README.md file and write the workings of the code in details there. Keep it updated as you implement each milestone.
4. Also keep a copilot_log.txt file keeping the history of the prompts there. 


## Milestone 1: Modifying and Updating Bubbles Data File
1. read the jwst_bubble_properties_A.csv file using astropy tables.
2. create new column RA_DEG and DEC_DEG
2. Convert RA_DMS and DEC_DMS to degree from sexagesimal (dms) using SkyCoord from astropy.coordinates and put those values in RA_DEG and DEC_DEG
3. The Columns SEMI_MAJ and SEMI_MIN are in pc. The distance of the galaxy is taken to be 9.84 Mpc for calculation. create new columns SEMI_MAJ_ARCSEC and SEMI_MIN_ARCSEC. Calculate the values. The pixel scale is 0.11 arc sec/pix

## Milestone 2: Displaying the bubbles as overlays over JWST Fits file.
* Pixel scale of JWST MIRI is 0.111"/pixel
* Postition Angle of each bubble is given in the PA_DEG column of the jwst_bubble_properties_A_updated.csv file. The length of the semimajor axis and semiminor axis in arc sec is also in that file under the column SEMI_MAJ_ARCSEC,SEMI_MIN_ARCSEC.

1. Use astropy.io.fits to load the jw01783-o908_t016_miri_f770w_i2d.fits file
2. Use astropy.wcs.WCS to convert RA/DEC to pixel xoordinates
3. use matplotlib.pyplot and matplotlib.patches.Ellipse to plot the fits file and draw ellipses as overlay over the fits file.

## Milestone 3: Output a .reg file of the overlay

Here is a example .reg file

```
# Region file format: DS9 version 4.1
icrs
ellipse(150.116321, 2.205830, 10", 5", 0)

```

150.116321 = RA in degrees

2.205830 = DEC in degrees

10" = semi-major axis (arcsec)

5" = semi-minor axis (arcsec)

0 = position angle (degrees, from North toward East)

Use this as a reference to generate a .reg file of the bubble overlays. 




