# 🧠 Analyze Death Age Difference of Right-Handers vs. Left-Handers

This project explores whether left-handed individuals truly die earlier than right-handed ones—a claim often circulated in pop science. By analyzing historical trends in handedness and death distributions, we apply Bayesian statistics to investigate whether apparent age differences can arise naturally from shifting societal patterns over time.

---

## 📁 Dataset

- **Handedness Data**: National Geographic Survey  
- **Death Distribution Data**: U.S. Census Bureau  
- [Download Dataset](https://drive.google.com/uc?export=download&id=1gSjYHJ8OPM9HMd3prr7XuhvSWWGKYZNE)

---

## 📌 Tasks Breakdown

### ✅ Task 1: Load & Visualize Handedness Data
- Load CSV using `pandas`
- Plot `"Male"` and `"Female"` handedness vs. `"Age"`

### ✅ Task 2: Birth Year & Mean Handedness
- Create `Birth_year = 1986 - Age`
- Create `Mean_lh = mean of Male & Female`
- Plot `Mean_lh` vs. `Birth_year`

### ✅ Task 3: Define P(LH | A)
- Use `numpy`
- Average last 10 rows → `early_1900s_rate`
- Average first 10 rows → `late_1900s_rate`
- Return handedness probability by age

### ✅ Task 4: Load Death Distribution Data
- Use `sep='\t'`, `skiprows=[1]`
- Drop NaNs from `"Both Sexes"`
- Plot deaths vs. age

### ✅ Task 5: Define P(LH)
- Multiply handedness probability with deaths by age
- Divide by total number of deaths

### ✅ Task 6: Define P(A | LH)
- Use Bayes’ Theorem
- P(A), P(LH), and P(LH | A) as inputs

### ✅ Task 7: Define P(A | RH)
- Similar to Task 6
- Use `P(RH) = 1 - P(LH)`, `P(RH | A) = 1 - P(LH | A)`

### ✅ Task 8: Plot Age at Death Distribution
- Plot `P_A_given_lh` and `P_A_given_rh` over a range of ages

### ✅ Task 9: Calculate Mean Age at Death
- Use `np.nansum(age * probability)`
- Output:
  - `average_lh_age`
  - `average_rh_age`
  - Difference

### ✅ Task 10: Repeat with 2018 Study Year
- Re-run Task 8 using `study_year = 2018`

---

## 🛠️ Tools Used

- Python 3.x
- pandas
- numpy
- matplotlib
- Bayesian probability

---

## 📈 Outcome

This analysis illustrates how changes in societal behavior (like increased acceptance of left-handedness) can confound data interpretation. The results may show that the "early death" myth is more a reflection of historical handedness bias than biological disadvantage.

---
