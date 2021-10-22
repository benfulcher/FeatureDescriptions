# Simple Forecasting-Based Features

_catch22_ contains two features that capture the behavior of two (very!) simple forecasting algorithms that use the previous value, or the mean of the previous 3 values to predict the next value in the time series.

### `FC_LocalSimple_mean1_tauresrat`

This feature is the `tauresrat` output of running the code `FC_LocalSimple(x_z,'mean',1)` in_ hctsa. _It computes:

1. The set of incremental differences between successive pairs of time-series values (imagining this as the set of residuals from a naive 1-point forecast).
2. Computes the first zero-crossing of the autocorrelation function for the residuals, `tau_resid`, and for the original time series, `tau`.
3. Returns the ratio of these two values, `tau_resid/tau`.

Here's an example of a time series, where the autocorrelation function (black, lower plot) decays slowly due to slower trends in the time series (black, upper plot), whereas the incremental differences (blue in the upper plot) are much noisier, leading to a rapid drop of the autocorrelation function, and reduction in the first zero-crossing from 15 -> 1.

![](<../.gitbook/assets/image (17).png>)

By contrast, in this AR(2) time series, the increments are still highly autocorrelated, and we end up with a value of the feature near 1.

![](<../.gitbook/assets/image (19).png>)



### `FC_LocalSimple_mean3_stderr`

This feature computes the `stderr` output from running the code `FC_LocalSimple(x_z,'mean',3)` in _hctsa_. It returns the a measure of error from using the mean of the previous 3 values of the time series to predict the next value. The error statistic used here is the standard deviation of the residuals from the full set of simple 1-step forecasts. Because the input time series is _z_-scored (standard deviation of 1), the residuals should have a standard deviation less than 1 if this forecasting method is doing something (at least minimally) useful.

Time series that are easy to predict (i.e., time series for which the mean of the 3 previous time steps are a good prediction of the current value) will get low values of this feature.

Here's an example of a predator-prey system (black) for which the dynamics are varying on a timescale of 3 steps, such that mean-3 predictions (blue) are very poor forecasts. For this time series, the residuals have a higher variance than the original time series.

![](<../.gitbook/assets/image (21).png>)

This ODE system, by contrast is very highly sampled, such that the time series is a similar value in 3 steps, and the forecasts (blue) are very close to the original time series, yielding residuals with a very low standard deviation (0.03).

![](<../.gitbook/assets/image (22).png>)

