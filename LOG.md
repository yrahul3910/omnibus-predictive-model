**Nov 01 2018**: Found Spearman's correlation coefficient value. The function also returns p-values, but these seem to indicate the probability that uncorrelated data generated the correlation values. Only 3% of these are above 0.05, so we can safely assume that all the correlation coefficients are correct. In addition, there are many correlations, and all seem to be positive. I confirmed this by first checking the fraction of values that were above a threshold, say 0.8, and then checking the fraction that were either above 0.8 or below -0.8. Both values were the same

**Nov 05 2018**: Found Pearson R coefficients, and visualized it to find the vars that have high R with many other variables. `v4` is this variable, and so I took this as the DV, and as suggested by Dr. Saha, started adding IVs one by one. I did not try all combinations since it is prohibitive (2^11), and randomly kept adding in one order. The results are below.
DV |IVs | Adj. R^2|Significant IVs
---|:---:|:---:|---
v4 |v6 | 0.759|All
v4 |v6,v7|0.769|All
v4 |v6,v7,v8|0.799|All
v4 |v6,v7,v8,v10|0.854|All
v4 |v6,v7,v8,v10,v11|0.857|All; v8 has 0.026
v4 |v6,v7,v8,v10,v11,v12|0.882|All
v4 |v6,v7,v8,v10,v11,v12,v14|0.886|All
v4 |v6,v7,v8,v10,v11,v12,v14|0.886|All
v4 |v6,v9|0.796|All except constant, p-value 0.18
v4 |v6,v9,v10 (no const)|0.868|All
v4 |v6,v9,v10 (w/ const)|0.835|All
v4 |v6,v9,v10,v11 (no const)|0.874|All
v4 |v6,v9,v10,v11 (w/ const)|0.846|All
v4 |v6,v9,v10,v11,v13 (no const)|0.893|All
v4 |v6,v9,v10,v11,v13 (w/ const)|0.866|All except constant
v4 |v6,v9,v10,v11,v13,v14 (no const)|0.896|All
v4 |v6,v9,v10,v11,v13,v14,v15 (no const)|0.896|All except v15
v4 |v6,v9,v10,v11,v13,v14,v16 (no const)|0.893|All except v16, p-value 0.052
v4 |v6,v9,v10,v11,v13,v14,v17 (no const)|0.912|All
v4 |v6,v9,v10,v11,v13,v14,v17,v19 (no const)|0.953|All except v10, p-value 0.051
v4 |v6,v9,v11,v13,v14,v17,v19 (no const)|0.961|All
v4 |v6,v9,v11,v13,v14,v17,v19,v24 (no const)|0.961|All
v4 |v6,v9,v11,v13,v14,v17,v19,v25 (no const)|0.953|All, v25 has 0.033
v4 |v6,v9,v11,v13,v14,v17,v19,v24,v25 (no const)|0.972|All


