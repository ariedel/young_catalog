# young_catalog 

Contains:

young.master.2015.0512 is the version used for the initial journal submission of LACEwING (3955 objects, 351 columns)

young.master.2015.0801 has new parallaxes from Erini Lambrides. (3956 objects, 350 columns)

young.master.2015.1216 has eight new papers of data, cleaned up X-ray and UV data, revised lithium selection, and APASS DR9 for BVg'r'i' photometry. (5200 objects, 379 columns)

young.master.2015.1229 has renamed headers to better conform to AAS Journal standards. Several unused and redundant columns have been removed. All stars now have names (finally) and a generally better set of GJ, HD, HR, and DM (BD/SD/CD/CPD) names. There has been further data cleanup, and joint photometry flags are now more consistently applied. Five duplicate entries have been removed. (5195 objects, 358 columns)

young.master.2016.0116 has headers that ACTUALLY conform to AAS Journal standards. Several less-important or empty columns were removed for the journal's machine-readable table. (5195 objects, 358 columns for ODS, XLSX, CSV)

young.master.2016.0704 adds several more papers (mostly Castor and the classic Eggen moving groups) plus Gontcharov et al. (2006) for RVs. (5350 objects, 388 columns for ODS, CSV, XLSX) The expansion in columns is entirely due to requiring more space to hold more instances of existing data (ex. there are now 8 blocks of RV columns) and not to any new kinds of data.

young.master.2016.1011 is a cleaned-up version of the 0704 version. 5350 objects, 388 columns for ODS, CSV, XLSX; 360 columns for the AAS-formatted machine-readable table)

This is the Catalog of Suspected Young Stars from Riedel et al. (2016) (at time of paper submission).

The catalog is meant to contain astrometric, photometric, and basic spectroscopic information for all stars EVER reported as being young (and nearby, with a rough outer limit of 100 parsecs plus the Pleiades and stars in the Octans moving group (both extend beyond 100 parsecs) plus field stars included in papers presenting young stars, or considered and rejected in those papers. Basically, if the star's youth was ever under consideration, this catalog should have it.

The catalog currently contains 5350 stars, in a one-line-per-star format, with 392 columns. Every quantity has an associated reference, nearly all quantities have uncertainties, and most quantities have upper limit/lower limit/joint/deblended flags. The master file is actually an OpenDocument (.ods) spreadsheet which has the following improvements over the .csv file:
* Color-coded sections
* In-sheet calculations for derived quantities like Mean RV, Mean Parallax, and most photometric colors.
* Properties of companions that were simply copied from the primary star are in bold. For instance, if all that's known is that the star is a binary, EVERYTHING should be bolded. The procedure upon discovering a companion is to copy the entire primary star's line and bold it, and then replace those values with the ones specific to the secondary.
* Note that the OpenDocument and Excel files have two extra header lines as compared to the CSV

The .csv file is probably easier to read into a program. Code for using Python 2.7+ and Astropy 0.4+ to produce a Python table is below:

from astropy.io import ascii

catalog = ascii.read(infilename)


Buyer beware: This is a work in progress. There is missing data (no lithium data for The Pleiades yet; I haven't added the papers; nearly no Hyades at all because I haven't added the papers yet). Multiplicity is incomplete. The Bold/Unbolded method of dealing with multiples is not consistently applied, and I intend to supplant it with flags on every data value.

Comments and suggestions are welcome.
