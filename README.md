
<!-- README.md is generated from README.Rmd. Please edit that file -->

# ppcong <img src="man/figures/logo.png" width="160px" align="right" />

<!-- badges: start -->

[![Travis build
status](https://travis-ci.org/mkearney/ppcong.svg?branch=master)](https://travis-ci.org/mkearney/ppcong)
[![AppVeyor build
status](https://ci.appveyor.com/api/projects/status/github/mkearney/ppcong?branch=master&svg=true)](https://ci.appveyor.com/project/mkearney/ppcong)
[![Lifecycle:
experimental](https://img.shields.io/badge/lifecycle-experimental-orange.svg)](https://www.tidyverse.org/lifecycle/#experimental)
[![CRAN
status](https://www.r-pkg.org/badges/version/ppcong)](https://CRAN.R-project.org/package=ppcong)
[![Codecov test
coverage](https://codecov.io/gh/mkearney/ppcong/branch/master/graph/badge.svg)](https://codecov.io/gh/mkearney/ppcong?branch=master)
<!-- badges: end -->

A simple interface for interacting with [ProPublica’s Congress
API](https://projects.propublica.org/api-docs/congress-api/), which
provides data about current and former members of both chambers of the
U.S. Congress.

## Installation

You can install the released version of ppcong from
[CRAN](https://CRAN.R-project.org) with:

``` r
install.packages("ppcong")
```

And the development version from [GitHub](https://github.com/) with:

``` r
# install.packages("remotes")
remotes::install_github("mkearney/ppcong")
```

## Examples

Get “house” data from the “116”th Congress:

``` r
## get and preview house data from 116th congress
h116 <- ppc_members(congress = "116", chamber = "house")
h116
#> # A tibble: 0 x 0
```

Get “senate” data from the “110”th Congress:

``` r
## get and preview senate data from 110th congress
s110 <- ppc_members(congress = "110", chamber = "senate")
s110
#> # A tibble: 0 x 0
```

## API Key

Use of the [ProPublica
API](https://projects.propublica.org/api-docs/congress-api/) requires a
valid key, which you can obtain by completing the form found at the
following URL:
<https://www.propublica.org/datastore/api/propublica-congress-api>

Once you’ve obtained an API key, you can either include it in every
request, e.g.,

``` r
## include API key in request
s116 <- ppc_members(116, "senate", api_key = "as9d78f6aayd9fy2fq378a9ds876fsas89d7f")
```

Or for the duration of any given session, you can set the API key once
via the `ppc_api_key()` function

``` r
## set as environment variable for the remainder of current session
ppc_api_key("as9d78f6aayd9fy2fq378a9ds876fsas89d7f")
```

If you’d like to set the API key and store it for use in future
sessions, use `set_renv = TRUE`

``` r
## append as environment variable in user's home .Renviron file
ppc_api_key("as9d78f6aayd9fy2fq378a9ds876fsas89d7f", set_renv = TRUE)
```
