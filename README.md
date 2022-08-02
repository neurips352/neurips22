# Synthetic Data
(the "Normal clusters" distribution chooses 20 cluster centers uniformly from the unit hypercube, then samples 100 points from a normal distribution with mean at the cluster center and with stddev=0.1 for each cluster center)
Note a superior err/rank tradeoff from the HDF in all cases below except the high d, high p, normal clusters settings. This is an example of a case where "the lack of additional compression based on the harmonics will result in poor efficiency" as discussed in the Limitations section of the main text, and is the subject of ongoing research. 
## d=5
### Cauchy kernel
* [Uniform distribution](https://github.com/neurips352/neurips22/blob/main/plots/unif_relerr_vs_rank_cauchy_d5_plot.pdf)
* [Uniform distribution on surface of unit hypersphere](https://github.com/neurips352/neurips22/blob/main/plots/spher_relerr_vs_rank_cauchy_d5_plot.pdf)
* [Normal clusters](https://github.com/neurips352/neurips22/blob/main/plots/mix_relerr_vs_rank_cauchy_d5_plot.pdf)
### Matern kernel
* [Uniform distribution](https://github.com/neurips352/neurips22/blob/main/plots/unif_relerr_vs_rank_matern15_d5_plot.pdf)
* [Uniform distribution on surface of unit hypersphere](https://github.com/neurips352/neurips22/blob/main/plots/spher_relerr_vs_rank_matern15_d5_plot.pdf)
* [Normal clusters](https://github.com/neurips352/neurips22/blob/main/plots/mix_relerr_vs_rank_matern15_d5_plot.pdf)
### Gaussian kernel
* [Uniform distribution](https://github.com/neurips352/neurips22/blob/main/plots/unif_relerr_vs_rank_gaussian_d5_plot.pdf)
* [Uniform distribution on surface of unit hypersphere](https://github.com/neurips352/neurips22/blob/main/plots/spher_relerr_vs_rank_gaussian_d5_plot.pdf)
* [Normal clusters](https://github.com/neurips352/neurips22/blob/main/plots/mix_relerr_vs_rank_gaussian_d5_plot.pdf)
## d=30
### Cauchy kernel
* [Uniform distribution](https://github.com/neurips352/neurips22/blob/main/plots/unif_relerr_vs_rank_cauchy_d30_plot.pdf)
* [Uniform distribution on surface of unit hypersphere](https://github.com/neurips352/neurips22/blob/main/plots/spher_relerr_vs_rank_cauchy_d30_plot.pdf)
* [Normal clusters](https://github.com/neurips352/neurips22/blob/main/plots/mix_relerr_vs_rank_cauchy_d30_plot.pdf)
### Matern kernel
* [Uniform distribution](https://github.com/neurips352/neurips22/blob/main/plots/unif_relerr_vs_rank_matern15_d30_plot.pdf)
* [Uniform distribution on surface of unit hypersphere](https://github.com/neurips352/neurips22/blob/main/plots/spher_relerr_vs_rank_matern15_d30_plot.pdf)
* [Normal clusters](https://github.com/neurips352/neurips22/blob/main/plots/mix_relerr_vs_rank_matern15_d30_plot.pdf)
### Gaussian kernel
* [Uniform distribution](https://github.com/neurips352/neurips22/blob/main/plots/unif_relerr_vs_rank_gaussian_d30_plot.pdf)
* [Uniform distribution on surface of unit hypersphere](https://github.com/neurips352/neurips22/blob/main/plots/spher_relerr_vs_rank_gaussian_d30_plot.pdf)
* [Normal clusters](https://github.com/neurips352/neurips22/blob/main/plots/mix_relerr_vs_rank_gaussian_d30_plot.pdf)
## Gaussian kernel, normal distribution, comparison with improved fast Gauss transform
* [d=3](https://github.com/neurips352/neurips22/blob/main/plots/d3_fgt.pdf)
* [d=5](https://github.com/neurips352/neurips22/blob/main/plots/d5_fgt.pdf)
* [d=7](https://github.com/neurips352/neurips22/blob/main/plots/d7_fgt.pdf)
## Error vs space experiment

To examine memory usage, we reran the error vs time synthetic experiment from the main paper, replacing @elapsed with @allocated in Julia. [The results for the HDF and Nystrom factorizations are here](https://github.com/neurips352/neurips22/blob/main/plots/err_vs_space_plot.pdf).

# Real-world Data
[In this experiment](https://github.com/neurips352/neurips22/blob/main/plots/power_relerr_vs_rank_plot.pdf) we use the Combined Cycle Power Plant Data Set and create the same diagonal blocks based on clusters as described in the main text (one change: sigma is set to 0.5 to increase the rank of the block, allowing us to explore more of the rank/error tradeoff). The figure shows the rank/error tradeoff for randomly chosen blocks. The size of the randomly chosen block is the title of each plot. In all these cases the HDF shows better tradeoff (in agreement with the synthetic experiments for similar parameters), although it is worth noting that the same limitation encountered for synthetic datasets which don't fill out ambient dimensions well enough is experienced for higher dimensional real-world datasets when high accuracy is desired - in this case a method is desired to efficiently compress the harmonic components. 
