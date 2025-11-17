
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
devtools::install_github("zoehorlick/assignmentb2")
#> Using GitHub PAT from the git credential store.
#> Downloading GitHub repo zoehorlick/assignmentb2@HEAD
#> 
#> ── R CMD build ─────────────────────────────────────────────────────────────────
#> * checking for file ‘/private/var/folders/ds/vvrsbdrj7d7bm_4nlgf3vtbh0000gn/T/RtmpnLONrI/remotes252c7c821eee/zoehorlick-assignmentb2-b67a1e4/DESCRIPTION’ ... OK
#> * preparing ‘assignmentb2’:
#> * checking DESCRIPTION meta-information ... OK
#> * checking for LF line-endings in source and make files and shell scripts
#> * checking for empty or unneeded directories
#>   NB: this package now depends on R (>= 4.1.0)
#>   WARNING: Added dependency on R >= 4.1.0 because package code uses the
#>   pipe |> or function shorthand \(...) syntax added in R 4.1.0.
#>   File(s) using such syntax:
#>     ‘count_all_missing_by_group.R’
#> * building ‘assignmentb2_0.0.0.9000.tar.gz’
#> Installing package into '/private/var/folders/ds/vvrsbdrj7d7bm_4nlgf3vtbh0000gn/T/Rtmpwse9hT/temp_libpath1def6874550e'
#> (as 'lib' is unspecified)
```

OR, you can use `pak`

``` r
# install.packages("pak")
pak::pak("zoehorlick/assignmentb2")
#> ℹ Loading metadata database
#> ✔ Loading metadata database ... done
#> 
#> 
#> → Will install 15 packages.
#> → All 15 packages (9.62 MB) are cached.
#> + cli          3.6.5  🔧
#> + dplyr        1.1.4  🔧
#> + generics     0.1.4  
#> + glue         1.8.0  🔧
#> + lifecycle    1.0.4  
#> + magrittr     2.0.4  🔧
#> + pillar       1.11.1 
#> + pkgconfig    2.0.3  
#> + R6           2.6.1  
#> + rlang        1.1.6  🔧
#> + tibble       3.3.0  🔧
#> + tidyselect   1.2.1  
#> + utf8         1.2.6  🔧
#> + vctrs        0.6.5  🔧
#> + withr        3.0.2
#> ℹ No downloads are needed, 15 pkgs (9.62 MB) are cached
#> ✔ Installed R6 2.6.1  (77ms)
#> ✔ Installed cli 3.6.5  (84ms)
#> ✔ Installed dplyr 1.1.4  (98ms)
#> ✔ Installed generics 0.1.4  (102ms)
#> ✔ Installed glue 1.8.0  (107ms)
#> ✔ Installed lifecycle 1.0.4  (111ms)
#> ✔ Installed magrittr 2.0.4  (147ms)
#> ✔ Installed pillar 1.11.1  (154ms)
#> ✔ Installed pkgconfig 2.0.3  (51ms)
#> ✔ Installed rlang 1.1.6  (37ms)
#> ✔ Installed tibble 3.3.0  (38ms)
#> ✔ Installed tidyselect 1.2.1  (36ms)
#> ✔ Installed utf8 1.2.6  (34ms)
#> ✔ Installed vctrs 0.6.5  (36ms)
#> ✔ Installed withr 3.0.2  (25ms)
#> ✔ 1 pkg + 15 deps: kept 1, added 15 [5.7s]
```

## Example

This is a basic example which shows you how to use the function
`count_all_missing_by_group()`

``` r
# This example outputs the number of missing values in the airquality dataset grouped by the cyl column
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

You can also use pipes:

``` r
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

If you want to keep the output grouped:

``` r
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

You’ll still need to render `README.Rmd` regularly, to keep `README.md`
up-to-date. `devtools::build_readme()` is handy for this.
