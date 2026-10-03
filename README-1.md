# Kepler-8 Transit Analysis

Detecting the transit of the exoplanet Kepler-8 b in Kepler lightcurve data using Python, `lightkurve` and the Box Least Squares (BLS) algorithm.

## Goal

Detect a periodic transit signal in the Kepler lightcurve of Kepler-8 (KIC 6922244) and compare the result with the known values from the NASA Exoplanet Archive.

## Data

- Mission: Kepler
- Star: Kepler-8 (KIC 6922244)
- Source: NASA MAST archive, accessed with the `lightkurve` library

## Method

1. Downloaded the lightcurve and normalized the flux.
2. Binned the data to 30-minute bins, removed slow brightness trends with `flatten()`, and clipped upward outliers.
3. Ran a BLS periodogram to search for repeating dips (period range 1 to 10 days).
4. Folded the lightcurve on the best period to inspect the shape of the transit.

## Results

| Quantity | My result | NASA Exoplanet Archive (Kepler-8 b) |
|---|---|---|
| Period (days) | 3.524 | ___ |
| Depth | 0.0084 (about 0.84%) | optional |
| Duration (days) | 0.1 (about 2.4 hours) | ___ |

The BLS period agrees with the known orbital period of Kepler-8 b. The duration is approximate because the BLS search only tried a few duration values.

## Plot

![Folded transit of Kepler-8 b](fold_plot.png)

Folded lightcurve of Kepler-8. The transit appears as a clear dip at phase 0, about 0.9% deep, and the flux is flat outside the transit. The red line is the binned average and the gray dots are the individual measurements.

## Limitations

- Only a single quarter of Kepler data was used.
- The BLS duration grid is coarse, so the duration estimate is approximate.
- This is a learning project and has not been independently validated.

## Other practice

I also classify light curves on the Planet Hunters TESS project on Zooniverse. That is citizen-science practice and does not count as a confirmed discovery.

## Tools

Python, lightkurve, NumPy, pandas, Matplotlib (Google Colab)
