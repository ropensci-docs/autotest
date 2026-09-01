# expect_autotest_testdata

Expect
[`autotest_package()`](https://docs.ropensci.org/autotest/reference/autotest_package.md)
to be clear of errors with some tests switched off, and to have note
column explaining why those tests are not run.

## Usage

``` r
expect_autotest_testdata(object)
```

## Arguments

- object:

  An `autotest_package` object with a `test` column flagging tests which
  are not to be run on the local package.

## Value

(invisibly) The autotest object

## See also

Other expectations:
[`expect_autotest_no_err()`](https://docs.ropensci.org/autotest/reference/expect_autotest_no_err.md),
[`expect_autotest_no_testdata()`](https://docs.ropensci.org/autotest/reference/expect_autotest_no_testdata.md),
[`expect_autotest_no_warn()`](https://docs.ropensci.org/autotest/reference/expect_autotest_no_warn.md),
[`expect_autotest_notes()`](https://docs.ropensci.org/autotest/reference/expect_autotest_notes.md)

## Examples

``` r
test_data <- autotest_types (notest = "vector_to_list_col")
if (FALSE) { # \dontrun{
# Called within a 'testthat' test file of the local package itself:
testthat::test_that ("autotest", {
    testthat::expect_success (expect_autotest_testdata (test_data))
})
} # }
```
