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
**v4** |**v6,v9,v11,v13,v14,v17,v19,v24,v25 (no const)**|**0.972**|**All**

**Nov 08 2018**: Wrote a general function to do the above. It's definitely not perfect, but it seems to yield pretty decent results. Since v2 was the next predictor variable (it has high correlation with 9 other variables), I performed the same analysis as above on v2. The results are below.  



| Expt. No. |   DV   |                     IVs                     | Adj. R^2  | Significant IVs               |
| --------- | :----: | :-----------------------------------------: | :-------: | ----------------------------- |
| 1         |   v2   |                     v4                      |   0.804   | All                           |
| 2         |   v2   |                v4 (no const)                |   0.818   | All                           |
| 3         |   v2   |                    v4,v6                    |   0.924   | All                           |
| 4         |   v2   |              v4,v6 (no const)               |   0.93    | All                           |
| 5         |   v2   |                  v4,v6,v9                   |   0.924   | v4,v6,v9                      |
| 6         |   v2   |             v4,v6,v9 (no const)             |   0.93    | All                           |
| 7         |   v2   |                v4,v6,v9,v10                 |   0.925   | All                           |
| 8         |   v2   |           v4,v6,v9,v10 (no const)           |   0.931   | v4,v6,v10                     |
| 9         |   v2   |              v4,v6,v9,v10,v14               |   0.933   | All                           |
| 10        |   v2   |         v4,v6,v9,v10,v14 (no const)         |   0.939   | All                           |
| 11        |   v2   |            v4,v6,v9,v10,v14,v16             |   0.981   | v6,v9,v10,v14,v16,v18         |
| 12        |   v2   |       v4,v6,v9,v10,v14,v16 (no const)       |   0.983   | All                           |
| 13        |   v2   |          v4,v6,v9,v10,v14,v16,v18           |   0.981   | v6,v9,v10,v14,v16,v18         |
| 14        |   v2   |     v4,v6,v9,v10,v14,v16,v18 (no const)     |   0.983   | v4,v6,v9,v10,v14,v16          |
| 15        |   v2   |        v4,v6,v9,v10,v14,v16,v18,v19         |   0.992   | All                           |
| **16**    | **v2** | **v4,v6,v9,v10,v14,v16,v18,v19 (no const)** | **0.993** | **v4,v6,v10,v14,v16,v18,v19** |
| 17        |   v2   |      v4,v6,v9,v10,v14,v16,v18,v19,v24       |   0.992   | All                           |
| 18        |   v2   | v4,v6,v9,v10,v14,v16,v18,v19,v24 (no const) |   0.993   | v4,v6,v10,v14,v16,v18,v19,v24 |

Next, seeing row 16 had the best results--highest adjusted R^2 and least number of significant IVs, I ran the OLS model on just these. All the IVs had p-value 0. I also plotted the residuals vs. fits plot for both v2 and v4. For v2, the Pearson R value was 0.44, and for v4, the Pearson R value was 0.41. Both the plots are in the notebook.

**Nov 17 2018**: Explored DBSCAN and mean-shift algorithms for clustering points. With `eps` of 45, DBSCAN produced 3 clusters, and 60 individual clusters. Mean-shift gave 12 clusters, where 5 had only one point. The distribution of the number of points in both was very similar.  

**Nov 19 2018**: Clustered points for the subset of the data, and did the analysis above with a little more detail, tracking every point in both clustering algorithms.

**Nov 20 2018**: Started writing the paper. Completed half of the Method section. Continued this on Nov 21 2018.

**Nov 26 2018**: Checked whether v9-v21 and v24 have the same distributions using the KS test. All p-values were below 0.05, so none of these have the same distribution. Also ran clustering algorithms on z-standardized and min-max scaled data. DBSCAN produced pretty bad results (though this was rather predictable), but MeanShift produced interesting results.