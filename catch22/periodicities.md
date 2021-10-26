# Periodicities

### `PD_PeriodicityWang_th0.01`

This feature returns the first peak in the autocorrelation function satisfying a set of conditions (after detrending the time series using a single-knot cubic regression spline).

It is based on a method by Wang et al. (2007) (described in their paper: _"Structure-based Statistical Features and Multivariate Time Series Clustering" _[Link](https://doi.org/10.1109/ICDM.2007.103)_)._

Broadly, it gives high values to slowly-varying time series like this slow (on the timescale of $$\Delta t$$) oscillator (feature value of 62):

![](<../.gitbook/assets/image (39).png>)

And lower values to this fast (on the timescale of $$\Delta t$$) map (the Gingerbread map) (feature value = 4):

![](<../.gitbook/assets/image (26).png>)

### `SP_Summaries_welch_rect_area_5_1`

This feature computes the relative power in the lowest 20% of frequencies (relative to the sampling rate of the data) \[the output `area_5_1` from the _hctsa_ code `SP_Summaries(x_z,'welch','rect',[],false)`].

It gives high values to time series with lots of power in low frequencies, and low values to time series that have most of their power in higher frequencies.

The area under the power spectrum is estimated in linear space, where the power spectral density is estimated using Welch's method (with a rectangular window).

Here's an example of a slow-varying stocahstic process with a very high value for this feature, 0.987, reflecting 98.7% of power is this low-frequency band (relevant portion of the power spectrum shaded red below):

![](<../.gitbook/assets/image (40).png>)

This Lozi map has a low value of 0.03 (3% of power is in the red low-frequency band):

![](<../.gitbook/assets/image (35).png>)

### `SP_Summaries_welch_rect_centroid`

Like the previous feature, this one is also extracted from the power spectrum (estimated using a Welch's method with a rectangular window). But this time, it returns the frequency, $$f$$, at which the amount of power in frequencies low and higher than $$f$$ is the same: the "_**centroid**_".

It gives high values to time series that have their power in high frequencies, like this audio of an animal sound (centroid point shown with a red circle), 2.82:

![](<../.gitbook/assets/image (37).png>)

And it gives low values to slower-varying time series like this snippet of an electrocardiogram recording from a patient with congestive heart failure. 0.15:

![](<../.gitbook/assets/image (28).png>)

