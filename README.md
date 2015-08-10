# young_catalog 

This is the Catalog of Suspected Young Stars from Riedel et al. (2015) (at time of paper submission).

The catalog is meant to contain astrometric, photometric, and basic spectroscopic information for all stars EVER reported as being young (and nearby, with a rough outer limit of 100 parsecs plus the Pleiades and stars in the Octans moving group (both extend beyond 100 parsecs) plus field stars included in papers presenting young stars, or considered and rejected in those papers. Basically, if the star's youth was ever under consideration, this catalog should have it.

The catalog currently contains 3955 stars, in a one-line-per-star format, with 351 columns. Every quantity has an associated reference, nearly all quantities have uncertainties, and most quantities have upper limit/lower limit/joint/deblended flags. The master file is actually an OpenDocument (.ods) spreadsheet which has the following improvements over the .csv file:
* Color-coded sections
* In-sheet calculations for derived quantities like Mean RV, Mean Parallax, and most photometric colors.
* Properties of companions that were simply copied from the primary star are in bold. For instance, if all that's known is that the star is a binary, EVERYTHING should be bolded. The procedure upon discovering a companion is to copy the entire primary star's line and bold it, and then replace those values with the ones specific to the secondary.

The .csv file is probably easier to read into a program. Code for using Python 2.7+ and Astropy 0.4+ to produce a Python table is below:

from astropy.io import ascii

file = open(infilename,'rb')
readtable = ascii.get_reader(Reader=ascii.Basic)
readtable.header.splitter.delimiter = ','
readtable.data.splitter.delimiter = ','
readtable.header.start_line = 1
readtable.data.start_line = 3
catalog = readtable.read(file)
file.close()

A simpler method might be to open the .csv file in a text editor, chop out the first (sections) and third (units) lines of the 3-line header. Reading would be easier:

from astropy.io import ascii

catalog = ascii.read(infilename)


Buyer beware: This is a work in progress. There is missing data (no lithium data for The Pleiades yet; I haven't added the papers; no Hyades at all because I haven't added the papers yet). Multiplicity is incomplete; I've only scanned and fixed coordinates and statistics for the first 4 hours of RA and the Bona-Fide stars, using the Washington Double Star catalog. The Bold/Unbolded method of dealing with multiples is not consistently applied, and I intend to supplant it with flags on every data value.

Comments and suggestions are welcome.
