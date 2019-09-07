1. Write a SQL statement to create a simple table countries including columns country_id,country_name and region_id.

# create database countries;
# use countries;
# create table countries (country_id int, country_name varchar (25), region_id int);
# describe countries;


2. Write a SQL statement to create a simple table countries including columns country_id,country_name and region_id which is already exists.

# create table if not exists countries(country_id int
, country_name varchar (25), region_id int);

3. Write a SQL statement to create the structure of a table dup_countries similar to countries.

#create table dup_countries like countries;


4. Write a SQL statement to create a duplicate copy of countries table including structure and data by name dup_countries.

# create table if not exists  dup_countries As select * from countries;


5. Write a SQL statement to create a table countries set a constraint NOT NULL (all the fields should be not null).

# create table if not exists countries( country_id int NOT NULL,country_name varchar (25) NOT NULL,region_id int NOT NULL);

6. Write a SQL statement to create a table named jobs including columns job_id, job_title, min_salary, max_salary and check whether the max_salary amount exceeding the upper limit 25000.
 
# create table jobs (
    -> job_id int ,
    -> job_title varchar (25),
    -> min_salary int ,
    -> max_salary int,
    -> check (max_salary <=25000)
    -> );


 
7. Write a SQL statement to create a table named countries including columns country_id, country_name and region_id and make sure that no countries except Italy, India and China will be entered in the table.

#create table if not exists countries(
   -> country_id int,
   -> country_name varchar (25)
   -> check (country_name in ('Italy','India','Chain')),
   -> region_id int 
   -> );


8. Write a SQL statement to create a table named job_history including columns employee_id, start_date, end_date, job_id and department_id and make sure that the value against column end_date will be entered at the time of insertion to the format like '--/--/----'.

#create table job_history (
    -> employee_id int ,
    -> start_date date,
    -> end_date date
    -> CHECK (END_DATE LIKE '--/--/----'),
    -> job_id int,
    -> department_id int
    -> );


9. Write a SQL statement to create a table named countries including columns country_id,country_name and region_id and make sure that no duplicate data against column country_id will be allowed at the time of insertion.

#create table exists countries (
    -> country_id int not null unique,
    -> country_name varchar (25) not null,
    -> region_id int not null
    -> );

10. Write a SQL statement to create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.

#create table if not exists jobs (
    -> job_id int unique,
    -> job_title varchar(25) default ' ',
    -> min_salary int default 8000,
    -> max_salary int default NULL
    -> );



11. Write a SQL statement to create a table named countries including columns country_id, country_name and region_id and make sure that the country_id column will be a key field which will not contain any duplicate data at the time of insertion.

#create table if not exists countries (
    -> country_id int not null unique primary key,
    -> country_name varchar(25) not null,
    -> region_id int not null
    -> );



12. Write a SQL statement to create a table countries including columns country_id, country_name and region_id and make sure that the column country_id will be unique and store an auto incremented value.

#create table if not exists countries (
    -> country_id int not null unique primary key auto_increment,
    -> country_name varchar(25) not null,
    -> region_id int not null
    -> );


13. Write a SQL statement to create a table countries including columns country_id, country_name and region_id and make sure that the combination of columns country_id and region_id will be unique.

#create table if not exists countries(
    -> country_id int not null unique,
    -> country_name varchar(25) ,
    -> region_id int not null,
    -> primary key (country_id , region_id)
    -> );



14. Write a SQL statement to create a table job_history including columns employee_id, start_date, end_date, job_id and department_id and make sure that, the employee_id column does not contain any duplicate value at the time of insertion and the foreign key column job_id contain only those values which are exists in the jobs table.

Here is the structure of the table jobs;



| Field      | Type         | Null | Key | Default | Extra |
|------------|--------------|------|-----|---------|-------|
| JOB_ID     | varchar(10)  | NO   | PRI |         |       |
| JOB_TITLE  | varchar(35)  | NO   |     | NULL    |       |
| MIN_SALARY | decimal(6,0) | YES  |     | NULL    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |


#create table if not exists job_history(
    -> employee_id int NOT NULL primary key,
    -> start_date date NOT NULL ,
    -> end_date date NOT NULL,
    -> job_id varchar(10) NOT NULL,
    -> department_id int ,
    -> foreing key(job_id) references jobs(job_id)
    -> ) engine= innoDB;



15. Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, email, phone_number hire_date, job_id, salary, commission, manager_id and department_id and make sure that, the employee_id column does not contain any duplicate value at the time of insertion and the foreign key columns combined by department_id and manager_id columns contain only those unique combination values, which combinations are exists in the departments table.

Assume the structure of departments table below.

| Field           | Type         | Null | Key | Default | Extra |
|-----------------|--------------|------|-----|---------|-------|
| DEPARTMENT_ID   | decimal(4,0) | NO   | PRI | 0       |       |
| DEPARTMENT_NAME | varchar(30)  | NO   |     | NULL    |       |
| MANAGER_ID      | decimal(6,0) | NO   | PRI | 0       |       |
| LOCATION_ID     | decimal(4,0) | YES  |     | NULL    |       |

