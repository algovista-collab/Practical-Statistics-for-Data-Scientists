# 📊 Data Exploration: Elements and Estimates

The **first step** in any data science project is to **explore the data** to understand its characteristics, structure, and quality.

---

## 1.1 Elements of Structured Data

Understanding data types is crucial because it signals to the software how the data should be processed and analyzed.

| Data Type Category | Type | Intuition/Meaning |
| :--- | :--- | :--- |
| **Quantitative (Numerical)** | **Continuous** | Data that can take any value within a given range (e.g., temperature, height). |
| | **Discrete** | Data that can only take specific, fixed values, often integers (e.g., count of items, number of customers). |
| **Qualitative (Categorical)** | **Binary (Nominal)** | A variable with only two categories, which have no intrinsic order (e.g., Yes/No, True/False, Male/Female). |
| | **Ordinal** | A variable where the categories have a meaningful, inherent order or rank (e.g., Low/Medium/High, Survey responses like 'Agree' to 'Strongly Disagree'). |

---

## 1.2 Structured Data Representation

Structured data is typically organized in a **rectangular format** (like a spreadsheet or database table).

* **Data Frame (or Table):** The basic rectangular data structure used for statistical and Machine Learning (ML) models.
* **Feature (Column):** An individual variable or characteristic being measured (e.g., age, income). In ML, these are often **independent variables** or **predictors**.
* **Outcome (Target/Label):** The dependent variable or output that the model is trying to predict (e.g., a customer's purchase decision).
* **Record (Row/Instance/Observation):** A single set of measurements for all features and the outcome; represents one unit in the dataset.

---

## 1.3 Estimates of Location (Measures of Central Tendency)

These statistics describe where the "center" or "typical" value of the data lies.

### Mean (Average)

* **Meaning:** The sum of all values divided by the number of values. It's the most common measure of central tendency.
* **Intuition:** The point where the dataset would balance, physically speaking. It is sensitive to **outliers**.
* **Formula:**
    $$\bar{x} = \frac{\sum_{i=1}^{n} x_i}{n}$$

### Weighted Mean (Weighted Average)

* **Meaning:** An average where each value contributes a different amount, based on a corresponding weight.
* **Intuition:** Used when some values are inherently more important or representative than others (e.g., averaging grades where exams count more than quizzes, or adjusting for underrepresented groups in a sample).
* **Formula:**

$$\bar{x}_w = \frac{\sum_{i=1}^{n} w_i x_i}{\sum_{i=1}^{n} w_i}$$

### Median

* **Meaning:** The middle value in a dataset that has been sorted in ascending order. If the number of data points is even, it's the average of the two middle values.
* **Intuition:** It perfectly divides the data into two halves (50% of the data is above it, and 50% is below it). It is **robust** to outliers.
* **Calculation:**
    1.  Sort the data: $x_{(1)}, x_{(2)}, \dots, x_{(n)}$
    2.  If $n$ is odd, Median $= x_{(\frac{n+1}{2})}$
    3.  If $n$ is even, Median $= \frac{x_{(\frac{n}{2})} + x_{(\frac{n}{2} + 1)}}{2}$

### Percentile (Quantile)

* **Meaning:** The value below which a specified percentage of observations fall. The **median** is the 50th percentile.
* **Intuition:** Helps understand the spread and distribution of the data beyond just the center. For example, the **25th percentile** (First Quartile) and **75th percentile** (Third Quartile) are commonly used.

### Weighted Median

* **Meaning:** The value such that the sum of the weights of all observations less than or equal to the weighted median is at least half of the total sum of weights, and the sum of the weights of all observations greater than or equal to the weighted median is at least half of the total sum of weights.
* **Intuition:** Similar to the weighted mean, it applies importance to observations via weights, but retains the **robustness** property of the regular median against outliers.

### Trimmed Mean (Truncated Mean)

* **Meaning:** The mean calculated after discarding a fixed percentage of data points from both the high and low extremes (e.g., removing the top and bottom 5% of values).
* **Intuition:** It is a compromise between the **mean** and the **median**. It reduces the influence of extreme values, making it more **robust** than the regular mean without discarding too much information.

### Key Concepts

* **Robust:** A statistic is considered **robust** if it is not heavily influenced by extreme values or **outliers**. (e.g., Median, Trimmed Mean, Weighted Median).
* **Outlier:** A data point that is significantly distant from other observations. Outliers can skew the results of non-robust statistics like the simple **mean**.

## 1.4 Estimates of Variability (Dispersion)

While **estimates of location** (like mean and median) summarize the center of the data, **estimates of variability** (or dispersion) describe whether the data values are **clustered** or **spread out**.

---

### Key Concepts

* **Deviation (Error):** The difference between an **observed value** ($x_i$) and an **estimate of location** (e.g., the mean $\bar{x}$ or median $M$).
    $$\text{Deviation} = x_i - \bar{x}$$
* **Order Statistics:** Metrics based on the data values after they have been **sorted** from smallest to biggest.

---

### Measures of Variability

### Variance

* **Meaning:** The average of the squared deviations from the mean. It measures how far a set of numbers is spread out from their average value.
* **Intuition:** Squaring the deviations ensures that both positive and negative differences contribute to the total spread. Since squaring magnifies the effect of large deviations, **variance is highly sensitive to outliers**.
* **Formula (Sample Variance):**
    $$s^2 = \frac{\sum_{i=1}^{n} (x_i - \bar{x})^2}{n-1}$$
    > **Note:** We divide by $n-1$ instead of $n$ to provide an **unbiased estimate** of the population variance when using a sample.

### Standard Deviation (SD)

* **Meaning:** The square root of the variance. It returns the measure of variability to the **original units** of the data, making it more interpretable than variance.
* **Intuition:** Represents the typical distance between the data points and the mean. Since it is derived from the variance, **SD is also sensitive to outliers**.
* **Formula:**
    $$s = \sqrt{\frac{\sum_{i=1}^{n} (x_i - \bar{x})^2}{n-1}}$$

### Mean Absolute Deviation (MAD or $L_1$ Norm / Manhattan Norm)

* **Meaning:** The average of the absolute values of the deviations from the mean.
* **Intuition:** It's a straightforward average distance from the mean. By using the absolute value instead of squaring, it is **less sensitive to outliers** than the variance or SD, although still less robust than the median-based measure.
* **Formula:**
    $$\text{MAD} = \frac{\sum_{i=1}^{n} |x_i - \bar{x}|}{n}$$

### Median Absolute Deviation (MAD from the Median)

* **Meaning:** The median of the absolute deviations from the median.
* **Intuition:** This is a **highly robust** estimate of variability. It uses the median (a robust location estimate) to calculate the deviations, and then takes the median of those deviations, effectively minimizing the influence of extreme outliers on the measure of spread.

### Range

* **Meaning:** The difference between the largest and smallest observed values in the dataset.
* **Intuition:** Provides the simplest boundary of the data spread. It is **extremely sensitive to outliers** because it is calculated using only the two most extreme values, making it generally a poor measure of dispersion.
* **Formula:**
    $$\text{Range} = \text{Maximum Value} - \text{Minimum Value}$$

### Interquartile Range (IQR)

* **Meaning:** The difference between the 75th percentile ($Q_3$) and the 25th percentile ($Q_1$). It measures the spread of the middle 50% of the data. To avoid the sensitivity of the range to the outliers, estimate is based on differences between percentiles, range of the data after dropping values from each end.
* **Intuition:** Because it ignores the top 25% and bottom 25% of the data, the **IQR is robust to outliers**. It's a key component in defining box plots.
* **Formula:**
    $$\text{IQR} = Q_3 - Q_1$$

---

### Relationship Between Measures

The Standard Deviation (SD) is always greater than or equal to the Mean Absolute Deviation (MAD), which itself is always greater than or equal to the Median Absolute Deviation (MAD from the median).

$$\text{SD} \geq \text{MAD} \geq \text{Median Absolute Deviation}$$

### Percentile Calculation (Weighted Average Method)

This method involves determining the rank $j$ (the integer part) and the weight $w$ (the fractional part) based on the desired percentile $P$ and the total number of data points $n$.

### Determining the Rank Range

The rank $r$ for the $P$-th percentile is calculated as:
$$r = \frac{P}{100} (n-1) + 1$$
We then find the integer part of the rank, $j$, and the fractional part, $w$.

The formula you provided describes the relationship between the percentile $P$ and the rank $j$ as it relates to the sorted data:

$$\frac{100 \cdot j}{n} \leq P < \frac{100 \cdot (j+1)}{n}$$

* **Intuition:** This inequality defines the range where the $P$-th percentile falls between the $j$-th observation ($x_{(j)}$) and the $(j+1)$-th observation ($x_{(j+1)}$) in the sorted data.

### Percentile as a Weighted Average

The $P$-th percentile is then calculated as the weighted average of the $j$-th and the $(j+1)$-th sorted data values.

The provided weighted average formula, when using $x_{(j)}$ and $x_{(j+1)}$ as the $j$-th and $(j+1)$-th sorted observations, is:

$$\text{Percentile } P = (1 - w) x_{(j)} + w x_{(j+1)}$$

* **Where:**
    * $x_{(j)}$ is the $j$-th observation (the value at rank $j$) in the sorted data.
    * $x_{(j+1)}$ is the $(j+1)$-th observation (the value at rank $j+1$) in the sorted data.
    * $w$ is the fractional weight derived from the rank calculation.
    * **Intuition:** If the desired rank $r$ is exactly an integer ($w=0$), the percentile is simply $x_{(j)}$. If $r$ is exactly half-way between two ranks ($w=0.5$), it's the simple average of $x_{(j)}$ and $x_{(j+1)}$.

> **Note:** Different statistical software and textbooks may use slightly different interpolation methods (like R-1, R-2, R-6, R-7, etc.) to define the rank $r$ and the weighted average, but the structure provided above is a common, standard approach (often referred to as the R-7 method).

## 1.5 Exploring the Distribution

To fully understand a feature (column) in a dataset, we need to explore its **distribution**. This involves visualizing and summarizing how frequently different values or ranges of values occur.

---

### Boxplot (Box and Whisker Plot)

* **Meaning:** A standardized way of displaying the distribution of numerical data based on five key number summaries.
* **Intuition:** It visually summarizes the spread and skewness of the data and helps identify potential **outliers** at a glance.
* **Key Components:**
    * **Box:** Represents the Interquartile Range (**IQR**), containing the middle 50% of the data.
    * **Line inside the Box:** Represents the **Median** ($Q_2$, the 50th percentile).
    * **Edges of the Box:** The 25th percentile ($Q_1$) and the 75th percentile ($Q_3$).
    * **Whiskers:** Extend from the box to the farthest data points that are not considered outliers.
    * **Outliers:** Data points plotted individually beyond the whiskers.

---

### Frequency Table

* **Meaning:** A table that lists the distinct values (or bins/intervals) for a variable and the count (frequency) of how many times each value occurs.
* **Intuition:** Provides a raw, numerical summary of the distribution, especially useful for **categorical** or **discrete** data. Quartiles and Deciles will have the same count in each bin but the bin sizes are different.
* **Example (Ages):**

| Age Range (Bin) | Count (Frequency) | Relative Frequency |
| :--- | :--- | :--- |
| 20-29 | 15 | 0.30 (30%) |
| 30-39 | 25 | 0.50 (50%) |
| 40-49 | 10 | 0.20 (20%) |
| **Total** | **50** | **1.00 (100%)** |

---

### Histogram

* **Meaning:** A graphical representation of a frequency distribution for **numerical data**. It uses adjacent vertical bars (bins) to show the frequency of data points falling into specified intervals.
* **Intuition:** It provides the clearest visual picture of the **shape** of the distribution (e.g., normal, skewed right, bimodal). Unlike a bar chart, the area of the bar is proportional to the frequency, and there are no spaces between adjacent bars for continuous data.
* **Key Consideration:** The number and size of the **bins** significantly impact the appearance and interpretation of the histogram.

---

### Density Plot (Kernel Density Estimate - KDE)

* **Meaning:** A smoothing of the histogram, which estimates the probability density function of the data.
* **Intuition:** Provides a continuous, smooth curve to visualize the distribution, making it easier to identify the shape and central peaks (modes) without the rigid, blocky structure of a histogram. It is particularly effective for **comparing the distribution of multiple variables** on the same graph. Total area under the density curve is 1, area under the curve between any 2 points on the x-axis correspond to the proportion of the distribution lying between those two points.
* **Calculation:** It works by placing a small, smooth curve (the **kernel**) over each data point and then summing these curves to get a final smooth density estimate.

> **Note:** In statistical theory, location and variability are referred to as the first and second moments of a distribution. The third and fourth moments are skewness (refers to whether the data is skewed to larger or smaller values) and kurtosis (indicates propensity of the data to have extreme values). They are discovered through visualization and not a metric.

## 1.6 Exploring Categorical Data

* **Mode:** The most commonly occuring category or value in the dataset.

* **Expected Value:** The average value based on a probability of category's occurence when the categories can be associated with a numeric value. It is a form of weighted mean, in which weight are the probabilities. It adds the ideas of future expectations and probability weights, often based on subjective judgement.

* **Bar Charts:** The frequency or proportion for each category plotted as bars.

* **Pie Charts:** The frequency or proportion for each category plotted as wedges in a pie.

### Correlation

Examines correlation among predictors and between predictors and target variables. Variables X and Y are positively correlated if they both go up or go down, vice-versa negative correlation.

* **Correlation coefficient:** A metric that measures the extent to which numeric variables are associated with one another (ranges from -1 to +1). It is sensitive to outliers. sklearn.covariance implement different robust alternatives to the classical correlation coefficient.

* **Pearson's correlation coefficient**

$$
r = \frac{\sum_{i=1}^{n} (x_i - \bar{x})(y_i - \bar{y})}{(n - 1) s_x s_y}
$$

* **Correlation matrix:** A matrix with cell values are the correlations between the variables.

* **Scatter Plot:** A plot in which x-axis is the value of one variable and y-axis is the value of another.
