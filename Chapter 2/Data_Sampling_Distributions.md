# 1.1 Random Sampling and Sample Bias

A **Sample** is a subset of data from a larger dataset called the **Population**.

---

## Random Sampling

**Random sampling** is a process in which each available member of the population has an **equal chance** to be chosen at each draw.
* The resulting sample is called a **Simple Random Sample**.
* It can be done **with replacement** (members can be selected more than once) or **without replacement** (members cannot be selected more than once).

### Stratified Sampling

**Stratified sampling** involves dividing the population into different **strata** and then randomly sampling from each stratum.
* **Stratum**: A **homogeneous subgroup** of a population with common characteristics.

---

## Data Quality

Data quality involves:
* **Completeness**
* **Consistency** of format
* **Cleanliness**
* **Accuracy**
* **Representativeness**

---

## Statistical Bias and Sample Bias

**Statistical Bias** is a **systematic error** (e.g., error in a measuring scale).
* It differs from **random error**, which cancels out on average.

**Sample Bias** occurs when a sample **misrepresents the population**.
* It's a non-random issue; the difference is **meaningful** and expected to continue across other samples.
* It can be avoided by **random selection**.

### Types and Examples of Selection Bias

**Selection Bias** is a bias resulting from the way in which observations are selected.

| Type of Bias | Description / Example |
| :--- | :--- |
| **Self-selection Sampling Bias** | Individuals select themselves for the sample (e.g., café reviews). |
| **Nonrandom Sampling** | The sample is not a representative of the population. |
| **Cherry Picking Data** | Choosing only the data that supports a hypothesis. |
| **Time Interval Selection** | Selecting time intervals that make the data look a certain way. |
| **Stopping Experiment Early** | Stopping an experiment when the result looks interesting by chance, instead of adhering to the pre-decided method. |
| **Data Snooping** | Excessive hunting through data in search of something interesting. |
| **Vast Search Effect** | Bias or non-reproducibility resulting from repeated data modeling. |

### Regression to the Mean

**Regression to the mean** is a phenomenon where extreme observations tend to be followed by more central ones in successive measurements. Attaching special meaning to an extreme value often leads to **selection bias**.

---

### Solutions to Avoid Bias

* Having **holdout sets** (more than one) to validate performance.
* **Target Shuffling**: A test to validate the predictive associations suggested by a data mining model.

# 📉 1.2 Sampling Distribution of a Statistic

## Key Definitions

| Term | Definition |
| :--- | :--- |
| **Sample Statistic** | A metric (e.g., mean, median, standard deviation) calculated for a single sample of data drawn from a larger population. |
| **Data Distribution** | The frequency distribution of individual values within a single sample. |
| **Sampling Distribution** | The frequency distribution of a **sample statistic** over many samples or resamples drawn from the population. |

### Visualizing the Sampling Distribution

The sampling distribution is created by:
1.  Drawing many samples (e.g., 1,000 samples) of a specific size (e.g., size $n=10$).
2.  Calculating the statistic (e.g., mean $\bar{x}$) for each of the $k$ samples ($$\bar{x}1, \bar{x}2, ..., \bar{x}{k}$$).
3.  Drawing a frequency distribution of these $k$ calculated means. 

---

## Standard Error (SE)

The **Standard Error (SE)** quantifies the **variability of a sample statistic** over many samples.
* **Sampling Variability**: Different samples from the same population will yield different measurements (statistics). The key concern is knowing *how* different these measurements are.
* In traditional statistics, the SE is crucial because we make inferences about the population based on a single sample statistic.

### The Central Limit Theorem (CLT)

The CLT describes the theoretical behavior of the sampling distribution:
* The sampling distribution of the mean tends to take on a **normal shape** as the sample size ($n$) increases, regardless of the population's underlying distribution.
* **The Square Root of $n$ Rule**: This rule defines the relationship between the Standard Error (SE) and the sample size:
    $$SE \approx \frac{s}{\sqrt{n}}$$
    Where $s$ is the standard deviation of the sample, and $n$ is the sample size.

### Calculating Standard Error without CLT

If we could collect multiple new samples, the SE could be calculated empirically:
1.  Collect $n$ new samples.
2.  For each sample, calculate the desired statistic (e.g., the mean).
3.  Calculate the **Standard Deviation (SD)** of all the resulting sample means. This value is the **Standard Error (SE)**.

**The Problem**: Collecting many new samples is often not feasible or too expensive.

### Practical Solution: Bootstrapping

The **bootstrap resamples** method is the solution used to estimate the Standard Error and other statistics without relying on the Central Limit Theorem. It involves repeatedly drawing samples **with replacement** from the single sample you already have.

1. Draw a sample value (ex: original sample has size of m = 100 observations) pick one sample value (say 9) and record it and then replace it
2. Repeat n times (take n sample values with replacement from m observations)
3. Record the mean of these n resampled values
4. Repeat steps 1-3 R times, we will have R different means
5. Use it to calculate their standard deviation and produce a histogram/boxplot and find a confidence interval
6. For an x% confidence interval, trim [(100 - x) / 2]% of the R resample results from either end of the distribution.
7. The trim points are the endpoints of an x% bootstrap confidence interval.
