# SF-Salaries
Case Study of SF Salaries (San Francisco city employees salary data)

**About Dataset**
One way to understand how a city government works is by looking at who it employs and how its employees are compensated. This data contains the names, job title, and compensation for San Francisco city employees on an annual basis from 2011 to 2014.

**Data Used**
**Data** - SF Salary Data with over 5000 rows from the year 2011 to 2014.

**Data Cleaning & Analysis** - MySQL Workbench

----------------------------------
|Column              |Description |
----------------------------------
|Id	                 |int         |
|EmployeeName	       |Varchar(50) |
|JobTitle	           |Varchar(50) |
|BasePay	           |double      |
|OvertimePay	       |double      |
|OtherPay	           |double      |
|Benefits	           |Varchar(50) |
|TotalPay	           |double      |
|TotalPayBenefits    |double      |
|Year	               |int         |
|Notes	             |Varchar(50) |
|Agency	             |Varchar(50) |
|Status	             |Varchar(50) |
----------------------------------

**Data Wrangling :** This is the first step where inspection of data is done to make sure **Null** values and missing values are detected and there is no **Null** or missing values are dedected in the data.

       1. Build a Database
       2. Create table and insert data.
       3. Select columns with null values in them. There are no null values in our database as in creating the table, we set NOT NULL for each field, hence null values are filtered out.

**Exploratory Data Analysis(EDA):** Exploratory data analysis is done to answer the listed questions and aims of this project.

1. How many number if employees does the data have?
Query : Select count(*) from salaries;
Ans : 5000 employees in the dataset.

2. How many job titles does the data have?
Query : Select count(distinct jobtitle) from salaries;
Ans : 269.

3. Identify the jobtitle and overtimepay for all employees with overtime pay greater than 50000.
Query : Select jobtitle, overtimepay from salaries 
where overtimepay > 50000;

4. What is the average basepay for all employees?
Query : Select avg(Basepay) as "Avg_Basepay" from salaries;
Ans : 125819.71565799965

5. Identify the top 10 highest paid employess?
Query : Select employeename, totalpay from salaries
        orderr by totalpay desc
        limit 10;
Ans : 
NATHANIEL FORD	   567595.43
GARY JIMENEZ	   538909.28
ALBERT PARDINI	   335279.91
CHRISTOPHER CHONG  332343.61
PATRICK GARDNER	   326373.19
DAVID SULLIVAN	   316285.74
ALSON LEE	   315981.05
DAVID KUSHNER	   307899.46
MICHAEL MORRIS	   303427.55
JOANNE HAYES-WHITE 302377.73

6. What is average of basepay, overtimepay and & otherpay for each employee?
Query : Select employeename, (basepay+otherpay+totalpay)/3 as "Avg_pay" from salaries;

7. Find out the employees who have the word "Manager" in theri job title?
Query : Select employeename, jobtitle from salaries
where jobtitle like '%manager%';

8. Find out the employees who don't have the word "Manager" in theri job title?
Query : Select employeename, jobtitle from salaries
where jobtitle <> 'manager';

9. Select all employees with a totalpay between 50,000 & 75,000;
Query : Select employeename, totalpay from salaries
where totalpay between 50000 and 75000;

10. Select all employees with a basepay less than 50000 or a totalpay greater than 100000;
Query : Select * from salaries;
        where basepay < 50000 or totalpay > 100000;

11. Select all employees with a totalpay benifits value between 125000 and 150000 and a 
jobtitle containing the word "Director"
Query : Select * from salaries
where totalpaybenifits between 125000 and 150000 and jobtitle like '%Director%';

12. Show all employees ordered by their totalpay benifits in descending order;
Query : Select * from salaries order by totalpaybenifits desc;

13. delete the column status;
Alter table salaries drop column status;

14. Update the basepay of all employees with the job title containing "Manager" by 
increasing it by 10%.
Update salaries
set basepay = basepay*1.1
where jobtitle like '%Manager%';

15. Delete all employees who have no overtimepay;
Delete from salaries
where overtimepay = 0;

----------------------------------------------------------------------------------------------------------------
