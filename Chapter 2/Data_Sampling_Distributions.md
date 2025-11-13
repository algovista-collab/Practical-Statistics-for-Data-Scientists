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

# 1.2 Sampling Distribution of a Statistic

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

The percentage associated with the confidence interval is termed the level of confidence. The higher the level of confidence, the wider the interval. Also, the smaller the sample, the wider the interval (i.e., the greater the uncertainty). Both make sense: the more confident you want to be, and the less data you have, the wider you must make the confidence interval to be sufficiently assured of capturing the true value. This means, if we take many confidence intervals using the same method then 95% of those intervals will contain the true mean (mean of population which is fixed and unknown).

A Confidence Interval is generally calculated as:

$$\text{CI} = \text{Point Estimate} \pm (\text{Critical Value} \times \text{Standard Error})$$

# 1.3 Distributions

## 1. Normal Distribution (Gaussian Distribution)

The **Normal Distribution** is a symmetric, bell-shaped distribution defined by its mean ($\mu$) and standard deviation ($\sigma$).

* **Standardize**: The process of transforming an individual data point by subtracting the mean and dividing the result by the standard deviation.
* **Z-score**: The result of standardizing an individual data point. It represents how many standard deviations the value is away from the mean.
* **Standard Normal Distribution**: A specific Normal distribution with a **mean ($\mu$) = 0** and a **standard deviation ($\sigma$) = 1**.
* **Empirical Rule**:
    * $\approx 68\%$ of the data lies within **one** standard deviation ($\pm 1\sigma$) of the mean.
    * $\approx 95\%$ of the data lies within **two** standard deviations ($\pm 2\sigma$) of the mean.
    * $\approx 99.7\%$ of the data lies within **three** standard deviations ($\pm 3\sigma$) of the mean.

### QQ Plot

A **QQ Plot (Quantile-Quantile Plot)** is a graphical tool used to visualize how closely a sample distribution follows a specified theoretical distribution (like the Normal distribution).
* It plots the $z$-score (or the observed data value) on the y-axis against the corresponding **quantile** (or theoretical $z$-score) of the specified distribution on the x-axis.

---

## 2. Standard Normal Distribution/Z-score Distribution

The process of converting a distribution into the Standard Normal Distribution is called **normalization** or **standardization**.
* The units on the x-axis are expressed in terms of the **number of standard deviations away from the mean**.

$$\text{z} = \frac{x - \mu}{\sigma}$$

---

## 3. Long-Tailed Distribution

* **Tail**: The long, narrow portion of a frequency distribution where **extreme values** occur at low frequency.
* **Skew**: A phenomenon where one tail of a distribution is longer than the other, indicating asymmetry.
* **Black Swan Theory (Nassim Taleb)**: Predicts that anomalous events (like a stock market crash) are much more likely to occur than would be predicted by the Normal distribution.
    * Tukey referred to this phenomenon as data being "normal in the middle but having **longer tails**." This means extreme events have a higher probability than the Normal distribution suggests.

---

## 4. Student's t-distribution

The **Student's t-distribution** is a family of distributions often used instead of the Normal distribution when the sample size is small or the population standard deviation is unknown.
* It is **normally shaped** but is generally **thicker and longer on the tails** than the standard normal distribution.
* As the **sample size increases**, the $t$-distribution becomes progressively more similar to the standard normal distribution.
* The family of $t$-distributions differs based on a parameter called **Degrees of Freedom**.

### Degrees of Freedom (DF)

**Degrees of Freedom ($df$)** is a parameter that allows the $t$-distribution to adjust to different sample sizes, statistics, and number of groups.
* For a single sample of size $n$, the degrees of freedom are typically **$n-1$**.
* **Intuitive Explanation**: If you know the sample mean and the sample size ($n$), only $n-1$ values in the sample can be freely chosen; the last value **must be fixed** to ensure the sample retains the pre-determined mean.
