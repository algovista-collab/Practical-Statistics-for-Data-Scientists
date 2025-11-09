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
