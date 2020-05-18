# mashr: Multivariate Adaptive Shrinkage in R

[![Travis Build Status](https://travis-ci.org/stephenslab/mashr.svg?branch=master)](https://travis-ci.org/stephenslab/mashr)
[![codecov](https://codecov.io/gh/stephenslab/mashr/branch/master/graph/badge.svg)](https://codecov.io/gh/stephenslab/mashr)

This package implements methods to estimate and test many effects in
many conditions (or many effects on many outcomes).

Empirical Bayes methods are used to estimate patterns of similarity
among conditions, then exploit these patterns of similarity among
conditions to improve accuracy of effect estimates. See
[Urbut et al][mash-paper] for details.

**Note:** the R package used to generate the results for the manuscript
is [here][mashr-pkg-for-paper].

## Quick Start

1. Follow the setup instructions below.

2. See the [introductory vignette][vignette-intro] for an
introduction to mashr.

3. Then walk through these vignettes to learn more about mashr:
[Introduction to mash: data-driven covariances][vignette-data-driven-cov]
and [Simulation with non-canonical matrices][vignette-non-canonical].

## Citing this work

If you find the masr package or any of the source code in this
repository useful for your work, please cite:

> Sarah Urbut, Gao Wang, Peter Carbonetto and Matthew Stephens
> (2019). [Flexible statistical methods for estimating and testing effects in genomic studies with multiple conditions.][mash-paper]
> *Nature Genetics* **51**, 187-195.

## Setup

Please follow these steps to install mashr.

1. Unlike most packages available on CRAN, mashr is not precompiled,
   and therefore to install mashr you will need to make sure that your
   R installation is properly set up to compile packages with C++
   source; in particular, the C++ compiler programs supported by your
   version of R should be installed on your computer, and R should be
   correctly configured to call these compilers when installing
   packages from source. For more information, see the
   [CRAN documentation][cran-docs].
   
2. Install the [latest release][mashr-release] of the mashr package
   using [devtools][devtools]:

    ```R
    install.packages("devtools")
    devtools::install_github("stephenslab/mashr@v0.2-11")
    ```
   
   This command should automatically install any missing dependencies
   that are available from CRAN. This command should also
   automatically retrieve and install the latest version of the ashr
   package from Github. If it does not, you can install the ashr
   package separately using devtools:

   ```R
   devtools::install_github("stephens999/ashr")
   ```
   
3. By default, the `devtools::install_github` function does not build
   the vignettes. If you would like to build the vignettes as well,
   you will need to several additional packages, including
   [flashr][flashr], that are used only in the vignettes. This can
   also be done with devtools:

   ```R
   devtools::install_github("stephenslab/mashr@v0.2-11",dependencies = TRUE,
                            build_vignettes = TRUE)
   ```

## Developer notes

+ When any changes are made to `roxygen2` markup or the C++ code in
the src directory, run `devtools::document()` to update the
[RcppExports.cpp](src/RcppExports.cpp), the package namespaces (see
[NAMESPACE](NAMESPACE)), and the package documentation files (in the
"man" subdirectory),

+ These are the R commands to build the website (make sure you are
connected to Internet while running these commands):

   ```R
   library(pkgdown)
   build_site(mathjax = FALSE)
   ```

+ *Add notes here about modifications that need to be made prior to
  submitting the mashr package to CRAN.*

[mashr-pkg-for-paper]: http://github.com/stephenslab/mashr-paper
[cran-docs]: https://cran.r-project.org/manuals.html
[mash-paper]: https://doi.org/10.1038/s41588-018-0268-8
[mashr-release]: https://github.com/stephenslab/mashr/releases/tag/v0.2-11
[devtools]: https://github.com/r-lib/devtools
[flashr]: https://github.com/stephenslab/flashr
[vignette-intro]: https://stephenslab.github.io/mashr/articles/intro_mash.html
[vignette-data-driven-cov]: https://stephenslab.github.io/mashr/articles/intro_mash_dd.html
[vignette-non-canonical]: https://stephenslab.github.io/mashr/articles/simulate_noncanon.html
