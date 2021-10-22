# Nonlinear Autocorrelation Statistics

### `CO_trev_1_num`

This statistic computes computes the average across the time series of the cube of successive time-series differences. It will be close to zero for time series for which the distribution of successive decreases in the time series matches the distribution of successive increases, but will be positive if increases tend to be larger in magnitude and negative if decreases tend to be larger in magnitude.

The statistic is computed as:

$$
\langle (x_{i+1} - x_i)^3\rangle_t\,,
$$

for time-series values, _x_, averaged across all possible time points_, t _(i.e., from index 1 to N-1, for a time series of length _N_).

It is based on a statistic used in nonlinear time-series analysis, cf. [Surrogate time series](https://doi.org/10.1016/S0167-2789\(00\)00043-9), Schreiber and Schmitz, _Physica D_, **142: **346 (2000).

The original _hctsa_ implementation is the code `CO_trev(x_z,1)` , for a _z_-scored time series, `x_z`.

For example, this Chua map time series has increments that are approximately symmetric (blue histogram), as are the cubic increments (orange histogram), and so this statistic has a value (the mean of the orange distribution) of approximately zero.

![](<../.gitbook/assets/image (23).png>)

This simple flow has a multimodal distribution of successive increments (blue), with an asymmetry towards larger increases compared to smaller decreases. This is accentuated after taking a cube (orange), yielding a positive value of this statistic:

![](<../.gitbook/assets/image (24).png>)

This Lozi map is an example of the opposite behavior: time-series decreases can be sudden and large in magnitude, whereas increases are relatively gradual. This leads to an asymmetry towards large negative values, leading to a negative value for this statistic.

![](<../.gitbook/assets/image (25).png>)

### `CO_HistogramAMI_even_2_5`

(NB: renamed in current _hctsa _library, as the feature named `CO_HistogramAMI_even_5bin_ami2`)

This feature is a nonlinear version of the autocorrelation function: using a nonlinear correlation metric (mutual information) instead of a conventional linear correlation metric, evaluated using a histogram with 5 bins and at a time delay _τ_ = 2 (from the _hctsa_ code `CO_HistogramAMI(x_z,2,'even',5)`).

This feature gives high values to time series like this Chaotic Web map:

![](<../.gitbook/assets/image (26).png>)

, which has clear dependence structure of the time-series value at the current point, _x\_t_, and the value two time points ahead, _x\_{t+2}, _yielding a high value for this feature of 1.25:

&#x20;![](<../.gitbook/assets/image (31).png>)

This Tent map also has a clear (nonlinear) dependence of present time-series value with that two-steps into the future (and a moderate value of this feature, 0.473):

![](<../.gitbook/assets/image (32).png>)

as seen in its embedding:

![](<../.gitbook/assets/image (33).png>)

And a moderate value (0.25) for this heart rhythm:

![](<../.gitbook/assets/image (29).png>)

![](<../.gitbook/assets/image (34).png>)

But a low value (0.02) for this earthquake time series:

![](<../.gitbook/assets/image (27).png>)

![](<../.gitbook/assets/image (30).png>)







