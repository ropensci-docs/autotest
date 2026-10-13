# expect_autotest_notes

Expect `test_data` param of `autotest_package` to have additional `note`
column explaining why tests have been switched off.

## Usage

``` r
expect_autotest_notes(object)
```

## Arguments

- object:

  An `autotest` object to be tested

## Value

(invisibly) The same object

## See also

Other expectations:
[`expect_autotest_no_err()`](https://docs.ropensci.org/autotest/reference/expect_autotest_no_err.md),
[`expect_autotest_no_testdata()`](https://docs.ropensci.org/autotest/reference/expect_autotest_no_testdata.md),
[`expect_autotest_no_warn()`](https://docs.ropensci.org/autotest/reference/expect_autotest_no_warn.md),
[`expect_autotest_testdata()`](https://docs.ropensci.org/autotest/reference/expect_autotest_testdata.md)

## Examples

``` r
# \donttest{
x <- autotest_package (package = "stats", functions = "cov", test = TRUE)
#> Error in cov(swM, use = "all") : missing observations in cov/cor
testthat::expect_success (expect_autotest_notes (x))
# }
```
