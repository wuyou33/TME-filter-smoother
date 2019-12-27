# Taylor Moment Expansion (TME) Gaussian Filter and Smoother

This repo gives a simple Matlab illustration of using TME Gaussian filter and smoother for a simple Duffing van der Pol model.

**Please cite the following paper**
```
@article{zhengzTME2019,
	title = {{T}aylor Moments Expansion for Continuous-Discrete {G}aussian Filtering and Smoothing},
	journal = {***},
	volume = {**},
	number = {**},
	pages = {***},
	year = {2019},
	author = {Zheng Zhao, Toni Karvonen, Roland Hostettler, and Simo S\"{a}rkk\"{a}}
}
```
## About the Model
Considering a non-linear Continuous discrete state-space model (Duffing van der Pol)
![](figs/dyn.svg)
![](figs/obs.svg)
with initial value `x_0 = [-3, 0]`. 

Parameters of simulation
`alp = 2`: Value of \alpha. 
`T = 5`:   Value of time length of the simulaton
`dt = 0.01`: Time interval (Higher order TME can deal with longer dt)

We simply consider a linear measurement model because TME is only concerned with the non-linearity in continuous model. For some examples on non-linear measurement models, you can check our paper [1].

## How to Run
Simply open and run `TME_GHKF.m` (Gauss-Hermite) or `TME_CKF.m` (spherical cubature), or `TME_UKF` (unscented transform)
![](figs/duffing_result.svg)

## Theory of TME
TME is employed to give any momemt approximation of a diffusion process. For examplle `E[\phi(x_t)]` for any smooth function `\phi()`. Thus the idea is that we use TME to estimate the mean and covariance of the continuous model and thus enable Gaussian filtering and smoothing. For detailed theory of TME and TME filter and smoothers, we refer the readers to our paper [1] or Kessler 1997 for details.

### Positive Definiteness
The TME covariance estimate might not be positive definite in some unusual cases. This depends on the expansion order, dt, and the SDE model itself. You can analyze using Theorem 1 of [1]. But a simple engineering solution is to just give more integration steps (higher value of `it_steps`).

## License

The GNU General Public License

## Reference
[1] Zheng Z., Toni K., Roland H., and Simo S., Taylor Moment Expansion for Continuous-discrete Filtering and Smoothing. IEEE Transactions on Automatic Control (Submitted)

