# The DN\_HistogramMode features

_catch22_ contains two features involving `DN_HistogramMode` function in  _hctsa:_

* `DN_HistogramMode_5`
* `DN_HistogramMode_10`

#### What it does

These functions involve computing the mode of the _z_-scored time series by:

1. _z_-scoring the input time series.
2. Computing a histogram using a given number of \(linearly spaced\) bins \(5 bins for`DN_HistogramMode_5`and 10 bins for `DN`\_`HistogramMode_10`\).
3. Returning the location of the bin with the most counts.

#### Intuition

Being a distributional property, this feature is completely insensitive to the time-ordering of values in the time series. Time series with a 



