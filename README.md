qrbp is an r package for generating quasi random background points for Poisson point process models.
----------------------------------------------------------------------------------------------------

The package aims to generate background points that...

``` r
devtools::install_github('skiptoniam/qrbp')
```

There are two main functions in the `qrbp` package, the first and main function can be used to generate `n` quasirandom background points within a spatial domain. The for background points can be used in Poisson point process modelling in R. The main function is , which takes some coordinates, an area of interest and covariates (and other parameters) and produces a dataset. It is essentially a wrapper around the (excellent and existing) function in the MBHdesign package which alreay implements quasi-random sampling within a basic domain.

Here is an example using a set of spatial points and a raster. In this example we use the location of the existing sample sites to help generate a new set of back ground points based on an underlying probabiltiy of sampling intenstiy. The probablity of estimating the probabilty of presence from a series of spatial points. The probability of *absence in an area of size A* according to the poisson distribution is:

*p**r*(*y* = 0)=*e**x**p*(−*λ*(*u*)\**A*)

The prob of *presence* is then:

*p**r*(*y* = 1)=1 − *p**r*(*y* = 0) =1 − *e**x**p*(−*λ*(*u*)\**A*)

where *λ*(*u*) = the intensity value at point *u* and *A* is the area of the sampling unit (cell size). $\\lammbda$ is estimated using `density.ppp` from the spatstat package and then converted into a `inclusion.prob` to inform quasi-random background point selection.

Generate some random points and a raster to represent study area.

``` r
library(raster)
```

    ## Loading required package: sp

``` r
N <- 100
ks <- as.data.frame(cbind(x1=runif(N, min=-10, max=10),x2=runif(N, min=-10, max=10)))
sa <- raster(nrows=100, ncols=100, xmn=-10, xmx=10,ymn=-10,ymx=10)
sa[]<-rnorm(10000)
projection(sa) <- "+proj=longlat +datum=WGS84 +ellps=WGS84 +towgs84=0,0,0"
plot(sa)
points(ks$x1,ks$x2,pch=16,add=TRUE)
```

    ## Warning in plot.xy(xy.coords(x, y), type = type, ...): "add" is not a
    ## graphical parameter

![](readme_files/figure-markdown_github/unnamed-chunk-1-1.png)

How many qausiRandom background points do we need?

``` r
library(qrbp)
set.seed(123)
n <- 200
bkpts <- qrbp(n,dimension = 2,known.sites=ks,include.known.sites=TRUE,
              study.area = sa,inclusion.probs = NULL,sigma=1,plot.prbs=TRUE)
```

    ## No study.area defined. Using an interval/rectangle/hyper-rectangle based on the extreme locations in potential.sites

    ## Number of samples considered (number of samples found): 2000(0)

    ## Finished

![](readme_files/figure-markdown_github/unnamed-chunk-2-1.png)
