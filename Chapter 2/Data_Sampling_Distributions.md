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

## Solutions to Avoid Bias

* Having **holdout sets** (more than one) to validate performance.
* **Target Shuffling**: A test to validate the predictive associations suggested by a data mining model.
