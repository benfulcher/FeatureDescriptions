# Symbolic features

### `SB_MotifThree_quantile_hh`

This feature:

1. Converts each value in the time series into one of three symbols ('A', 'B', or 'C') using an equiprobable binning in which the lowest 3rd of values are assigned 'A', the middle 3rd 'B', and the highest 3rd of values are given 'C'.
2. It then analyzes the probabilities of all two-letter sequences ('AA', 'AB', 'BB', …) and outputs the entropy of this set of probabilities.

This feature is based on the _hctsa_ code `SB_MotifThree(x_z,'quantile')`, returning the `hh` output.

Time series that have predictable two-letter sequences (i.e., some sequences are far more probable than others) will have low values, and time series that are less predictable (i.e., all two-letter sequences are approximately equiprobable) will have high values.

For example, this Ricker map is highly predictable, with letters (A=red, B=blue, C=green) shown below, converting to "ABCABCABCABC…", such that "AB", "BC", and "CA" become highly probable sequences. It has a very low value for this feature (1.1):

![](<../.gitbook/assets/image (34).png>)

Here is another very predictable series, which has a very long string of C, then B, then A, such that "AA", "BB", and "CC" are highly probable sequences yielding low entropy (1.1):

![](<../.gitbook/assets/image (38).png>)

Time series that have predictable patterns on longer than 2-length windows, or that requiring more granularity than a 3-letter symbolization to resolve, have high values, like this map:

![](<../.gitbook/assets/image (32).png>)

### `SB_TransitionMatrix_3ac_sumdiagcov`

