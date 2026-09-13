
<!-- README.md is generated from README.Rmd. Please edit that file -->

# **GLM.RMoE**: LASSO Regularized Mixture-of-Experts Models

<!-- badges: start -->

<!-- badges: end -->

`GLM.RMoE` is an R package for fitting regularized mixture-of-experts models with generalized linear experts. 

The package provides regularized Gaussian, multinomial, and Poisson mixture-of-experts models with LASSO-based feature
selection.

The package accompanies the paper:

*Regularized Estimation and Feature Selection in Mixtures of Generalized Linear Experts.* Ref: arXiv:1907.06994v2, September, 2026 by Thin Nguyen-Van, Faicel Chamroukhi, Ha Hoang Van and Bao Tuyen Huynh. Please cite the paper and the toolbox when using the
code.

This package has three main functions:

| Function         | Model         |
| ---------------- | ------------- |
| `GaussRMoE()`    | Gaussian RMoE |
| `LogisticRMoE()` | Multinomial RMoE |
| `PoissonRMoE()`  | Poisson RMoE  |

# Installation

Install package:

``` r
# install.packages("devtools")
devtools::install_github("nv-thin/GLM-RMoE")
```

Install with vignettes:

``` r
devtools::install_github(
  "nv-thin/GLM-RMoE",
  build_vignettes = TRUE,
  build_opts = c("--no-resave-data", "--no-manual")
)
```

Use the following command to display vignettes:

``` r
browseVignettes("GLM.RMoE")
```

# Main features

- Gaussian regularized mixture-of-experts
- Multinomial regularized mixture-of-experts
- Poisson regularized mixture-of-experts
- LASSO-based feature selection
- Proximal Newton optimization
- Proximal Newton-type optimization

# Usage

``` r
library(GLM.RMoE)
```

<details>

<summary>Gaussian Regularized Mixture-of-Experts</summary>

The following example fits a Gaussian RMoE model to a simulated dataset with two experts.

``` r
data("gaussian")

X <- as.matrix(gaussian[, -8])
y <- gaussian$V8

grmoe <- GaussRMoE(
  Xm = X,
  Ym = y,
  K = 2,
  Lambda = 5,
  Gamma = 5,
  option = FALSE # FALSE: proximal Newton; TRUE: proximal Newton-type
)

grmoe$plot()
```

The fitted model can be visualized using `plot()`.

<img src="man/figures/README-unnamed-chunk-6-1.png" style="display: block; margin: auto;" /><img src="man/figures/README-unnamed-chunk-6-2.png" style="display: block; margin: auto;" />

The following example fits a Gaussian RMoE model to a real dataset with two experts.

``` r

data("housing")

X <- as.matrix(housing[, -15])
y <- housing$V15

grmoe <- GaussRMoE(
  Xm = X,
  Ym = y,
  K = 2,
  Lambda = 42,
  Gamma = 10,
  option = FALSE # FALSE: proximal Newton; TRUE: proximal Newton-type
)

grmoe$plot()
```

The fitted model can be visualized using `plot()`.

<img src="man/figures/README-unnamed-chunk-7-1.png" style="display: block; margin: auto;" /><img src="man/figures/README-unnamed-chunk-7-2.png" style="display: block; margin: auto;" />

</details>

<details>

<summary>Multinomial Regularized Mixture-of-Experts</summary>

The following example fits a multinomial RMoE model to a simulated dataset with two experts.

``` r

data("logistic")

X <- as.matrix(logistic[, -8])
y <- logistic$V8

lrmoe <- LogisticRMoE(
  Xmat = X,
  Ymat = y,
  K = 2,
  Lambda = 3,
  Gamma = 3,
  option = FALSE # FALSE: proximal Newton; TRUE: proximal Newton-type
)

lrmoe$plot()
```

The fitted model can be visualized using `plot()`.

<img src="man/figures/README-unnamed-chunk-8-1.png" style="display: block; margin: auto;" /><img src="man/figures/README-unnamed-chunk-8-2.png" style="display: block; margin: auto;" />

The following example fits a multinomial RMoE model to a real dataset with two experts.

``` r

data("ionosphere")

X <- as.matrix(ionosphere[, -35])
y <- ionosphere$V35

lrmoe <- LogisticRMoE(
  Xmat = X,
  Ymat = y, 
  K = 2, 
  Lambda = 3, 
  Gamma = 3, 
  option = FALSE # FALSE: proximal Newton; TRUE: proximal Newton-type
)

lrmoe$plot()
```

The fitted model can be visualized using `plot()`.

<img src="man/figures/README-unnamed-chunk-9-1.png" style="display: block; margin: auto;" /><img src="man/figures/README-unnamed-chunk-9-2.png" style="display: block; margin: auto;" />

</details>

<details>

<summary>Poisson Regularized Mixture-of-Experts</summary>

The following example fits a Poisson RMoE model to a simulated dataset with two experts.

``` r

data("poisson")
X <- as.matrix(poisson[, -8])
y <- poisson$V8

prmoe <- PoissonRMoE(
  Xmat = X, 
  Ymat = y, 
  K = 2, 
  Lambda = 20, 
  Gamma = 10,
  option = FALSE # FALSE: proximal Newton; TRUE: proximal Newton-type
)

prmoe$plot()
```

The fitted model can be visualized using `plot()`.

<img src="man/figures/README-unnamed-chunk-10-1.png" style="display: block; margin: auto;" /><img src="man/figures/README-unnamed-chunk-10-2.png" style="display: block; margin: auto;" />

The following example fits a Poisson RMoE model to a real dataset with two experts.

``` r

data("cleveland")
X <- as.matrix(cleveland[, -15])
y <- cleveland$V15

prmoe <- PoissonRMoE(
  Xmat = X, 
  Ymat = y, 
  K = 2, 
  Lambda = 10, 
  Gamma  = 4, 
  option = FALSE # FALSE: proximal Newton; TRUE: proximal Newton-type
)

prmoe$plot()
```

The fitted model can be visualized using `plot()`.

<img src="man/figures/README-unnamed-chunk-11-1.png" style="display: block; margin: auto;" /><img src="man/figures/README-unnamed-chunk-11-2.png" style="display: block; margin: auto;" />

</details>
