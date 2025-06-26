# Two-Sample t-Test: Beginner-Friendly Notes with Analogies & Code Examples

---

## 1. What is a Two-Sample t-Test?

A **Two-Sample t-Test** compares the **means of two independent groups** to determine if they are **statistically different** from each other.

### Real-World Analogy:

Imagine you have two teachers: Mr. A and Ms. B. Each has a class of students. You want to know if **Mr. A's teaching leads to higher average scores** than Ms. B's.

This is a **two-sample t-test**: comparing two sample means to check if any observed difference is likely real — or just due to chance.

---

## 2. When to Use It?

Use the **two-sample t-test** when:

* You have **two independent groups** (e.g., Group A and Group B)
* You want to **compare their means**
* Data is approximately **normally distributed**
* Variances are **equal** (for the standard t-test; Welch's t-test is for unequal variances)

---

## 3. Formula for Two-Sample t-Test

For equal variances:

```math
 t = \frac{\bar{X}_1 - \bar{X}_2}{\sqrt{s_p^2 \left(\frac{1}{n_1} + \frac{1}{n_2}\right)}}
```

Where:

* $\bar{X}_1, \bar{X}_2$ are the sample means
* $n_1, n_2$ are sample sizes
* $s_p^2$ is the pooled variance

```math
 s_p^2 = \frac{(n_1 - 1)s_1^2 + (n_2 - 1)s_2^2}{n_1 + n_2 - 2}
```

You compare the **t-statistic** to a **critical value** from the **t-distribution table** or calculate the **p-value**.

---

## 4. Example 1: Comparing Exam Scores (Equal Variance)

```python
import scipy.stats as stats

# Scores of students taught by two different teachers
group_A = [88, 90, 92, 85, 87]
group_B = [82, 84, 86, 80, 83]

# Perform two-sample t-test (assume equal variances)
t_stat, p_value = stats.ttest_ind(group_A, group_B, equal_var=True)
print("t-statistic:", t_stat)
print("p-value:", p_value)
```

---

## 5. Example 2: Testing Drug Effectiveness

Group 1 takes **Drug A**, Group 2 takes **Drug B**. Is there a difference in recovery time?

```python
drug_A = [7, 9, 6, 8, 10]
drug_B = [5, 6, 4, 6, 5]

t_stat, p_value = stats.ttest_ind(drug_A, drug_B, equal_var=True)
print("t-statistic:", t_stat)
print("p-value:", p_value)
```

---

## 6. Example 3: Comparing Salaries

```python
male_salaries = [50000, 52000, 51000, 53000, 49000]
female_salaries = [47000, 46000, 48000, 45000, 49000]

t_stat, p_value = stats.ttest_ind(male_salaries, female_salaries, equal_var=False)
print("Welch t-statistic:", t_stat)
print("p-value:", p_value)
```

---

## 7. Example 4: Sports Performance

Basketball players from Team A vs Team B:

```python
team_A = [18, 20, 22, 19, 21]
team_B = [15, 14, 17, 16, 15]

t_stat, p_value = stats.ttest_ind(team_A, team_B, equal_var=True)
print("t-statistic:", t_stat)
print("p-value:", p_value)
```

---

## 8. Example 5: Website A/B Testing

Group A sees **Version 1** of a webpage; Group B sees **Version 2**. We measure time spent on the page.

```python
version_1 = [120, 130, 115, 140, 110]
version_2 = [100, 95, 105, 98, 102]

t_stat, p_value = stats.ttest_ind(version_1, version_2)
print("t-statistic:", t_stat)
print("p-value:", p_value)
```

---

## 9. How to Interpret Results

* **p-value < 0.05**: Statistically significant → groups are **different**
* **p-value ≥ 0.05**: Not significant → groups are **similar** (no strong evidence they're different)

---

## 10. Final Analogy Recap:

> A two-sample t-test is like a **referee** checking if two runners had **significantly different speeds**, or if the gap between them was just **normal race randomness**.

It helps you make **data-driven decisions** when comparing groups.
