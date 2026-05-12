

Each of these notebooks perform some sort of operation to assist in the running of
`pszp.py' or in the post-processing of the photometry.

NOTE. None of these notebooks are meant to be fully automatic. They are intended to assist
with zeropoint-correcting Pan-STARRS photometry, but there are some manual steps in that
process. As such, a `plug-and-play' set of notebooks is not recommended as it provides the
user the ability to run with (potentially) erroneous outputs. These are designed such that
every step should be obvious and clear. If not, add a note to the GitHub where you feel
improvements could be made. This process should be easy to follow, and easy to undertake.

========


metadata.txt

This file contains the transient name, RA and Dec. This info is needed by multiple
notebooks, so makes most sense to define once in a file.

========


0-CMF_rearranger.ipynb

This notebook is used to re-order the CMFs (downloaded from the Pan-STARRS stamp server)
into some `pszp.py' friendly format. It requires some tweaking because the downloaded CMF
files can have varying directory structures; be sure to modify for your use case.

========


1-pszp_wrapper.ipynb

This notebook acts as a wrapper for repeated calls of `pszp.py'; i.e., it is the notebook
that actually runs the code to estimate zeropoint corrections for all CMF files.

========


2-applying_zero-points.ipynb

This notebook combines the newly computed zeropoint corrections with the forced photometry
data. Individual nightly exposures are co-added. Outputs (to a `Photometry' directory)
include .csv files with data grouped by MJD, and plots that compare the forced photometry
with the new zeropoint-corrected and co-added data.


========


3-collating_photometry.ipynb

This notebook combines all of the individual .csv files from before. Here we also compute
3- and 5-sigma upper limits where relevant; i.e., we only compute these if our detection
significance is less than 3- or 5-sigma.


========


4-formatting_photometry.ipynb

This notebook adds some extra info to our output photometry. It also generates some plots
to compare the `default' forced photometry with our new, finalised, co-added and
zeropoint-corrected photometry.

