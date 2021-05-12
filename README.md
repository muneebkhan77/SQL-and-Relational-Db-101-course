# SQL-and-Relational-Db-101-course

# Code

CREATE TABLE EMPLOYEES (
                            EMP_ID CHAR(9) NOT NULL, 
                            F_NAME VARCHAR(15) NOT NULL,
                            L_NAME VARCHAR(15) NOT NULL,
                            SSN CHAR(9),
                            B_DATE DATE,
                            SEX CHAR,
                            ADDRESS VARCHAR(30),
                            JOB_ID CHAR(9),
                            SALARY DECIMAL(10,2),
                            MANAGER_ID CHAR(9),
                            DEP_ID CHAR(9) NOT NULL,
                            PRIMARY KEY (EMP_ID));
                            
  CREATE TABLE JOB_HISTORY (
                            EMPL_ID CHAR(9) NOT NULL, 
                            START_DATE DATE,
                            JOBS_ID CHAR(9) NOT NULL,
                            DEPT_ID CHAR(9),
                            PRIMARY KEY (EMPL_ID,JOBS_ID));
 
 CREATE TABLE JOBS (
                            JOB_IDENT CHAR(9) NOT NULL, 
                            JOB_TITLE VARCHAR(15) ,
                            MIN_SALARY DECIMAL(10,2),
                            MAX_SALARY DECIMAL(10,2),
                            PRIMARY KEY (JOB_IDENT));

CREATE TABLE DEPARTMENTS (
                            DEPT_ID_DEP CHAR(9) NOT NULL, 
                            DEP_NAME VARCHAR(15) ,
                            MANAGER_ID CHAR(9),
                            LOC_ID CHAR(9),
                            PRIMARY KEY (DEPT_ID_DEP));

CREATE TABLE LOCATIONS (
                            LOCT_ID CHAR(9) NOT NULL,
                            DEP_ID_LOC CHAR(9) NOT NULL,
                            PRIMARY KEY (LOCT_ID,DEP_ID_LOC));
                            
      
   
SELECT * FROM  EMPLOYEES             
WHERE  ADDRESS LIKE '%Elgin,IL';             

SELECT  F_NAME,L_NAME FROM EMPLOYEES 
WHERE B_DATE  LIKE '197%';


SELECT * FROM EMPLOYEES
WHERE DEP_ID = 5 AND
( SALARY  BETWEEN 60000 AND 70000) ;


SELECT * FROM EMPLOYEES 
ORDER BY DEP_ID ;

SELECT * FROM EMPLOYEES 
ORDER  BY  DEP_ID DESC,  L_NAME DESC ;
        
 SELECT DEP_ID, COUNT(*) AS num_employees, AVG( SALARY) as avg_salary FROM EMPLOYEES
 GROUP BY DEP_ID HAVING COUNT(*) < 4 AND AVG(SALARY) >66667 ORDER BY avg_salary  ;
