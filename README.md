# NosRMCM supporting materials

These files contain stored numerical summaries for the article *NosRMCM: Scalable Rough Membership C-Means Clustering via Mass-Weighted Node Summaries*. The figure and table numbers refer to the submitted manuscript. The file [experiment_settings.json](experiment_settings.json) lists the datasets, node counts, neighborhood settings, repetition or seed choices, and other recorded conditions by experiment. Figure 1 is a constructed example with its inputs in fig1_example.json.

| Manuscript item | Data and interpretation |
|---|---|
| Figure 1 | `fig1_example.json` contains the synthetic example. |
| Figures 2 and 3 | `fig2_fidelity.json`, `fig3_radius.json` and `fig3_knn.json` summarize fidelity across node counts, sample sizes and neighborhood definitions. |
| Table 1 | `table1_batch.json` records the prespecified criteria and setting-level statistics on four additional data sets. |
| Table 2 | `table2_trials.csv` contains the matched trials, including those excluded by the baseline-distance rule. `table2_ablation.csv` contains the 77 retained setting summaries. `table2_medians.json` gives the four table entries before rounding. |
| Figure 4 and the abstract | `fig4_scaling.json` records matrix sizes in bytes and the timing measurements. In `fig4_memberships.json`, select `per_n → 30000 → timed → 500` for the corresponding membership comparison. Memory units in the article are decimal. |
| Figure 5 and the stream evaluation | `fig5_stream.json` and `stream_confirmation.json` summarize the stream and additional data sets. |
| Table 3 | `table3_tuning.json` contains the reported hyperparameter-tuning summaries. |

For Figures 2 and 3, the corresponding trial CSVs give the setting, seed and distances. For each retained trial, compute fidelity as one minus the membership distance divided by the k-means distance for that trial. For Figure 4, fig4_measurements.csv records measured matrix sizes and timing ranges; rows with only an estimated size were not run. The times were measured on a single thread of one computer in three separate processes; `time_total` is the median over the processes and the minimum and maximum are over the processes (conditions in experiment_settings.json). For Figure 5, fig5_windows.csv records arrival fidelity and seconds per input (median over three processes) by window and stream order. The batch reference lines are the median batch fidelities in fig5_stream.json.

For Table 2, retain trials with `D_kmeans >= 0.01`. For each trial compute `rho = 1 - D_out_pt / D_kmeans`. Within each dataset, radius quantile, requested node count and method, take the median of each metric across retained seeds. Then take the median of the 77 setting medians separately for each method. The reported paired gain uses the median of the 77 within-setting differences in rho. Trial seeds were 0 through 4, with ten restarts. Both fits used the same radius-based point-output procedure.

The four additional batch datasets are OpenML [1459 v1](https://www.openml.org/d/1459), [1475 v1](https://www.openml.org/d/1475), [4538 v1](https://www.openml.org/d/4538) and [40966 v4](https://www.openml.org/d/40966). The scaling experiments used [Skin Segmentation 1502 v1](https://www.openml.org/d/1502) and [Pendigits 32 v1](https://www.openml.org/d/32). Besides four data sets bundled with scikit-learn, the tuning comparison (Table 3) used OpenML [6](https://www.openml.org/d/6), [60](https://www.openml.org/d/60), [40499](https://www.openml.org/d/40499), [299](https://www.openml.org/d/299), [1476](https://www.openml.org/d/1476), [12](https://www.openml.org/d/12), [41070](https://www.openml.org/d/41070) and [40996](https://www.openml.org/d/40996) (version 1, in the order of the table). The manuscript describes feature processing, sampling and initialization for each experiment.

These files are released under the Creative Commons Attribution 4.0 International license (CC BY 4.0; see LICENSE).
