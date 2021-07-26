# The DN\_HistogramMode features

_catch22_ contains two features involving the `DN_HistogramMode` function in  _hctsa:_

* `DN_HistogramMode_5`
* `DN_HistogramMode_10`

**Note:** The C implementation of these features \(in _catch22_\) does not map perfectly onto the _hctsa_ implementation, due to slight differences in how the histogram bins are constructed. But the trends are similar.

### What it does

These functions involve computing the mode of the _z_-scored time series through the following steps:

1. _z_-score the input time series.
2. Compute a histogram using a given number of \(linearly spaced\) bins \(5 bins for`DN_HistogramMode_5`and 10 bins for `DN_HistogramMode_10`\).
3. Return the location of the bin with the most counts.

### What it measures

Being distributional properties, these features are completely insensitive to the time-ordering of values in the time series. Instead, they capture how the most probable time-series values are positioned relative to the mean.

* Time series with a symmetric distribution, with a central peak, will have a mode near the center, and a value close to zero. Here is an example, of Gaussian-distributed noise \(`NS_norm_L1000_a0_b10_4` \) which obtains a score of -0.36.

![](../.gitbook/assets/screen-shot-2021-07-23-at-17.39.49.png)

* Time series with a symmetric distribution but with density far from the origin, like this Chirikov map \(`MP_chirikov_L1000_IC_0.2_6_x`\) obtain high \(positive or negative\) values:

![](../.gitbook/assets/screen-shot-2021-07-23-at-17.41.14.png)

* Time series with positively skewed distributions, like this example of beta-distributed noise \(`NS_beta_L10000_a1_b3_2.dat`\), obtain negative values as shown below:

![](../.gitbook/assets/image%20%289%29.png)

* \(and similarly negatively skewed distributions obtain positive values\)

