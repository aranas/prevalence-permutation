# Permutation-based prevalence inference using the minimum statistic

This is an implementation for Matlab of the method proposed by Carsten
Allefeld, Kai Görgen and John-Dylan Haynes, 'Valid population inference
for information-based imaging: From the second-level *t*-test to
prevalence inference', [*NeuroImage*
2016](http://dx.doi.org/10.1016/j.neuroimage.2016.07.040). In that paper
the method was introduced as a way to perform population inference for
classification accuracy and other information-like measures and
called 'permutation-based *information* prevalence inference using the
minimum statistic'. Since it can equally well be applied to other
first-level summary statistics, the method is here generically referred
to as 'permutation-based prevalence inference using the minimum
statistic', or 'prevalence inference' for short.

The main user interface is given by the function:

    prevalence(ifn, P2, alpha, prefix)

It takes a two-dimensional cell array of image filenames as input, which
reference MR images of a given test statistic in several subjects (rows)
and under several first-level permutations (columns), where the 1st
column has to be based on the original (unpermuted) data. Results of
prevalence inference are written to several image files.
[SPM](http://www.fil.ion.ucl.ac.uk/spm/) functions are used to read and
write image files, which therefore has to be installed. Images can be
read in NIfTI and Analyze format as well as gzipped NIfTI, and are
written as NIfTI files.

To perform the actual analysis, `prevalence` calls the function:

    [results, params] = prevalenceCore(a, P2, alpha)

It can also be used directly, for input data that do not have the form
of image files. The function provides a simple graphical display of the
analysis results, which is updated while more second-level permutations
are generated. This function has no external dependencies.

For more information on input and output parameters, use
`help prevalence` and `help prevalenceCore` under Matlab.

The script `prevalenceTest` tests the implementation using smoothed
images of cross-validated classification accuracy, derived from the data
acquired by Cichy, Chen & Haynes (2011). See the subdirectory
`cichy-2011-category-smoothedaccuracy` for more information. The script
can also serve as an example of how to use `prevalence`.

This software was developed with SPM8 under Matlab R2015a, but later
versions should work, too. It is released under the terms of the GNU
General Public License, version 3 or later.

