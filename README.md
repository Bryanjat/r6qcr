
<!-- README.md is generated from README.Rmd. Please edit that file -->

# r6qcr

<!-- badges: start -->
<!-- badges: end -->

La meta de r6qcr es poder realizar una clase madre con otros paquetes

## Installation

You can install the development version of r6qcr from
[GitHub](https://github.com/) with:

``` r
# install.packages("pak")
pak::pak("Bryanjat/r6qcr")
```

## Example

``` r
#### fdqcd (Functional data quality control) 

library(qcr)
#> Warning: package 'qcr' was built under R version 4.3.3
#> Loading required package: qcc
#> Warning: package 'qcc' was built under R version 4.3.3
#> Package 'qcc' version 2.7
#> Type 'citation("qcc")' for citing this R package in publications.
#> Loading required package: fda.usc
#> Loading required package: fda
#> Warning: package 'fda' was built under R version 4.3.3
#> Loading required package: splines
#> Loading required package: fds
#> Warning: package 'fds' was built under R version 4.3.3
#> Loading required package: rainbow
#> Warning: package 'rainbow' was built under R version 4.3.3
#> Loading required package: MASS
#> Loading required package: pcaPP
#> Warning: package 'pcaPP' was built under R version 4.3.3
#> Loading required package: RCurl
#> Warning: package 'RCurl' was built under R version 4.3.3
#> Loading required package: deSolve
#> Warning: package 'deSolve' was built under R version 4.3.3
#> 
#> Attaching package: 'fda'
#> The following object is masked from 'package:graphics':
#> 
#>     matplot
#> Loading required package: mgcv
#> Loading required package: nlme
#> Warning: package 'nlme' was built under R version 4.3.3
#> This is mgcv 1.9-0. For overview type 'help("mgcv-package")'.
#> Loading required package: knitr
#> Warning: package 'knitr' was built under R version 4.4.0
#>  fda.usc is running sequentially usign foreach package
#>  Please, execute ops.fda.usc() once to run in local parallel mode
#>  Deprecated functions: min.basis, min.np, anova.hetero, anova.onefactor, anova.RPm
#>  New functions: optim.basis, optim.np, fanova.hetero, fanova.onefactor, fanova.RPm
#> ----------------------------------------------------------------------------------
#> Loading required package: mvtnorm
#> Warning: package 'mvtnorm' was built under R version 4.4.0
#> 
#>  Package qcr: Quality Control Review 
#>  version 1.4 (built on 2022-02-15).
#>  Copyright Miguel A. Flores Sanchez 2016-2022.

m <- 30
tt<-seq(0,1,len=m) # Crea un vector de 0 1 partido en 30
mu<-30 * tt * (1 - tt)^(3/2) 
n0 <- 100
set.seed(12345) # Semilla
mdata<-matrix(NA,ncol=m,nrow=n0) # Crea una matriz de NA  de nxm
sigma <- exp(-3*as.matrix(dist(tt))/0.9)
for (i in 1:n0) mdata[i,]<- mu+0.5*mvrnorm(mu = mu,Sigma = sigma )
fdchart <- fdqcd(mdata)
plot(fdchart,type="l",col="red")
```

<img src="man/figures/README-unnamed-chunk-2-1.png" width="100%" />
