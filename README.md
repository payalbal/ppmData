
<!-- badges: start -->

[![R-CMD-check](https://github.com/skiptoniam/ppmData/workflows/R-CMD-check/badge.svg)](https://github.com/skiptoniam/ppmData/actions)
[![Coverage
Status](https://codecov.io/github/skiptoniam/ppmData/coverage.svg?branch=master)](https://codecov.io/github/skiptoniam/ppmData?branch=master)
<!-- badges: end -->

## ppmData is an R package that can be used to set up a quadrature scheme for spatial point processes modelling and could be used in [ecomix](https://github.com/skiptoniam/ecomix) to run multiple species Point Processes.

The approach uses quasi-random sampling (Grafston & Tille, 2013, Foster
et al., 2018) to generate a quadrature scheme for numerical
approximation of a Poisson point process model (Berman & Turner 1992;
Warton & Shepard 2010). Quasi-random sampling quadrature are form of
spatially-balanced survey design or point stratification that aims to
reduce the frequency of placing samples close to each other (relative to
pseudo-random or grid designs). A quasi-random quadrature design
improves efficiency of background point sampling (and subsequent
modelling) by reducing the amount of spatial auto-correlation between
data implying that each sample is providing as much unique information
as possible (Grafston & Tille, 2013, Foster et al., 2018) and thus
reducing low errors for geostatistical prediction (Diggle & Ribeiro,
2007). Because the quasi-random design is not on a regular grid we use
Dirichlet tessellation to generate polygons for each point in the
quadrature scheme. Areal weights are then derived from these polygons.

We note that this approach is different to a targeted background scheme
for generating pseudo-absences. If the users intent is to reduce
sighting biases via a targeted background scheme, we recommend that bias
is accounted for via covariates (distance to roads) or an offset (a
known amount of effort) (e.g Warton et al., 2013; Renner et al, 2015).

### References

Diggle, P. J., P. J. Ribeiro, *Model-based Geostatistics*. Springer
Series in Statistics. Springer, 2007.

Foster, S.D., Monk, J., Lawrence, E., Hayes, K.R., Hosack, G.R. and
Przeslawski, R., 2018. *Statistical considerations for monitoring and
sampling.* Field manuals for marine sampling to monitor Australian
waters, pp.23-41.

Grafstrom, Anton, and Yves Tille. *Doubly balanced spatial sampling with
spreading and restitution of auxiliary totals.* Environmetrics 24.2
(2013): 120-131.

Renner, I.W., Elith, J., Baddeley, A., Fithian, W., Hastie, T.,
Phillips, S.J., Popovic, G. and Warton, D.I., 2015. *Point process
models for presence only analysis.* Methods in Ecology and Evolution,
6(4), p.366-379.

Warton, D. I., and L. C. Shepherd. *Poisson point process models solve
the pseudo-absence problem for presence-only data in ecology.* The
Annals of Applied Statistics 4.3 (2010): 1383-1402.

Warton, D.I., Renner, I.W. and Ramp, D., 2013. *Model-based control of
observer bias for the analysis of presence-only data in ecology.* PloS
one, 8(11), p.e79168.
