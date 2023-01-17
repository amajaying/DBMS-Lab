# Step 1
connect c21053264<br>
kiit

`Connected.`

# Step 2: Creating Tables

CREATE TABLE salary(empid VARCHAR(10),  salary INT, depy VARCHAR(15), branch VARCHAR(20));
<br>
Table Created;

# Step 3: Describing Tables

DESC salary;

# Step 4: Insert Data

INSERT INTO student VALUES(21053264,'Ajay', 'Khatri', 'CSE', '15/JAN/2003', 'M', 'Hindu');

# Step 5: Displaying Table

To display in a line: 'set linesize 500`

SELECT * FROM student;

To save all the code in the drive, run:

`spool "A:\4th Sem Labs\DBMS-Lab\Lab 1\Saved\lab1output.txt";`

To end saving the code, run:
`spool off;`
