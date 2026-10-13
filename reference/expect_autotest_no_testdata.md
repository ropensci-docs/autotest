# expect_autotest_no_testdata

Expect
[`autotest_package()`](https://docs.ropensci.org/autotest/reference/autotest_package.md)
to be clear of errors with no tests switched off

## Usage

``` r
expect_autotest_no_testdata(object = NULL)
```

## Arguments

- object:

  Not used here, but required for `testthat` expectations

## Value

(invisibly) The autotest object

## See also

Other expectations:
[`expect_autotest_no_err()`](https://docs.ropensci.org/autotest/reference/expect_autotest_no_err.md),
[`expect_autotest_no_warn()`](https://docs.ropensci.org/autotest/reference/expect_autotest_no_warn.md),
[`expect_autotest_notes()`](https://docs.ropensci.org/autotest/reference/expect_autotest_notes.md),
[`expect_autotest_testdata()`](https://docs.ropensci.org/autotest/reference/expect_autotest_testdata.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# Called within a 'testthat' test file of the local package itself:
testthat::test_that ("autotest", {
    testthat::expect_success (expect_autotest_no_testdata ())
})
} # }
```
