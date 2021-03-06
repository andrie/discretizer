
<!-- README.md is generated from README.Rmd. Please edit that file -->

# discretizer

<!-- badges: start -->

<!-- badges: end -->

The goal of discretizer is to discretize data in a data frame (x and y)
to a matrix for fast visualizationn

## Installation

You can install the development version from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("andrie/discretizer")
```

## Example

To illustrate discretization, create a strange attractor with 10 million
points, and the plot:

(This takes \~10 on my laptop.)

``` r
library(magrittr)
library(discretizer)
par(mar = rep(0, 4), mai = rep(0, 4))

c(-0.8, 0.4, -1.1, 0.5, -0.6, -0.1, -0.5, 0.8, 1.0, -0.3, -0.6, -0.3, -1.2, -0.3) %>% 
  strange_attractor(1e7, 1, 1) %>% 
  trim_quantiles(q = 0.05) %>% 
  discretize() %>% 
  log1p() %>% 
  recolour("BuPu") %>% 
  plot()
```

<img src="man/figures/README-example-1.png" width="100%" />
