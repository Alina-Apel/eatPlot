
<!-- README.md is generated from README.Rmd. Please edit that file -->

# eatPlot

<!-- badges: start -->

[![R-CMD-check](https://github.com/nickhaf/eatPlot/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/nickhaf/eatPlot/actions/workflows/R-CMD-check.yaml)
[![Codecov test
coverage](https://codecov.io/gh/nickhaf/eatPlot/branch/main/graph/badge.svg)](https://app.codecov.io/gh/nickhaf/eatPlot?branch=main)
<!-- badges: end -->

The goal of eatPlot is to easily plot results stemming from the eatRep
package.

## Installation

You can install the development version of eatPlot from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("nickhaf/eatPlot")
```

## Basic workflow

### Data preperation

`eatPlot` makes it simple to prepare `eatRep` output for plotting.
Depending on whether you want to plot cross-sectional data or trenddata,
you can use either:

``` r
library(eatPlot)
barplot_data <- prep_no_trend(
  data = adjusted_means,
  grouping_var = "adjust",
  columns = "adjust",
  competence = "GL",
  sig_niveau = 0.05
)
```

or:

``` r
lineplot_data <- prep_trend(data = trend_books, grouping_var = "KBuecher_imp3", competence = "GL", sig_niveau = 0.05)
```

### Plotting

The prepared data can then fed into one of the plotting functions. For
example, if you want to plot a barplot with an ajacent table, first plot
both plots indidually, and then merge them together:

``` r
p_table <- plot_table(barplot_data[["plot_table"]])
p_bar <- plot_bar(barplot_data)


plot_table_bar(p_table, p_bar)
```

<img src="man/figures/README-unnamed-chunk-4-1.png" width="100%" />