#create table departments(
    -> department_id decimal(4,0) NOT NULL default 0,
    -> department_name varchar(30) NOT NULL ,
    -> manager_id decimal(6,0) NOT NULL default 0,
    -> location_id decimal(4,0) default NULL,
    -> primary key(department_id , manager_id)
    -> );

# create table employees(
    -> employee_id int primary key not null,
    -> first_name varchar(25),
    -> last_name varchar(25),
    -> email varchar(25) not null,
    -> phone_number varchar(25) ,
    -> hire_date date not null,
    -> job_id varchar(25) not null,
    -> salary varchar(10) ,
    -> commission int ,
    -> manager_id int ,
    -> department_id int ,
    -> FOREING KEY (department_id ,manager_id)
    -> REFERENCES departments(department_id,manager_id)
    -> )ENGINE=InnoDB;


16. Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, email, phone_number hire_date, job_id, salary, commission, manager_id and department_id and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column department_id, reference by the column department_id of departments table, can contain only those values which are exists in the departments table and another foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The InnoDB Engine have been used to create the tables.

"A foreign key constraint is not required merely to join two tables. For storage engines other than InnoDB, it is possible when defining a column to use a REFERENCES tbl_name(col_name) clause, which has no actual effect, and serves only as a memo or comment to you that the column which you are currently defining is intended to refer to a column in another table." - Reference dev.mysql.com

Assume that the structure of two tables departments and jobs.

| Field           | Type         | Null | Key | Default | Extra |
|-----------------|--------------|------|-----|---------|-------|
| DEPARTMENT_ID   | decimal(4,0) | NO   | PRI | 0       |       |
| DEPARTMENT_NAME | varchar(30)  | NO   |     | NULL    |       |
| MANAGER_ID      | decimal(6,0) | YES  |     | NULL    |       |
| LOCATION_ID     | decimal(4,0) | YES  |     | NULL    |       |



| Field      | Type         | Null | Key | Default | Extra |
|------------|--------------|------|-----|---------|-------|
| JOB_ID     | varchar(10)  | NO   | PRI |         |       |
| JOB_TITLE  | varchar(35)  | NO   |     | NULL    |       |
| MIN_SALARY | decimal(6,0) | YES  |     | NULL    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |

#create table if not exists employees(
    -> employee_id int primary key not null,
    -> first_name varchar(25),
    -> last_name varchar(25),
    -> email varchar(25) not null,
    -> phone_number varchar(25) ,
    -> hire_date date not null,
    -> job_id varchar(25) not null,
    -> salary varchar(10) ,
    -> commission int ,
    -> department_id int ,
    -> FOREIGN KEY(department_id)
    -> REFERENCES departments(department_id),
    -> FOREIGN KEY(job_id)
    -> REFERENCES jobs(job_id)
    -> )ENGINE=InnoDB;


17. Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, job_id, salary and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The InnoDB Engine have been used to create the tables. The specialty of the statement is that, The ON UPDATE CASCADE action allows you to perform cross-table update and ON DELETE RESTRICT action reject the deletion. The default action is ON DELETE RESTRICT.

Assume that the structure of the table jobs and InnoDB Engine have been used to create the table jobs.

```CREATE TABLE IF NOT EXISTS jobs ( 
JOB_ID integer NOT NULL UNIQUE PRIMARY KEY, 
JOB_TITLE varchar(35) NOT NULL DEFAULT ' ', 
MIN_SALARY decimal(6,0) DEFAULT 8000, 
MAX_SALARY decimal(6,0) DEFAULT NULL
)ENGINE=InnoDB;
```



| Field      | Type         | Null | Key | Default | Extra |
|------------|--------------|------|-----|---------|-------|
| JOB_ID     | int(11)      | NO   | PRI | NULL    |       |
| JOB_TITLE  | varchar(35)  | NO   |     |         |       |
| MIN_SALARY | decimal(6,0) | YES  |     | 8000    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |

#create table if not exists employees(
    -> employee_id int primary key not null,
    -> first_name varchar(25),
    -> last_name varchar(25),
    -> email varchar(25) not null,
    -> phone_number varchar(25) ,
    -> hire_date date not null,
    -> job_id varchar(25) not null,
    -> salary varchar(10) ,
    -> commission int ,
    -> department_id int ,
    -> FOREIGN KEY(department_id)
    -> REFERENCES departments(department_id),
    -> FOREIGN KEY(job_id)
    -> REFERENCES jobs(job_id)
    -> )ENGINE=InnoDB;


18. Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, job_id, salary and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The InnoDB Engine have been used to create the tables. The specialty of the statement is that, The ON DELETE CASCADE that lets you allow to delete records in the employees(child) table that refer to a record in the jobs(parent) table when the record in the parent table is deleted and the ON UPDATE RESTRICT actions reject any updates.

