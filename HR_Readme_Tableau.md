# HR Attrition Analysis - Adecco (Tableau)

This is my Tableau project for the Jobaaj case study **DACS12 - Adecco HR Analytics**.

The company is losing a lot of junior staff, especially in Sales, and HR wants to know why. I used the employee dataset to look at who is leaving, what they have in common, and what the company could do about it.

## Files

- `HR_Analysis.twbx` - the Tableau workbook (packaged, so the data is inside it)
- `Adecco_HR_Analysis_Project Tableau.xlsx` - the raw data
- `DACS12 - Adecco HR Analytics.docx` - the case study brief with all the questions

To open it, double-click `HR_Analysis.twbx` in Tableau Desktop or Tableau Public. You don't need to connect the Excel file separately.

## About the data

- 1,470 employees, 35 columns (age, department, job role, income, overtime, satisfaction scores, years at company etc.)
- `Attrition` = Yes means the employee has left
- No missing values and no duplicate employee numbers, so no imputation was needed

What I did before starting the questions:

- Left out `EmployeeCount`, `Over18` and `StandardHours` because they have the same value for everyone
- Renamed the columns so they read properly (MonthlyIncome -> Monthly Income etc.)
- Added aliases to the 1-4 rating columns (1 = Low, 4 = Very High) and Education (1 = Below College ... 5 = Doctor)
- Changed some number fields to dimensions where it made sense (Job Level, Stock Option Level, ratings)
- Made groups for Age, Tenure, Income, Distance from Home and Years Since Last Promotion
- Sorted the fields into folders

## Main calculated fields

- **Attrition Flag** - 1 if the employee left, 0 if not. Most of the other calculations use this.
- **Total Employees** - count of employee numbers
- **Employees Left** - sum of Attrition Flag
- **Attrition Rate %** - Employees Left / Total Employees
- **Company Attrition %** - same thing but with FIXED, so it stays at the company level. I used it for the reference lines.
- **r (factor)** fields - CORR() between Attrition Flag and each factor, for Medium Q1
- **T Statistic** - to check if the gender difference is significant (Basic Q5)

## Dashboards

**1. Overview** - attrition rate, average age and income of leavers, overtime count and average tenure, plus attrition by department and gender. Clicking a department or gender bar filters the rest of the page. There is also a Job Level filter.

**2. Attrition Drivers** - the top factors linked to attrition and attrition rate by job involvement, marital status, stock options, training and distance from home. Department filter.

**3. Job Satisfaction** - satisfaction by job role, age, years at company and business travel. Department filter.

**4. Performance** - performance rating split, and ratings against work-life balance and promotion gap. Department filter.

Use the Back / Next buttons at the top to move between the dashboards.

## Answers

Basic questions

| # | Question | Answer |
|---|---|---|
| 1 | Overall attrition rate | 16.12% (237 of 1,470) |
| 2 | Department with highest attrition | Sales, 20.63% |
| 3 | Average age of employees who left | 33.6 years |
| 4 | Job satisfaction by role | Healthcare Rep highest (2.79), HR lowest (2.56) |
| 5 | Attrition by gender | Male 17.0%, Female 14.8%. Not significant (p around 0.25) |
| 6 | Average monthly income of leavers | $4,787 |
| 7 | Distance from home vs attrition | Small positive link, very weak (R-squared 0.006) |
| 8 | Performance rating split | 84.6% rated 3, 15.4% rated 4 |
| 9 | Employees working overtime | 416 (28.3%) |
| 10 | Average years at company | 7.0 years |

Medium questions

| # | Question | Answer |
|---|---|---|
| 1 | Top 3 factors linked to attrition | Overtime, Total Working Years, Job Level |
| 2 | Job involvement vs attrition | Low involvement 33.7%, Very High 9.0% |
| 3 | Age vs job satisfaction | No relationship |
| 4 | Marital status | Single employees leave most (25.5%) |
| 5 | Training vs attrition | No training 27.8%, 6 sessions 9.2% |
| 6 | Work-life balance vs performance | No relationship |
| 7 | Stock options vs attrition | No stock options 24.4%, highest |
| 8 | Years at company vs satisfaction | No relationship |
| 9 | Business travel | Satisfaction is about the same, but frequent travellers leave 24.9% vs 8.0% for non travellers |
| 10 | Promotion gap vs performance | No relationship |

## What I found

- About 1 in 6 employees has left. Sales is the worst department.
- Junior Sales Representatives (Job Level 1) are the biggest problem: 32 out of 76 have left, which is 42%. For the ones working overtime it goes up to 73%.
- People who leave are younger, earn around 30% less and are more likely to work overtime, be single, have no stock options and have had little training.
- Satisfaction scores don't explain much on their own. Frequent travellers are just as satisfied as everyone else but still leave three times more.
- Performance ratings are only ever 3 or 4, so they can't really be used to spot who might leave.

## Suggestions for HR

1. Cut down overtime for junior Sales staff
2. Look at starting salaries for junior roles
3. Give stock options from entry level
4. Make sure new joiners get proper training in their first year
5. Reduce frequent travel or give extra support to people who travel a lot
6. Fix the rating system so it actually separates performance levels

## Limitations

- The dataset is a sample HR dataset, not real Adecco data
- Correlation doesn't mean one thing causes the other
- It's a single snapshot, so there's no way to see trends over time

---
Made by: Manisha Mali - Jobaaj Data Analytics course
