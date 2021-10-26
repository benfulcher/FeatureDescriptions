# Self-Affine Scaling

_catch22_ contains two features that capture the behavior of two features based on fluctuation analysis, which aim to capture potential long-range correlations in time series, derived from the `SC_FluctAnal` function in [_hctsa_](https://github.com/benfulcher/hctsa).

Here is a reference for understanding scaling methods: _Power spectrum and detrended fluctuation analysis: Application to daily temperatures_ Talkner and Weber, _Phys. Rev. E_ **62:** 150 (2000).

The main steps of the method are as follows:

1. Compute a cumulative sum of the time series
2. Compute the level of fluctuation (e.g., root-mean-square deviations from local low-order trends) across windows corresponding to a given timescale. Different methods exist for detrending time-series windows at a given timescale, including (relevant to these two features):
   1. Rescaled range analysis removes a line connecting the endpoints of each window and computes the range of the remaining points (Caccia et al., Physica A, 1997)
   2. DFA fits a _k_-order polynomial to each window and computes the residuals from this fit.
3. Looks for linear scaling in the log(timescale)–log(fluctuation) plot.

Some time series exhibit 'multifractal' scaling: there are different scaling rules at different ranges of timescales. The two _catch22_ features fit two distinct scaling regimes and return the timescale at which the predicted change in scaling regime occurs.

Note that these features make quite strong assumptions about the data and can be unstable for time series that do not exhibit scaling, or exhibit strong but 'unifractal' scaling.

### `SC_FluctAnal_2_rsrangefit_50_1_logi_prop_r1`

This feature uses rescaled range analysis described above to estimate points in logarithmic timescale–fluctuation space.

Time series with (the best approximation to two distinct scaling regimes: the first scaling regime is indicated with red markers in the plots below) that change at a short timescale, like this AR(2) process, receive low values of this feature (0.2):

![](<../.gitbook/assets/image (42).png>)

And gives high values for time series where the scaling regime changes at longer timescales:

![](<../.gitbook/assets/image (30).png>)

Or this complex butterfly map:

![](<../.gitbook/assets/image (31).png>)

### `SC_FluctAnal_2_dfa_50_1_2_logi_prop_r1`

This feature measures the same property as above, but from a timescale–fluctuation curve estimated using detrended fluctuation analysis (DFA), using linear detrending in each window, after down-sampling the time series by a factor of 2.

It displays qualitatively similar behavior as the above, e.g., with low value for this oscillator (which has a change in the scaling relationship at short timescales).

![](<../.gitbook/assets/image (36).png>)

And higher values for time series that exhibit strong scaling through to longer timescales, like this log-return series of an opening share price:

![](<../.gitbook/assets/image (33).png>)



