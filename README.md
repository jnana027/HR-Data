# HR DATA ANALYSIS - SQL SERVER 2024

This project dives deep into the realm of data analysis using SQL and Power BI to uncover important human resource insights that can greatly benefit the company. Featuring eye-catching dashboards offer crucial HR metrics like employee turnover, diversity, recruitment efficacy and performance evaluations. These help HR professionals make informed decisions and strategic workforce planning.

Source Data:

The source data contained Human Resource 22000 records from 2000 to 2020. This is included in the repository.

Data Cleaning & Analysis:

This was done on SQL server 2024 involving

Data loading & inspection

Handling missing values

Data cleaning and analysis

SELECT  [id]
      ,[first_name]
      ,[last_name]
      ,[birthdate]
      ,[gender]
      ,[race]
      ,[department]
      ,[jobtitle]
      ,[location]
      ,[hire_date]
      ,[termdate]
      ,[location_city]
      ,[location_state]
  FROM [My DataBase].[dbo].[HR]


  /*Data Cleaning and Transformation*/
---------------------------------------------------------------------------------------------------------
/*count all the rows*/

  select count(*) as total_rows from [My DataBase].[dbo].[HR]

select * from [My DataBase].[dbo].[HR]

/*check null value is there in any column */

select distinct(id) from [My DataBase].[dbo].[HR]

select count(distinct(id)) from [My DataBase].[dbo].[HR]

select first_name from [My DataBase].[dbo].[HR] where id is null

select distinct(first_name) from [My DataBase].[dbo].[HR]

select count(distinct(first_name)) from [My DataBase].[dbo].[HR]

select first_name from [My DataBase].[dbo].[HR] where first_name is null


select distinct(last_name) from [My DataBase].[dbo].[HR]

select count(distinct(last_name)) from [My DataBase].[dbo].[HR]

select last_name from [My DataBase].[dbo].[HR] where last_name is null


select distinct(birthdate) from [My DataBase].[dbo].[HR]

select count(distinct(birthdate)) from [My DataBase].[dbo].[HR]

select birthdate from [My DataBase].[dbo].[HR] where birthdate is null


select distinct(gender) from [My DataBase].[dbo].[HR]
select count(distinct(gender)) from [My DataBase].[dbo].[HR]
select gender from [My DataBase].[dbo].[HR] where gender is null

select distinct(race) from [My DataBase].[dbo].[HR]

select count(distinct(race)) from [My DataBase].[dbo].[HR]

select race from [My DataBase].[dbo].[HR] where race is null


select distinct(department) from [My DataBase].[dbo].[HR]

select count(distinct(department)) from [My DataBase].[dbo].[HR]

select department from [My DataBase].[dbo].[HR] where department is null


select distinct(jobtitle) from [My DataBase].[dbo].[HR]
select count(distinct(jobtitle)) from [My DataBase].[dbo].[HR]
select jobtitle from [My DataBase].[dbo].[HR] where jobtitle is null

select distinct(location) from [My DataBase].[dbo].[HR]

select count(distinct(location)) from [My DataBase].[dbo].[HR]

select location from [My DataBase].[dbo].[HR] where location is null


select distinct(hire_date) from [My DataBase].[dbo].[HR]

select count(distinct(hire_date)) from [My DataBase].[dbo].[HR]

select hire_date from [My DataBase].[dbo].[HR] where hire_date is null


select distinct(termdate) from [My DataBase].[dbo].[HR]

select count(distinct(termdate)) from [My DataBase].[dbo].[HR]

select termdate from [My DataBase].[dbo].[HR] where termdate is null

select count(*) from [My DataBase].[dbo].[HR] where termdate is null


select distinct(location_city) from [My DataBase].[dbo].[HR]

select count(distinct(location_city)) from [My DataBase].[dbo].[HR]

select location_city from [My DataBase].[dbo].[HR] where first_name is null


select distinct(location_state) from [My DataBase].[dbo].[HR]

select count(distinct(location_state)) from [My DataBase].[dbo].[HR]

select location_state from [My DataBase].[dbo].[HR] where first_name is null


/*To check the Data types*/

SELECT * FROM INFORMATION_SCHEMA.COLUMNS

select * from [My DataBase].[dbo].[HR]

/*Format the termdate column*/

select termdate from [My DataBase].[dbo].[HR] order by termdate desc

update [My DataBase].[dbo].[HR] set termdate=format(CONVERT(datetime,LEFT(termdate,19),120),'yyyy-MM-dd')

select * from [My DataBase].[dbo].[HR]

/* creating a new column name as "new_termdate" in HR table*/

alter table [My DataBase].[dbo].[HR] add new_termdate date;

/* copy converted time value from termdate to new_termdate*/

UPDATE [My DataBase].[dbo].[HR] SET
    new_termdate=case when termdate is not null and ISDATE(termdate)=1 then cast(termdate as datetime) else null end;

/*creating a new column age*/

alter table [My DataBase].[dbo].[HR] add age nvarchar(50);

---populate new column to hr

UPDATE [My DataBase].[dbo].[HR] SET
    age=DATEDIFF(year,birthdate,GETDATE())

    Exploratory Data Analysis
Questions:
What's the age distribution in the company?
What's the gender breakdown in the company?
How does gender vary across departments and job titles?
What's the race distribution in the company?
What's the average length of employment in the company?
Which department has the highest turnover rate?
What is the tenure distribution for each department?
How many employees work remotely for each department?
What's the distribution of employees across different states?
How are job titles distributed in the company?
How have employee hire counts varied over time?
Findings:
There are more male employees than female or non-conforming employees.
The genders are fairly evenly distributed across departments. There are slightly more male employees overall.
Employees 21-30 years old are the fewest in the company. Most employees are 31-50 years old. Surprisingly, the age group 50+ have the most employees in the company.
Caucasian employees are the majority in the company, followed by mixed race, black, Asian, Hispanic, and native Americans.
The average length of employment is 7 years.
Auditing has the highest turnover rate, followed by Legal, Research & Development and Training. Business Development & Marketing have the lowest turnover rates.
Employees tend to stay with the company for 6-8 years. Tenure is quite evenly distributed across departments.
About 25% of employees work remotely.
Most employees are in Ohio (14,788) followed distantly by Pennsylvania (930) and Illinois (730), Indiana (572), Michigan (569), Kentucky (375) and Wisconsin (321).
There are 182 job titles in the company, with Research Assistant II taking most of the employees (634) and Assistant Professor, Marketing Manager, Office Assistant IV, Associate Professor and VP of Training and Development taking the just 1 employee each.
Employee hire counts have increased over the years

