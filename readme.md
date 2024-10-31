Hello,

I am pleased that you are being assigned the project of "Analyze Death Age Difference of Right Handers with Left Handers." Review the following project proposal, which outlines the details of this project.



**Project Description**  
In this project, you will explore this phenomenon using age distribution data to see if we can reproduce a difference in average age at death purely from the changing rates of left-handedness over time, refuting the claim of early death for left-handers. This notebook uses pandas and Bayesian statistics to analyze the probability of being a certain age at death given that you are reported as left-handed or right-handed.

**Project Dataset**  
[Dataset Link](https://drive.google.com/uc?export=download&id=1gSjYHJ8OPM9HMd3prr7XuhvSWWGKYZNE)

**Task 1 Instructions**  
Load the handedness data from the National Geographic survey and create a scatter plot.
- Import `pandas` as `pd` and `matplotlib.pyplot` as `plt`.
- Load the data into a pandas DataFrame named `lefthanded_data` using the provided `data_url_1`. Note that the file is a CSV file.
- Use the `.plot()` method to create a plot of the "Male" and "Female" columns vs. "Age".

**Task 2 Instructions**  
Add two new columns, one for birth year and one for mean left-handedness, then plot the mean as a function of birth year.
- Create a column in `lefthanded_data` called `Birth_year`, which is equal to `1986 - Age` (since the study was done in 1986).
- Create a column in `lefthanded_data` called `Mean_lh` which is equal to the mean of the "Male" and "Female" columns.
- Use the `.plot()` method to plot `Mean_lh` vs. `Birth_year`.

**Task 3 Instructions**  
Create a function that will return P(LH | A) for particular ages of death in a given study year.
- Import the numpy package aliased as `np`.
- Use the last ten `Mean_lh` data points to get an average rate for the early 1900s. Name the resulting DataFrame `early_1900s_rate`.
- Use the first ten `Mean_lh` data points to get an average rate for the late 1900s. Name the resulting DataFrame `late_1900s_rate`.
- For the early 1900s ages, fill in `P_return` with the appropriate left-handedness rates for `ages_of_death`. Input `early_1900s_rate` as a fraction, i.e., divide by 100.
- For the late 1900s ages, fill in `P_return` with the appropriate left-handedness rates for `ages_of_death`. Input `late_1900s_rate` as a fraction, i.e., divide by 100.

**Task 4 Instructions**  
Load death distribution data for the United States and plot it.
- Load death distribution data in the provided `data_url_2` into `death_distribution_data`, setting `sep = '\t'` and `skiprows=[1]` to account for the dataset's format.
- Drop the NaN values from the "Both Sexes" column.
- Use the `.plot()` method to plot the number of people who died as a function of their age.

**Task 5 Instructions**  
Create a function called `P_lh()` which calculates the overall probability of left-handedness in the population for a given study year.
- Create a series, `p_list`, by multiplying the number of dead people in the "Both Sexes" column with the probability of their being left-handed using `P_lh_given_A()`.
- Set the variable `p` equal to the sum of that series.
- Divide `p` by the total number of dead people by summing `death_distribution_data` over the "Both Sexes" column. Return the result from the function.

P(LH | A) was defined in Task 3. N(A) is the value of "Both Sexes" in the `death_distribution_data` DataFrame where the "Age" column is equal to A. The denominator is the total number of dead people, which you can get by summing over the entire DataFrame in the "Both Sexes" column.

**Task 6 Instructions**  
Write a function to calculate `P_A_given_lh()`.
- Calculate `P_A`, the overall probability of dying at age A, which is given by `death_distribution_data` at age A divided by the total number of dead people (the sum of the "Both Sexes" column of `death_distribution_data`).
- Calculate the overall probability of left-handedness P(LH) using the function defined in Task 5.
- Calculate P(LH | A) using the function defined in Task 3.

**Task 7 Instructions**  
Write a function to calculate `P_A_given_rh()`.
- Calculate `P_A`, the overall probability of dying at age A, which is given by `death_distribution_data` at age A divided by the total number of dead people. (This value is the same as in Task 6.)
- Calculate the overall probability of right-handedness P(RH), which is `1 - P(LH)`.
- Calculate P(RH | A), which is `1 - P(LH | A)`.

**Task 8 Instructions**  
Plot the probability of being a certain age at death given that you're left- or right-handed for a range of ages.
- Calculate `P_A_given_lh` and `P_A_given_rh` using the functions defined in Task 6.
- Use the `.plot()` method to plot the results versus age.

**Task 9 Instructions**  
Find the mean age at death for left-handers and right-handers.
- Multiply the ages list by the left-handed probabilities of being those ages at death, then use `np.nansum` to calculate the sum. Assign the result to `average_lh_age`.
- Do the same with the right-handed probabilities to calculate `average_rh_age`.
- Print `average_lh_age` and `average_rh_age`.
- Calculate the difference between the two average ages and print it.

To make your printed output prettier, try using the `round()` function to round your results to two decimal places.

**Task 10 Instructions**  
Redo the calculation from Task 8, setting the `study_year` parameter to 2018.
- In the call to `P_A_given_lh`, set `age_of_death` to `ages`, `death_distribution_data` to `death_distribution_data`, and `study_year` to 2018.
- Do the same for `P_A_given_rh`.
