# HR Project - SQL intern Psyliq


1. Retrieve the total number of employees in the dataset.
``` SQL
Select  COUNT (EmployeeID) as Total_Employees
From hr; 
```
2. List all unique job roles in the dataset.
``` SQL
Select  DISTINCT (JobRole) 
From hr; 
```
3. Find the average age of employees. 
``` SQL
SELECT ROUND(AVG(Age)) as AVG_Age
FROM hr;
```
4. Retrieve the names and ages of employees who have worked at the company for more than 5 years.
``` SQL
SELECT Emp_Name, Age
FROM hr
WHERE YearsAtCompany > 5;
```
5. Get a count of employees grouped by their department.
``` SQL
SELECT Department, COUNT(EmployeeID) as Number_of_Employees
FROM hr
Group by Department
```
6. List employees who have 'High' Job Satisfaction. 
``` SQL
SELECT Emp_Name, JobSatisfaction
FROM hr
INNER JOIN survey ON hr.EmployeeID = survey.EmployeeID
WHERE survey.JobSatisfaction >= 4;
```
7. Find the highest Monthly Income in the dataset.
``` SQL
SELECT  max(MonthlyIncome) as Highest_Income
FROM hr ;
```
8. List employees who have 'Travel_Rarely' as their BusinessTravel type.
``` SQL
SELECT Emp_Name, BusinessTravel
FROM hr
WHERE BusinessTravel like 'Travel_Rarely';
```
9. Retrieve the distinct MaritalStatus categories in the dataset.
``` SQL
SELECT DISTINCT MaritalStatus
FROM hr;
```
10. Get a list of employees with more than 2 years of work experience but less than 4 years in their current role.
``` SQL
SELECT  Emp_Name, TotalWorkingYears
FROM hr
WHERE TotalWorkingYears > 2 and TotalWorkingYears < 4;
```
11. List employees who have changed their job roles within the company (JobLevel and JobRole differ from their previous job).
``` SQL
SELECT Emp_Name, JobRole
FROM hr 
Group By JobRole
Having count(Emp_Name)>1 ;
```
12. Find the average distance from home for employees in each department.
``` SQL
SELECT Department, AVG(DistanceFromHome) as Avg_Distance
FROM hr 
Group By Department ;
```
13. Retrieve the top 5 employees with the highest MonthlyIncome. 
``` SQL
SELECT Emp_Name, MonthlyIncome
FROM hr
ORDER by MonthlyIncome DESC
LIMIT 5;
```
14. Calculate the percentage of employees who have had a promotion in the last year. 
``` SQL
SELECT SUM(YearsSinceLastPromotion=1)*100/count(*) as 
FROM hr;
```
15. List the employees with the highest and lowest EnvironmentSatisfaction.  
``` SQL
SELECT
  hr.Emp_Name,
  survey.EnvironmentSatisfaction,
  CASE survey.EnvironmentSatisfaction
    WHEN 0 THEN 'Lowest'
    WHEN 4 THEN 'Highest'
    ELSE 'Other'
  END AS SatisfactionLevel
FROM hr
INNER JOIN survey ON hr.EmployeeID = survey.EmployeeID
WHERE survey.EnvironmentSatisfaction IN (0, 4);
```
16. Find the employees who have the same JobRole and MaritalStatus. 
``` SQL
SELECT hr.JobRole, hr.MaritalStatus
FROM hr
Group by JobRole, MaritalStatus;
```
17. List the employees with the highest TotalWorkingYears who also have a PerformanceRating of 4. 
``` SQL
SELECT Emp_Name, PerformanceRating, TotalWorkingYears 
FROM hr inner join manager on hr.EmployeeID=manager.EmployeeID
Where PerformanceRating=4;
```
18. Calculate the average Age and JobSatisfaction for each BusinessTravel type.  
``` SQL
SELECT round(avg(Age)) as AvgAge, round(avg(JobSatisfaction)) as AvgJobSatisfaction, BusinessTravel 
FROM hr inner join survey on hr.EmployeeID=survey.EmployeeID
Group by BusinessTravel;
```
19. Retrieve the most common EducationField among employees. 
``` SQL
SELECT  EducationField, 
count(*) as TotalCount
From hr
Group by EducationField 
Order by TotalCount DESC
LIMIT 1;
```
20. List the employees who have worked for the company the longest but haven't had a promotion. 
``` SQL
SELECT  Emp_Name, YearsAtCompany
From hr
Where YearsSinceLastPromotion = 0
Order by YearsAtCompany DESC ;
```
