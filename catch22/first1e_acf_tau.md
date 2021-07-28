# Autocorrelation Function Features

## `first1e_acf_tau`

### What it does

The `first1e_acf_tau` feature in _catch22_ computes the first 1/_e_ crossing of the autocorrelation function of the time series. In _hctsa_, this can be computed as `CO_FirstCrossing(x_z,'ac',1/exp(1),'discrete')`.

This feature measures the first time lag at which the autocorrelation function drops below 1/_e_ \(= 0.3679\).

### What it measures

`first1e_acf_tau` captures the approximate scale of autocorrelation in a time series. This can be thought of as the number of steps into the future at which a value of the time series at the current point and that future point remain substantially \(&gt;1/_e_\) correlated. For a continuous-time system, this statistic is high when the sampling rate is high relative to the timescale of the dynamics.

* For uncorrelated noise, like the Poisson-distributed series shown below, the autocorrelation function drops to ~0 immediately, and we obtain the minimum value of this statistic: `first1e_acf_tau = 1`.

![](../.gitbook/assets/image%20%2811%29.png)

* For processes with a greater level of autocorrelation, the autocorrelation function decays more slowly, and we can obtain a larger value of this feature. Take this series simulated from a Chirikov map, which has `first1e_acf_tau = 6`

  :

![](../.gitbook/assets/image%20%2810%29.png)

* We obtain even larger values for even more slowly varying time series, like this ODE, measured at a very high sampling rate, yielding `first1e_acf_tau = 17`

![](../.gitbook/assets/image%20%281%29.png)

* Financial series \(and many non-stationary stochastic processes\) are highly autocorrelated, like this series for which `first1e_acf_tau = 176`

![](../.gitbook/assets/image%20%286%29.png)

## `firstMin_acf`

Similar to the 1/_e_ crossing feature above, `firstMin_acf` computes the first minimum of the autocorrelation function. It exhibits similar behavior.

