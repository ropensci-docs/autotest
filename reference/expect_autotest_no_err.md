# expect_autotest_no_err

Expect
[`autotest_package()`](https://docs.ropensci.org/autotest/reference/autotest_package.md)
to be clear of errors

## Usage

``` r
expect_autotest_no_err(object)
```

## Arguments

- object:

  An `autotest` object to be tested

## Value

(invisibly) The same object

## See also

Other expectations:
[`expect_autotest_no_testdata()`](https://docs.ropensci.org/autotest/reference/expect_autotest_no_testdata.md),
[`expect_autotest_no_warn()`](https://docs.ropensci.org/autotest/reference/expect_autotest_no_warn.md),
[`expect_autotest_notes()`](https://docs.ropensci.org/autotest/reference/expect_autotest_notes.md),
[`expect_autotest_testdata()`](https://docs.ropensci.org/autotest/reference/expect_autotest_testdata.md)

## Examples

``` r
# \donttest{
x <- autotest_package (package = "stats", functions = "cov", test = TRUE)
#> Error in cov(swM, use = "all") : missing observations in cov/cor
#> Testing functions ■■■■                              10% | ETA: 12s
#> Testing functions ■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■  100% | ETA:  0s
testthat::expect_failure (expect_autotest_no_err (x))
# }
```
