
# BayesDC: the Bayesian method for estimating the degree of the dosage compensation on X chromosome

<!-- badges: start -->
<!-- badges: end -->

The goal of BayesDC is to estimate the degree of dosage compensation at X-linked loci.

## Installation

You can install the development version of BayesDC like so:

``` r
if(!require(remotes)){
   install.packages("remotes")
}
remotes::install_github("joyswhale/BayesDC")
```

## Example

This is a basic example which shows you how to estimate the degree of dosage compensation at X-linked loci using example data:

``` r
library(BayesDC)
data("ped1")
data("covar")
library("rstan")
options(mc.cores = parallel::detectCores())
rstan_options(auto_write = TRUE)

##example 1: quantitative trait with covariate and the prior distribution of d is a truncated normal distribution specified in our paper
set.seed(123)
BayesDC(ped1,covariate=covar,trait_type = "quantitative",
        trait_missing=NA,genotype_missing=NA,covariate_missing=NA,
        prior = "normal",chains_num=8,iter_num=1000,warmup_num=500,acceptance_rate=0.99)
```
