
<!-- README.md is generated from README.Rmd. Please edit that file -->

# assignmentb2

<!-- badges: start -->

<!-- badges: end -->

The goal of **assignmentb2** is to demonstrate how to wrap and document
a function in an R package. This package uses the pre-baked function
`count_all_missing_by_group()` provided by the STAT 545 instructional
team. The function counts the missing values in a dataset and is grouped
by a chosen variable.

## Installation

You can install the development version of assignmentb2 from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("zoehorlick/assignmentb2", ref = "v0.1.3")
```

## Examples

Here are three examples which show you how to use the function
`count_all_missing_by_group()`

``` r
# Example 1: This example computes the number of missing values in the `airquality` dataset grouped by the `cyl` column. 

library(assignmentb2)
count_all_missing_by_group(airquality, Month)
#> # A tibble: 5 × 6
#>   Month Ozone Solar.R  Wind  Temp   Day
#>   <int> <int>   <int> <int> <int> <int>
#> 1     5     5       4     0     0     0
#> 2     6    21       0     0     0     0
#> 3     7     5       0     0     0     0
#> 4     8     5       3     0     0     0
#> 5     9     1       0     0     0     0
```

``` r
# Example 2: This example has the same output as the last example, but shows off an alternative way of invoking the `count_all_missing_by_group()`: piping the dataset into the function. 
airquality |>
  count_all_missing_by_group(Month)
#> # A tibble: 5 × 6
#>   Month Ozone Solar.R  Wind  Temp   Day
#>   <int> <int>   <int> <int> <int> <int>
#> 1     5     5       4     0     0     0
#> 2     6    21       0     0     0     0
#> 3     7     5       0     0     0     0
#> 4     8     5       3     0     0     0
#> 5     9     1       0     0     0     0
```

``` r
# Example 3: The optional `.groups` argument allows us to keep the output grouped by the grouping column. 
count_all_missing_by_group(airquality, Month, .groups = "keep")
#> # A tibble: 5 × 6
#> # Groups:   Month [5]
#>   Month Ozone Solar.R  Wind  Temp   Day
#>   <int> <int>   <int> <int> <int> <int>
#> 1     5     5       4     0     0     0
#> 2     6    21       0     0     0     0
#> 3     7     5       0     0     0     0
#> 4     8     5       3     0     0     0
#> 5     9     1       0     0     0     0
```
