# CSE549-project
Course project for Fall 17

### Link to find the data
https://drive.google.com/drive/folders/0B_OfHrdJFRfdb3h3eEwyZ0FsY3M

# Uncertainty Quantification
### Project Description
Salmon is a state-of-the-art tool for measuring gene expression (quantifying the abundance of different RNA transcripts in an experiment). One of the primary benefits of this method is that it is orders of magnitude faster than the competition, while producing results of the same or better accuracy. Salmon determines expression levels by solving a maximum likelihood problem. A result of this formulation is that one often gets accurate estimates of the transcript abundances, but has no notion of confidence in these predictions. That is, predictions can be highly specific and highly accurate, or highly specific and highly inaccurate --- this depends on the “shape” of the likelihood function, and how optimization proceeds. Thus, it is very valuable to provide some measure of confidence in the estimates that are inferred. There are a number of ways to estimate such confidence. One way is “bootstrapping”. This approach treats the observed sample data as the population, samples from the original data a number of times, and reruns the maximum likelihood estimator independently on all of these samples. By looking at the distribution of these different runs, one can form an empirical confidence interval, that provides a notion of the uncertainty of the maximum likelihood point estimate. However, a close inspection on simulated data demonstrates that these empirical intervals fail to capture the uncertainty adequately (i.e., they tend to underestimate the uncertainty).

The goal here is to determine what are the specific properties, if any, of the transcripts that tend to fall outside the predicted uncertainty interval. To be exact, we define the problem as follows: for each transcript expression, if the truth value is not within the 95% confidence interval  (i.e. greater than at least 2.5% of the bootstrap samples and less than the upper 97.5 percentile of the bootstrap samples) we count the transcript as a failure. We expect that, in statistically valid cases, only 5% of transcripts fall outside of the 95% confidence intervals. The steps of the project would be to filter the failing transcripts and then find some common properties between them, using sequence similarity or transcript quantification estimates or other variables output by Salmon during the bootstrapping phase. The second part is to come up with a quality score based on these properties. This score will reflect the level of confidence we have in the transcript-level estimates. 

### Inputs
- The following information about each transcript:
  - Length
  - Effective Length
  - Set of equivalence classes + their counts and transcript weight distributions
  - Count of ambiguous vs uniquely mapped reads
- Transcripts tpm distributions
- True transcripts tpm

### Output
- Property values + A Quality Measurement of that property
### Midway result
- Filter the faulty transcripts and provide some statistics regarding their properties
