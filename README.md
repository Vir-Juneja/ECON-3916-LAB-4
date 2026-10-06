# ECON-3916-LAB-4
# Robust Statistics -- Automated Anomaly Detection

## Objective
I compared how different summary statistics and outlier detection methods handle the skewed house values in the California Housing dataset.

## Methodology
- Loaded the California Housing dataset (20,640 census block groups) from scikit-learn and focused on median house value.
- Computed six summary measures: mean, median, 10% trimmed mean, standard deviation, IQR, and MAD.
- Compared the standard deviation to the scaled MAD (MAD × 1.4826) to see how much the right tail stretches the spread.
- Calculated Tukey Fences by hand (Q1 − 1.5×IQR and Q3 + 1.5×IQR) and flagged house values outside them.
- Plotted the fences on a histogram and a boxplot.
- Fit an Isolation Forest on the eight non-price features with 5% contamination.
- Compared which block groups each method flagged and looked at what made the forest-only rows unusual.
- Built an interactive dashboard with ipywidgets that lets me change the column, Tukey's k, and the contamination rate.

## Key Findings
- House values are right-skewed (skewness 0.98). The mean ($206,860) is about $27,000 above the median ($179,700), and the trimmed mean ($192,770) falls between them.
- The standard deviation ($115,396) is about 14% larger than the scaled MAD ($101,410), which shows how much the high-value tail inflates the spread.
- Tukey Fences flagged 1,071 block groups, all above the upper fence. The lower fence was negative, so no low values could be flagged.
- 965 of the 1,071 Tukey outliers sit at the Census cap of $500,001, so they reflect how the data was recorded, not real prices.
- Isolation Forest flagged 1,032 block groups, but only 165 were flagged by both methods. The forest-only rows had more than twice the average household occupancy, which a price-only method can't catch.
- Plotting the data showed patterns the summary statistics hid, especially the pile of values at the $500,001 cap.