Assume that the structure of the table jobs and InnoDB Engine have been used to create the table jobs.

```CREATE TABLE IF NOT EXISTS jobs ( 
JOB_ID integer NOT NULL UNIQUE PRIMARY KEY, 
JOB_TITLE varchar(35) NOT NULL DEFAULT ' ', 
MIN_SALARY decimal(6,0) DEFAULT 8000, 
MAX_SALARY decimal(6,0) DEFAULT NULL
)ENGINE=InnoDB;
```


| Field      | Type         | Null | Key | Default | Extra |
|------------|--------------|------|-----|---------|-------|
| JOB_ID     | int(11)      | NO   | PRI | NULL    |       |
| JOB_TITLE  | varchar(35)  | NO   |     |         |       |
| MIN_SALARY | decimal(6,0) | YES  |     | 8000    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |

#CREATE TABLE IF NOT EXISTS employees ( 
EMPLOYEE_ID decimal(6,0) NOT NULL PRIMARY KEY, 
FIRST_NAME varchar(20) DEFAULT NULL, 
LAST_NAME varchar(25) NOT NULL, 
JOB_ID INTEGER NOT NULL, 
SALARY decimal(8,2) DEFAULT NULL, 
FOREIGN KEY(JOB_ID) 
REFERENCES  jobs(JOB_ID) 
ON DELETE CASCADE ON UPDATE RESTRICT
)ENGINE=InnoDB;


19. Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, job_id, salary and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The InnoDB Engine have been used to create the tables. The specialty of the statement is that, The ON DELETE SET NULL action will set the foreign key column values in the child table(employees) to NULL when the record in the parent table(jobs) is deleted, with a condition that the foreign key column in the child table must accept NULL values and the ON UPDATE SET NULL action resets the values in the rows in the child table(employees) to NULL values when the rows in the parent table(jobs) are updated.

Assume that the structure of two table jobs and InnoDB Engine have been used to create the table jobs.

```CREATE TABLE IF NOT EXISTS jobs ( 
JOB_ID integer NOT NULL UNIQUE PRIMARY KEY, 
JOB_TITLE varchar(35) NOT NULL DEFAULT ' ', 
MIN_SALARY decimal(6,0) DEFAULT 8000, 
MAX_SALARY decimal(6,0) DEFAULT NULL
)ENGINE=InnoDB;
```



| Field      | Type         | Null | Key | Default | Extra |
|------------|--------------|------|-----|---------|-------|
| JOB_ID     | int(11)      | NO   | PRI | NULL    |       |
| JOB_TITLE  | varchar(35)  | NO   |     |         |       |
| MIN_SALARY | decimal(6,0) | YES  |     | 8000    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |

#CREATE TABLE IF NOT EXISTS employees ( 
EMPLOYEE_ID decimal(6,0) NOT NULL PRIMARY KEY, 
FIRST_NAME varchar(20) DEFAULT NULL, 
LAST_NAME varchar(25) NOT NULL, 
JOB_ID INTEGER, 
SALARY decimal(8,2) DEFAULT NULL, 
FOREIGN KEY(JOB_ID) 
REFERENCES  jobs(JOB_ID)
ON DELETE SET NULL 
ON UPDATE SET NULL
)ENGINE=InnoDB;

20. Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, job_id, salary and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The InnoDB Engine have been used to create the tables. The specialty of the statement is that, The ON DELETE NO ACTION and the ON UPDATE NO ACTION actions will reject the deletion and any updates.

Assume that the structure of two table jobs and InnoDB Engine have been used to create the table jobs.

```CREATE TABLE IF NOT EXISTS jobs ( 
JOB_ID integer NOT NULL UNIQUE PRIMARY KEY, 
JOB_TITLE varchar(35) NOT NULL DEFAULT ' ', 
MIN_SALARY decimal(6,0) DEFAULT 8000, 
MAX_SALARY decimal(6,0) DEFAULT NULL
)ENGINE=InnoDB;
```



| Field      | Type         | Null | Key | Default | Extra |
|------------|--------------|------|-----|---------|-------|
| JOB_ID     | int(11)      | NO   | PRI | NULL    |       |
| JOB_TITLE  | varchar(35)  | NO   |     |         |       |
| MIN_SALARY | decimal(6,0) | YES  |     | 8000    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |

#CREATE TABLE IF NOT EXISTS employees ( 
EMPLOYEE_ID decimal(6,0) NOT NULL PRIMARY KEY, 
FIRST_NAME varchar(20) DEFAULT NULL, 
LAST_NAME varchar(25) NOT NULL, 
JOB_ID INTEGER NOT NULL, 
SALARY decimal(8,2) DEFAULT NULL, 
FOREIGN KEY(JOB_ID) 
REFERENCES  jobs(JOB_ID)
ON DELETE NO ACTION 
ON UPDATE NO ACTION
)ENGINE=InnoDB;
