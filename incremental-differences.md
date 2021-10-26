# Incremental differences

### `MD_hrv_classic_pnn40`

`MD_hrv_classic_pnn40` computes the proportion of difference magnitudes that are greater than 4% of the standard deviation of the time series.

This feature will give low values to series that have periods in which the series stays approximately constant (within $$0.04\sigma$$), and high values to series that do (e.g., they 'jump around alot' from point to point).

This is a common statistic to measure about heart rate time series, cf. "_The pNNx files: re-examining a widely used heart rate variability measure"_, J.E. Mietus et al., Heart 88(4) 378 (2002).

For example, the Rossler attractor time series below has many near-constant stretches (Just 14.5% of all step increments are larger than $$0.04\sigma$$), yielding a low value for this statistic:

![](<.gitbook/assets/image (29).png>)

These log returns of opening prices of a stock, on the other hand, fluctuate alot more: 95% of successive increments exceed the $$0.04\sigma$$ threshold, yielding a high value for this statistic:

![](<.gitbook/assets/image (27).png>)

