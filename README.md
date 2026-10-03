# Kepler-8 Transit Analysis

Python (lightkurve) se Kepler lightcurve data me planet transit dhoondhne ka chhota project.

## Goal
Known star Kepler-8 (KIC 6922244) ke lightcurve se transit signal detect karna, aur result ko NASA Exoplanet Archive ke known value se compare karna.

## Data
- Mission: Kepler
- Star: Kepler-8 (KIC 6922244)
- Source: NASA MAST archive (`lightkurve` library ke through)

## Method
1. Lightcurve download aur normalize kiya
2. 30-minute bins banaye, `flatten()` se star ki slow brightness changes hataye, upar ke outliers remove kiye
3. BLS (Box Least Squares) periodogram se repeating dips dhoondhe (period range 1 se 10 din)
4. Best period par fold karke transit ka shape dekha

## Results

| Quantity | My result | NASA Exoplanet Archive |
|---|---|---|
| Period (days) | 3.524 | ___ (Kepler-8 b page se bharo) |
| Depth | 0.0084 (about 0.84%) | optional |
| Duration (days) | 0.1 (about 2.4 hours) | ___ (hours me, 24 se divide karo) |

My BLS period matches the known planet Kepler-8 b. Duration approximate hai, kyunki BLS me sirf kuch duration values try ki gayi.

## Plot

![Folded transit of Kepler-8 b](fold_plot.png)

`fold_plot.png`: folded lightcurve. Beech me saaf transit dip (about 0.9% deep), baaki flux flat. Red line binned average hai, gray dots original data.

## Limitations
- Sirf ek quarter ka data use hua
- BLS ki duration grid coarse hai, isliye duration exact nahi
- Ye learning project hai, professional validation nahi

## Other practice
Zooniverse (Planet Hunters TESS) par lightcurves me possible transits mark kiye. Wo sirf classification practice hai, confirmed discovery nahi.

## Tools
Python, lightkurve, numpy, pandas, matplotlib (Google Colab)
