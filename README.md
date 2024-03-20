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

