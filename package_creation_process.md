Instructions used to turn this repo into a package
================

## Create a package

``` r
usethis::create_package("ALRA")
```

    ✔ Setting active project to '/path/to/ALRA'
    ✔ Creating 'R/'
    ✔ Writing 'DESCRIPTION'
    Package: ALRA
    Title: What the Package Does (One Line, Title Case)
    Version: 0.0.0.9000
    Authors@R (parsed):
        * First Last <first.last@example.com> [aut, cre] (YOUR-ORCID-ID)
    Description: What the package does (one paragraph).
    License: `use_mit_license()`, `use_gpl3_license()` or friends to
        pick a license
    Encoding: UTF-8
    Roxygen: list(markdown = TRUE)
    RoxygenNote: 7.2.2
    ✔ Writing 'NAMESPACE'

## Add dependencies

``` r
# if you don't have rsvd installed first
# install.packages("rsvd")
usethis::use_package("rsvd")
```

✔ Adding ‘rsvd’ to Imports field in DESCRIPTION • Refer to functions
with `rsvd::fun()`

``` r
# if you don't have fastRPCA installed, follow the instructions at
# https://github.com/KlugerLab/rpca-mkl#r-package-installation

# add to dependencies
usethis::use_dev_package("fastRPCA", "Suggests", remote = "github::KlugerLab/rpca-mkl/fastRPCA")
```

✔ Adding ‘fastRPCA’ to Suggests field in DESCRIPTION ✔ Adding
‘github::KlugerLab/rpca-mkl/fastRPCA’ to Remotes field in DESCRIPTION

## Move the source files

``` r
fs::file_move(c("alra.R", "alraSeurat2.R"), "R")
```

## Download the example data files

``` r
b_nk_example <- readr::read_rds('https://gauss.math.yale.edu/~gcl22/alra/b_nk_example.RDS')
usethis::use_data(b_nk_example)
```

    ✔ Adding 'R' to Depends field in DESCRIPTION
    ✔ Setting LazyData to 'true' in 'DESCRIPTION'
    ✔ Saving 'b_nk_example' to 'data/b_nk_example.rda'
    • Document your data (see 'https://r-pkgs.org/data.html')

``` r
labels_example <- readr::read_rds('https://gauss.math.yale.edu/~gcl22/alra/labels_example.RDS')
usethis::use_data(labels_example)
```

    > usethis::use_data(labels_example)
    ✔ Saving 'labels_example' to 'data/labels_example.rda'
    • Document your data (see 'https://r-pkgs.org/data.html')

## Create unit test

``` r
usethis::use_test("alra_test")
```

    ✔ Adding 'testthat' to Suggests field in DESCRIPTION
    ✔ Setting Config/testthat/edition field in DESCRIPTION to '3'
    ✔ Creating 'tests/testthat/'
    ✔ Writing 'tests/testthat.R'
    ✔ Writing 'tests/testthat/test-alra_test.R'
    • Modify 'tests/testthat/test-alra_test.R'