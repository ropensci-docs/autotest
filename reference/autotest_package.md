# autotest_package

Automatically test an entire package by tracing calls made in its
documented examples (and, for local source packages, its test suite)
with typetracer, then testing each traced function call in turn.

## Usage

``` r
autotest_package(
  package = ".",
  functions = NULL,
  exclude = NULL,
  test = FALSE,
  test_data = NULL,
  progress = c("bar", "tests", "none")
)
```

## Arguments

- package:

  Name of package, as either

  1.  Path to local package source

  2.  Name of installed package

  3.  Full path to location of installed package if not on
      [.libPaths](https://rdrr.io/r/base/libPaths.html), or

  4.  Default which presumes current directory is within package to be
      tested.

- functions:

  Optional character vector containing names of functions of nominated
  package to be included in 'autotesting'.

- exclude:

  Optional character vector containing names of any functions of
  nominated package to be excluded from 'autotesting'.

- test:

  If `FALSE`, return only descriptions of tests which would be run with
  `test = TRUE`, without actually running them.

- test_data:

  Result returned from calling either
  [autotest_types](https://docs.ropensci.org/autotest/reference/autotest_types.md)
  or autotest_package with `test = FALSE` that contains a list of all
  tests which would be conducted. These tests have an additional flag,
  `test`, which defaults to `TRUE`. Setting any tests to `FALSE` will
  avoid running them when `test = TRUE`.

- progress:

  Style of progress display while testing functions, one of:

  - `"bar"` (default) A `cli` progress bar. Automatically falls back to
    `"none"` when called from within a `knitr` document, to avoid
    literal ANSI escape sequences leaking into the rendered output.

  - `"tests"` One line per function tested, showing `[i / n]`.

  - `"none"` No progress display at all.

## Value

An `autotest_package` object which is derived from a tibble `tbl_df`
object. This has one row for each test, and the following eight columns:

1.  `type` The type of result, either "dummy" for `test = FALSE`, or one
    of "error", "warning", "diagnostic", or "message".

2.  `test_name` Name of each test

3.  `fn_name` Name of function being tested

4.  `parameter` Name of parameter being tested

5.  `parameter_type` Expected type of parameter as identified by
    `autotest`.

6.  `operation` Description of the test

7.  `content` For `test = FALSE`, the expected behaviour of the test;
    for `test = TRUE`, the observed discrepancy with that expected
    behaviour

8.  `test` If `FALSE` (default), list all tests without implementing
    them, otherwise implement all tests.

Some columns may contain NA values, as explained in the Note.

## Note

Some columns may contain NA values, including:

- `parameer` and `parameter_type`, for tests applied to entire
  functions, such as tests of return values.

- `test_name` for warnings or errors generated through "normal" function
  calls generated directly from example code, in which case `type` will
  be "warning" or "error", and `content` will contain the content of the
  corresponding message.

## See also

Other main_functions:
[`autotest_types()`](https://docs.ropensci.org/autotest/reference/autotest_types.md)

## Examples

``` r
# \donttest{
x <- autotest_package (package = "stats", functions = "var", test = FALSE)
#> namespace 'stats' is already loaded so argument 'keep.source' will be ignored.
#> Error in cov(swM, use = "all") : missing observations in cov/cor
#> R^2 = 0.21
#> Loading required namespace: testthat
x
#> # A tibble: 21 × 8
#>    type    test_name    fn_name parameter parameter_type operation content test 
#>    <chr>   <chr>        <chr>   <chr>     <chr>          <chr>     <chr>   <lgl>
#>  1 warning par_is_demo… var     na.rm     NA             Check th… Exampl… TRUE 
#>  2 warning par_is_demo… var     use       NA             Check th… Exampl… TRUE 
#>  3 dummy   int_as_nume… var     x         integer vector Integer … (Shoul… TRUE 
#>  4 dummy   vector_to_l… var     x         vector         Convert … (Shoul… TRUE 
#>  5 dummy   negate_logi… var     na.rm     single logical Negate d… (Funct… TRUE 
#>  6 dummy   subst_int_f… var     na.rm     single logical Substitu… (Funct… TRUE 
#>  7 dummy   subst_char_… var     na.rm     single logical Substitu… should… TRUE 
#>  8 dummy   single_par_… var     na.rm     single logical Length 2… Should… TRUE 
#>  9 dummy   return_succ… var     (return … (return objec… Check th… NA      TRUE 
#> 10 dummy   return_val_… var     (return … (return objec… Check th… NA      TRUE 
#> # ℹ 11 more rows
# }
```
