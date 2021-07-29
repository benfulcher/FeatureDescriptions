# Nonlinear Autocorrelation Statistics

### `CO_trev_1_num`

This statistic computes computes the average across the time series of the cube of successive time-series differences. It will be close to zero for time series for which the distribution of successive decreases in the time series matches the distribution of successive increases, but will be positive if increases tend to be larger in magnitude and negative if decreases tend to be larger in magnitude.

The statistic is computed as:

$$
\langle (x_{i+1} - x_i)^3\rangle_t\,,
$$

for time-series values, _x_, averaged across all possible time points_, t_ \(i.e., from index 1 to N-1, for a time series of length _N_\).

It is based on a statistic used in nonlinear time-series analysis, cf. [Surrogate time series](https://doi.org/10.1016/S0167-2789%2800%2900043-9), Schreiber and Schmitz, _Physica D_, **142:** 346 \(2000\).

The original _hctsa_ implementation is the code `CO_trev(x_z,1)` , for a _z_-scored time series, `x_z`.

For example, this Chua map time series has increments that are approximately symmetric \(blue histogram\), as are the cubic increments \(orange histogram\), and so this statistic has a value \(the mean of the orange distribution\) of approximately zero.

![](../.gitbook/assets/image%20%2825%29.png)

This simple flow has a multimodal distribution of successive increments \(blue\), with an asymmetry towards larger increases compared to smaller decreases. This is accentuated after taking a cube \(orange\), yielding a positive value of this statistic:

![](../.gitbook/assets/image%20%2823%29.png)

This Lozi map is an example of the opposite behavior: time-series decreases can be sudden and large in magnitude, whereas increases are relatively gradual. This leads to an asymmetry towards large negative values, leading to a negative value for this statistic.

![](../.gitbook/assets/image%20%2824%29.png)

### 



