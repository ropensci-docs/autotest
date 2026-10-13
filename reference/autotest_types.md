# autotest_types

List all types of 'autotests' currently implemented.

## Usage

``` r
autotest_types(notest = NULL)
```

## Arguments

- notest:

  Character string of names of tests which should be switched off by
  setting the `test` column to `FALSE`. Run this function first without
  this parameter to get all names, then re-run with this parameter
  switch specified tests off.

## Value

An `autotest` object with each row listing one unique type of test which
can be applied to every parameter (of the appropriate class) of each
function.

## See also

Other main_functions:
[`autotest_package()`](https://docs.ropensci.org/autotest/reference/autotest_package.md)

## Examples

``` r
x <- autotest_types ()
x
#> # A tibble: 27 × 8
#>    type  test_name      fn_name parameter parameter_type operation content test 
#>    <chr> <chr>          <chr>   <chr>     <chr>          <chr>     <chr>   <lgl>
#>  1 dummy rect_as_other  NA      NA        rectangular    Convert … "check… TRUE 
#>  2 dummy rect_compare_… NA      NA        rectangular    Convert … "expec… TRUE 
#>  3 dummy rect_compare_… NA      NA        rectangular    Convert … "expec… TRUE 
#>  4 dummy rect_compare_… NA      NA        rectangular    Convert … "expec… TRUE 
#>  5 dummy extend_rect_c… NA      NA        rectangular    Extend e… "(Shou… TRUE 
#>  6 dummy replace_rect_… NA      NA        rectangular    Replace … "(Shou… TRUE 
#>  7 dummy vector_to_lis… NA      NA        vector         Convert … "(Shou… TRUE 
#>  8 dummy vector_custom… NA      NA        vector         Custom c… "(Shou… TRUE 
#>  9 dummy double_is_int  NA      NA        numeric        Check wh… "int p… TRUE 
#> 10 dummy trivial_noise  NA      NA        numeric        Add triv… "(Shou… TRUE 
#> # ℹ 17 more rows
```
