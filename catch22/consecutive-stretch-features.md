# Consecutive Stretch Features

_catch22_ contains two features that capture the maximum length of time over which similar consecutive local patterns are observed:

* `SB_BinaryStats_mean_longstretch1`  measures the longest successive period of above-average values.
  * (the `longstretch1` output from running `SB_BinaryStats(x_z,'mean')` in _hctsa_);
* `SB_BinaryStats_diff_longstretch0` measures the longest successive period of successive decreases.
  * (the `longstretch0` output from running `SB_BinaryStats(x_z,'diff')` in _hctsa_).

### `SB_BinaryStats_mean_longstretch1`

### What it does

`SB_BinaryStats_mean_longstretch1` computes the longest sequence of successive values in the time series that are greater than the mean. Algorithmically, this is achieved in two steps:

1. Transform the time series into a binary sequence: time-series values that are greater than the mean are set to `1` and time-series values that are less than or equal to the mean are set to `0`.
2. Return the longest sequence of successive values that are `1`.

### What it measures

* Low values are given to time series that tend not to linger too much on either side of the mean, like this moving average process, which has a maximum duration of 8 samples (red) above the mean (zero: dashed line):

![](<../.gitbook/assets/image (12).png>)

* High values are given to time series that have at least one long duration of time spent above the mean, like this stochastic sine map (107 successive time points above the mean):

![](<../.gitbook/assets/image (13).png>)

### `SB_BinaryStats_diff_longstretch0`

### What it does

`SB_BinaryStats_diff_longstretch0` is similar to the above, but it calculates the longest sequence of successive steps in the time series that _decrease_. Algorithmically, this is achieved in two steps:

1. Transform the time series into a binary sequence: each time-series value is converted to a `1` if it is higher than the previous time point, and `0` if it is lower than the previous time point (starting from the second point in the time series, and thus yielding a sequence of length `N-1`, where `N` is the length of the original time series).
2. Return the longest sequence of successive values that are `0`.

### What it measures

* Here is a time series of a time series from the complex butterfly map, with the longest period (of 30) successive decreases highlighted in red

![](<../.gitbook/assets/image (16).png>)

