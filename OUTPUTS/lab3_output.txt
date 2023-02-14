SQL> CREATE TABLE emp12(empid INT PRIMARY KEY, empname VARCHAR(20) NOT NULL, phno NUMBER(10) UNIQUE, age NUMBER(3) CHECK (age>=18), emp_country VARCHAR(20) DEFAULT 'India');

Table created.

SQL> INSERT INTO emp12 VALUES(&empid, '&empname
  2  ', &phno, &age, '&emp_country');
Enter value for empid: 112
Enter value for empname: Michael
old   1: INSERT INTO emp12 VALUES(&empid, '&empname
new   1: INSERT INTO emp12 VALUES(112, 'Michael
Enter value for phno: 234
Enter value for age: 19
Enter value for emp_country: Russia
old   2: ', &phno, &age, '&emp_country')
new   2: ', 234, 19, 'Russia')

1 row created.

SQL> INSERT INTO emp12 VALUES(&empid, '&empname', &phno, &age, '&emp_country');
Enter value for empid: 113
Enter value for empname: Abdul
Enter value for phno: 913
Enter value for age: 25
Enter value for emp_country: 
old   1: INSERT INTO emp12 VALUES(&empid, '&empname', &phno, &age, '&emp_country')
new   1: INSERT INTO emp12 VALUES(113, 'Abdul', 913, 25, '')

1 row created.

SQL> /
Enter value for empid: 131
Enter value for empname: 
Enter value for phno: 678
Enter value for age: 43
Enter value for emp_country: USA
old   1: INSERT INTO emp12 VALUES(&empid, '&empname', &phno, &age, '&emp_country')
new   1: INSERT INTO emp12 VALUES(131, '', 678, 43, 'USA')
INSERT INTO emp12 VALUES(131, '', 678, 43, 'USA')
                              *
ERROR at line 1:
ORA-01400: cannot insert NULL into ("C21053264"."EMP12"."EMPNAME") 


SQL> /
Enter value for empid: 132
Enter value for empname: Riya
Enter value for phno: 234
Enter value for age: 22
Enter value for emp_country: India
old   1: INSERT INTO emp12 VALUES(&empid, '&empname', &phno, &age, '&emp_country')
new   1: INSERT INTO emp12 VALUES(132, 'Riya', 234, 22, 'India')
INSERT INTO emp12 VALUES(132, 'Riya', 234, 22, 'India')
*
ERROR at line 1:
ORA-00001: unique constraint (C21053264.SYS_C007130) violated 


SQL> /
Enter value for empid: 113
Enter value for empname: Lily
Enter value for phno: 876
Enter value for age: 60
Enter value for emp_country: UK
old   1: INSERT INTO emp12 VALUES(&empid, '&empname', &phno, &age, '&emp_country')
new   1: INSERT INTO emp12 VALUES(113, 'Lily', 876, 60, 'UK')
INSERT INTO emp12 VALUES(113, 'Lily', 876, 60, 'UK')
*
ERROR at line 1:
ORA-00001: unique constraint (C21053264.SYS_C007129) violated 


SQL> /
Enter value for empid: 127
Enter value for empname: Dino
Enter value for phno: 777
Enter value for age: 17
Enter value for emp_country: Italy
old   1: INSERT INTO emp12 VALUES(&empid, '&empname', &phno, &age, '&emp_country')
new   1: INSERT INTO emp12 VALUES(127, 'Dino', 777, 17, 'Italy')
INSERT INTO emp12 VALUES(127, 'Dino', 777, 17, 'Italy')
*
ERROR at line 1:
ORA-02290: check constraint (C21053264.SYS_C007128) violated 


SQL> /
Enter value for empid: 117
Enter value for empname: Indira
Enter value for phno: 676
Enter value for age: 
Enter value for emp_country: 
old   1: INSERT INTO emp12 VALUES(&empid, '&empname', &phno, &age, '&emp_country')
new   1: INSERT INTO emp12 VALUES(117, 'Indira', 676, , '')
INSERT INTO emp12 VALUES(117, 'Indira', 676, , '')
                                             *
ERROR at line 1:
ORA-00936: missing expression 


SQL> ALTER TABLE emp12 DROP CONSTRAINT age;
ALTER TABLE emp12 DROP CONSTRAINT age
                                  *
ERROR at line 1:
ORA-02443: Cannot drop constraint  - nonexistent constraint 


SQL> ALTER TABLE emp12 DROP CHECK age;
ALTER TABLE emp12 DROP CHECK age
                       *
ERROR at line 1:
ORA-00905: missing keyword 


SQL> DESC emp12
 Name                                      Null?    Type
 ----------------------------------------- -------- ----------------------------
 EMPID                                     NOT NULL NUMBER(38)
 EMPNAME                                   NOT NULL VARCHAR2(20)
 PHNO                                               NUMBER(10)
 AGE                                                NUMBER(3)
 EMP_COUNTRY                                        VARCHAR2(20)

SQL> /
ALTER TABLE emp12 DROP CHECK age
                       *
ERROR at line 1:
ORA-00905: missing keyword 


SQL> INSERT INTO emp12 VALUES(&empid, '&empname', &phno, &age, '&emp_country');
Enter value for empid: 
Enter value for empname: 
Enter value for phno: 
Enter value for age: 12
Enter value for emp_country: 
old   1: INSERT INTO emp12 VALUES(&empid, '&empname', &phno, &age, '&emp_country')
new   1: INSERT INTO emp12 VALUES(, '', , 12, '')
INSERT INTO emp12 VALUES(, '', , 12, '')
                         *
ERROR at line 1:
ORA-00936: missing expression 


SQL> /
Enter value for empid: 114
Enter value for empname: Raj
Enter value for phno: 238
Enter value for age: 54
Enter value for emp_country: USA
old   1: INSERT INTO emp12 VALUES(&empid, '&empname', &phno, &age, '&emp_country')
new   1: INSERT INTO emp12 VALUES(114, 'Raj', 238, 54, 'USA')

1 row created.

SQL> /
Enter value for empid: 115
Enter value for empname: Abhay
Enter value for phno: 222
Enter value for age: 
Enter value for emp_country: 
old   1: INSERT INTO emp12 VALUES(&empid, '&empname', &phno, &age, '&emp_country')
new   1: INSERT INTO emp12 VALUES(115, 'Abhay', 222, , '')
INSERT INTO emp12 VALUES(115, 'Abhay', 222, , '')
                                            *
ERROR at line 1:
ORA-00936: missing expression 


SQL> ALTER TABLE emp12 ADD CONSTRAINT check_age CHECK (age>=18 AND age<=70);

Table altered.

SQL> SELECT * FROM emp12;

     EMPID EMPNAME                    PHNO        AGE EMP_COUNTRY               
---------- -------------------- ---------- ---------- --------------------      
       112 Michael                     234         19 Russia                    
       113 Abdul                       913         25                           
       114 Raj                         238         54 USA                       

SQL> CREATE TABLE projectx(pid NUMBER c1 PRIMARY KEY, pname VARCHAR(20) c2 PRIMARY KEY, phead NUMBER uc_px_34 UNIQUe, ploc uc_px_34 UNIQUE, pmembers NUMBER DEFAULT 5 CONSTRAINT ck_px_5 (pmembers<=5));
CREATE TABLE projectx(pid NUMBER c1 PRIMARY KEY, pname VARCHAR(20) c2 PRIMARY KEY, phead NUMBER uc_px_34 UNIQUe, ploc uc_px_34 UNIQUE, pmembers NUMBER DEFAULT 5 CONSTRAINT ck_px_5 (pmembers<=5))
                                 *
ERROR at line 1:
ORA-00907: missing right parenthesis 


SQL> CREATE TABLE projectx(pid NUMBER CONSTRAINT c1 PRIMARY KEY, pname VARCHAR(20) CONSTRAINT c2 PRIMARY KEY, phead NUMBER CONSTRAINT uc_px_34 UNIQUe, ploc CONSTRAINT uc_px_34 UNIQUE, pmembers NUMBER DEFAULT 5 CONSTRAINT ck_px_5 (pmembers<=5));
CREATE TABLE projectx(pid NUMBER CONSTRAINT c1 PRIMARY KEY, pname VARCHAR(20) CONSTRAINT c2 PRIMARY KEY, phead NUMBER CONSTRAINT uc_px_34 UNIQUe, ploc CONSTRAINT uc_px_34 UNIQUE, pmembers NUMBER DEFAULT 5 CONSTRAINT ck_px_5 (pmembers<=5))
                                                                              *
ERROR at line 1:
ORA-02260: table can have only one primary key 


SQL> CREATE TABLE projectx(pid NUMBER, pname VARCHAR(20), phead NUMBER CONSTRAINT uc_px_34 UNIQUe, ploc CONSTRAINT uc_px_34 UNIQUE, pmembers NUMBER DEFAULT 5 CONSTRAINT ck_px_5 (pmembers<=5), CONSTRAINT primary_chk PRIMARY KEY (pid,pname));
CREATE TABLE projectx(pid NUMBER, pname VARCHAR(20), phead NUMBER CONSTRAINT uc_px_34 UNIQUe, ploc CONSTRAINT uc_px_34 UNIQUE, pmembers NUMBER DEFAULT 5 CONSTRAINT ck_px_5 (pmembers<=5), CONSTRAINT primary_chk PRIMARY KEY (pid,pname))
                                                                                                                                                         *
ERROR at line 1:
ORA-02253: constraint specification not allowed here 


SQL> CREATE TABLE projectx(pid NUMBER CONSTRAINT c1 PRIMARY KEY, pname VARCHAR(20) CONSTRAINT c1 PRIMARY KEY, phead NUMBER CONSTRAINT uc_px_34 UNIQUe, ploc CONSTRAINT uc_px_34 UNIQUE, pmembers NUMBER DEFAULT 5 CONSTRAINT ck_px_5 (pmembers<=5));
CREATE TABLE projectx(pid NUMBER CONSTRAINT c1 PRIMARY KEY, pname VARCHAR(20) CONSTRAINT c1 PRIMARY KEY, phead NUMBER CONSTRAINT uc_px_34 UNIQUe, ploc CONSTRAINT uc_px_34 UNIQUE, pmembers NUMBER DEFAULT 5 CONSTRAINT ck_px_5 (pmembers<=5))
                                                                              *
ERROR at line 1:
ORA-02260: table can have only one primary key 


SQL> CREATE TABLE projectx(pid NUMBER, pname VARCHAR(20), CONSTRAINT c1 PRIMARY KEY(pid, pname), phead NUMBER CONSTRAINT uc_px_34 UNIQUe, ploc CONSTRAINT uc_px_34 UNIQUE, pmembers NUMBER DEFAULT 5 CONSTRAINT ck_px_5 (pmembers<=5));
CREATE TABLE projectx(pid NUMBER, pname VARCHAR(20), CONSTRAINT c1 PRIMARY KEY(pid, pname), phead NUMBER CONSTRAINT uc_px_34 UNIQUe, ploc CONSTRAINT uc_px_34 UNIQUE, pmembers NUMBER DEFAULT 5 CONSTRAINT ck_px_5 (pmembers<=5))
                                                                                                                                                                                                *
ERROR at line 1:
ORA-02253: constraint specification not allowed here 


SQL> CREATE TABLE projectx(pid NUMBER, pname VARCHAR(20) CONSTRAINT c1 PRIMARY KEY(pid, pname), phead NUMBER CONSTRAINT uc_px_34 UNIQUe, ploc CONSTRAINT uc_px_34 UNIQUE, pmembers NUMBER DEFAULT 5 CONSTRAINT ck_px_5 (pmembers<=5));
CREATE TABLE projectx(pid NUMBER, pname VARCHAR(20) CONSTRAINT c1 PRIMARY KEY(pid, pname), phead NUMBER CONSTRAINT uc_px_34 UNIQUe, ploc CONSTRAINT uc_px_34 UNIQUE, pmembers NUMBER DEFAULT 5 CONSTRAINT ck_px_5 (pmembers<=5))
                                                                             *
ERROR at line 1:
ORA-00907: missing right parenthesis 


SQL> CREATE TABLE projectx(pid NUMBER, pname VARCHAR(20), CONSTRAINT c1 PRIMARY KEY(pid, pname), phead NUMBER CONSTRAINT uc_px_34 UNIQUE, ploc CONSTRAINT uc_px_34 UNIQUE, pmembers NUMBER DEFAULT 5 CONSTRAINT ck_px_5 (pmembers<=5));
CREATE TABLE projectx(pid NUMBER, pname VARCHAR(20), CONSTRAINT c1 PRIMARY KEY(pid, pname), phead NUMBER CONSTRAINT uc_px_34 UNIQUE, ploc CONSTRAINT uc_px_34 UNIQUE, pmembers NUMBER DEFAULT 5 CONSTRAINT ck_px_5 (pmembers<=5))
                                                                                                                                                                                                *
ERROR at line 1:
ORA-02253: constraint specification not allowed here 


SQL> CREATE TABLE projectx(pid NUMBER, pname VARCHAR(20), CONSTRAINT c1 PRIMARY KEY(pid, pname), phead NUMBER CONSTRAINT uc_px_34 UNIQUE, ploc CONSTRAINT uc_px_34 UNIQUE, pmembers NUMBER DEFAULT 5 CONSTRAINT ck_px_5 CHECK (pmembers<=5));
CREATE TABLE projectx(pid NUMBER, pname VARCHAR(20), CONSTRAINT c1 PRIMARY KEY(pid, pname), phead NUMBER CONSTRAINT uc_px_34 UNIQUE, ploc CONSTRAINT uc_px_34 UNIQUE, pmembers NUMBER DEFAULT 5 CONSTRAINT ck_px_5 CHECK (pmembers<=5))
                                                                                                                                     *
ERROR at line 1:
ORA-02263: need to specify the datatype for this column 


SQL> CREATE TABLE projectx(pid NUMBER, pname VARCHAR(20), CONSTRAINT c1 PRIMARY KEY(pid,pname), phead NUMBER CONSTRAINT uc_px_34 UNIQUE, ploc VARCHAR(20) CONSTRAINT uc_px_34 UNIQUE, pmembers NUMBER DEFAULT 5 CONSTRAINT ck_px_5 CHECK (pmembers<=5));
CREATE TABLE projectx(pid NUMBER, pname VARCHAR(20), CONSTRAINT c1 PRIMARY KEY(pid,pname), phead NUMBER CONSTRAINT uc_px_34 UNIQUE, ploc VARCHAR(20) CONSTRAINT uc_px_34 UNIQUE, pmembers NUMBER DEFAULT 5 CONSTRAINT ck_px_5 CHECK (pmembers<=5))
                                                                                                                                                                *
ERROR at line 1:
ORA-02264: name already used by an existing constraint 


SQL> CREATE TABLE projectx(pid NUMBER, pname VARCHAR(20), CONSTRAINT c1 PRIMARY KEY(pid,pname), phead NUMBER, ploc VARCHAR(20),CONSTRAINT uc_px_34 UNIQUE(phead,ploc), pmembers NUMBER DEFAULT 5 CONSTRAINT ck_px_5 CHECK (pmembers<=5));

Table created.

SQL> desc projectx
 Name                                      Null?    Type
 ----------------------------------------- -------- ----------------------------
 PID                                       NOT NULL NUMBER
 PNAME                                     NOT NULL VARCHAR2(20)
 PHEAD                                              NUMBER
 PLOC                                               VARCHAR2(20)
 PMEMBERS                                           NUMBER

SQL> ALTER TABLE projectx DROP CONSTRAINT c1;

Table altered.

SQL> ALTER TABLE projectx ADD CONSTRAINT pk_px_1 PRIMARY KEY (pid);

Table altered.

SQL> INSERT INTO projectx VALUES(&pid, '&pname', &phead, '&ploc', &pmembers);
Enter value for pid: a11
Enter value for pname: dexter
Enter value for phead: 112
Enter value for ploc: Miami
Enter value for pmembers: 2
old   1: INSERT INTO projectx VALUES(&pid, '&pname', &phead, '&ploc', &pmembers)
new   1: INSERT INTO projectx VALUES(a11, 'dexter', 112, 'Miami', 2)
INSERT INTO projectx VALUES(a11, 'dexter', 112, 'Miami', 2)
                            *
ERROR at line 1:
ORA-00984: column not allowed here 


SQL> /
Enter value for pid: p67
Enter value for pname: luna
Enter value for phead: 113
Enter value for ploc: 
SP2-0546: User requested Interrupt or EOF detected.
SQL> 




SQL> ALTER TABLE projectx MODIFY pid VARCHAR(20);

Table altered.

SQL> desc projectx;
 Name                                      Null?    Type
 ----------------------------------------- -------- ----------------------------
 PID                                       NOT NULL VARCHAR2(20)
 PNAME                                              VARCHAR2(20)
 PHEAD                                              NUMBER
 PLOC                                               VARCHAR2(20)
 PMEMBERS                                           NUMBER

SQL> INSERT INTO projectx VALUES('&pid', '&pname', &phead, '&ploc', &pmembers);
Enter value for pid: a11
Enter value for pname: dexter
Enter value for phead: 112
Enter value for ploc: Miami
Enter value for pmembers: 2
old   1: INSERT INTO projectx VALUES('&pid', '&pname', &phead, '&ploc', &pmembers)
new   1: INSERT INTO projectx VALUES('a11', 'dexter', 112, 'Miami', 2)

1 row created.

SQL> /
Enter value for pid: p67
Enter value for pname: luna
Enter value for phead: 113
Enter value for ploc: Chennai
Enter value for pmembers: 3
old   1: INSERT INTO projectx VALUES('&pid', '&pname', &phead, '&ploc', &pmembers)
new   1: INSERT INTO projectx VALUES('p67', 'luna', 113, 'Chennai', 3)

1 row created.

SQL> INSERT INTO projectx VALUES('&pid', '&pname', &phead, '&ploc');
Enter value for pid: x55
Enter value for pname: east_west
Enter value for phead: 114
Enter value for ploc: Japan
old   1: INSERT INTO projectx VALUES('&pid', '&pname', &phead, '&ploc')
new   1: INSERT INTO projectx VALUES('x55', 'east_west', 114, 'Japan')
INSERT INTO projectx VALUES('x55', 'east_west', 114, 'Japan')
            *
ERROR at line 1:
ORA-00947: not enough values


SQL> INSERT INTO projectx VALUES('&pid', '&pname', &phead, '&ploc', &pmembers);
Enter value for pid: x55
Enter value for pname: east_west
Enter value for phead: 114
Enter value for ploc: Japan
Enter value for pmembers:
old   1: INSERT INTO projectx VALUES('&pid', '&pname', &phead, '&ploc', &pmembers)
new   1: INSERT INTO projectx VALUES('x55', 'east_west', 114, 'Japan', )
INSERT INTO projectx VALUES('x55', 'east_west', 114, 'Japan', )
                                                              *
ERROR at line 1:
ORA-00936: missing expression


SQL> SELECT * FROM projectx;

PID                  PNAME                     PHEAD PLOC
-------------------- -------------------- ---------- --------------------
  PMEMBERS
----------
a11                  dexter                      112 Miami
         2

p67                  luna                        113 Chennai
         3


SQL> INSERT INTO projectx(pid, pname, phead, ploc) VALUES('x55','east_west',114,'Japan');

1 row created.

SQL> SELECT * FROM projectx;

PID                  PNAME                     PHEAD PLOC
-------------------- -------------------- ---------- --------------------
  PMEMBERS
----------
a11                  dexter                      112 Miami
         2

p67                  luna                        113 Chennai
         3

x55                  east_west                   114 Japan
         5


SQL> SELECT * FROM emp12
  2  ;

     EMPID EMPNAME                    PHNO        AGE EMP_COUNTRY
---------- -------------------- ---------- ---------- --------------------
       112 Michael                     234         19 Russia
       113 Abdul                       913         25
       114 Raj                         238         54 USA

SQL> INSERT INTO emp12(emp_country) VALUES('India');
INSERT INTO emp12(emp_country) VALUES('India')
*
ERROR at line 1:
ORA-01400: cannot insert NULL into ("C21053264"."EMP12"."EMPID")


SQL> INSERT INTO emp12(emp_country) VALUES('India');
INSERT INTO emp12(emp_country) VALUES('India')
*
ERROR at line 1:
ORA-01400: cannot insert NULL into ("C21053264"."EMP12"."EMPID")


SQL> SELECT * FROM emp12;

     EMPID EMPNAME                    PHNO        AGE EMP_COUNTRY
---------- -------------------- ---------- ---------- --------------------
       112 Michael                     234         19 Russia
       113 Abdul                       913         25
       114 Raj                         238         54 USA

SQL> DELETE FROM emp12 WHERE empname='Abdul';

1 row deleted.

SQL> SELECT * FROM emp12;

     EMPID EMPNAME                    PHNO        AGE EMP_COUNTRY
---------- -------------------- ---------- ---------- --------------------
       112 Michael                     234         19 Russia
       114 Raj                         238         54 USA

SQL> INSERT INTO emp12(empid, empname, phno, age) VALUES(113,'Abdul', 913, 25);

1 row created.

SQL> SELECT * FROM emp12;

     EMPID EMPNAME                    PHNO        AGE EMP_COUNTRY
---------- -------------------- ---------- ---------- --------------------
       112 Michael                     234         19 Russia
       114 Raj                         238         54 USA
       113 Abdul                       913         25 India

SQL> DELETE FROM emp12 WHERE empid NOT IN(112,114,113)
  2  ;

0 rows deleted.

SQL> ALRER TABLE emp12 ADD project VARCHAR(20);
SP2-0734: unknown command beginning "ALRER TABL..." - rest of line ignored.
SQL> ALTER TABLE emp12 ADD project VARCHAR(20);

Table altered.

SQL> ALTER TABLE emp12 ADD FOREIGN KEY (project) REFERENCES projectx(pid);

Table altered.

SQL> SELECT * FROM emp12;

     EMPID EMPNAME                    PHNO        AGE EMP_COUNTRY
---------- -------------------- ---------- ---------- --------------------
PROJECT
--------------------
       112 Michael                     234         19 Russia


       114 Raj                         238         54 USA


       113 Abdul                       913         25 India



SQL> set linesize 500;
SQL> SELECT * FROM emp12;

     EMPID EMPNAME                    PHNO        AGE EMP_COUNTRY          PROJECT
---------- -------------------- ---------- ---------- -------------------- --------------------
       112 Michael                     234         19 Russia
       114 Raj                         238         54 USA
       113 Abdul                       913         25 India

SQL> INSERT INTO emp12(project) VALUES('&project');
Enter value for project: a11
old   1: INSERT INTO emp12(project) VALUES('&project')
new   1: INSERT INTO emp12(project) VALUES('a11')
INSERT INTO emp12(project) VALUES('a11')
*
ERROR at line 1:
ORA-01400: cannot insert NULL into ("C21053264"."EMP12"."EMPID")


SQL> UPDATE emp12 SET project = 'a11' WHERE empid=112;

1 row updated.

SQL> UPDATE emp12 SET project = 'p67' WHERE empid=113;

1 row updated.

SQL> UPDATE emp12 SET project = 'x55' WHERE empid=114;

1 row updated.

SQL> ALTER TABLE emp12 ADD FOREIGN KEY (project) REFERENCES projectx(pid);
ALTER TABLE emp12 ADD FOREIGN KEY (project) REFERENCES projectx(pid)
                      *
ERROR at line 1:
ORA-02275: such a referential constraint already exists in the table


SQL> INSERT INTO emp12(empid, empname, phno, project) VALUES(115,'Bono', 910,'a11');

1 row created.

SQL> INSERT INTO emp12(empid, empname, phno,age,emp_country, project) VALUES(116,'Caitlin', 660,25,'UK','p67');

1 row created.

SQL> INSERT INTO emp12(empid, empname, phno,age, project) VALUES(117,'Rajesh', 200,60,'x50');
INSERT INTO emp12(empid, empname, phno,age, project) VALUES(117,'Rajesh', 200,60,'x50')
*
ERROR at line 1:
ORA-02291: integrity constraint (C21053264.SYS_C007139) violated - parent key not found


SQL>
SQL> INSERT INTO emp12(empid, empname, phno, age, project) VALUES(117,'Rajesh',200,60,'x50');
INSERT INTO emp12(empid, empname, phno, age, project) VALUES(117,'Rajesh',200,60,'x50')
*
ERROR at line 1:
ORA-02291: integrity constraint (C21053264.SYS_C007139) violated - parent key not found


SQL> SELECT * FROM emp12;

     EMPID EMPNAME                    PHNO        AGE EMP_COUNTRY          PROJECT
---------- -------------------- ---------- ---------- -------------------- --------------------
       112 Michael                     234         19 Russia               a11
       115 Bono                        910            India                a11
       114 Raj                         238         54 USA                  x55
       113 Abdul                       913         25 India                p67
       116 Caitlin                     660         25 UK                   p67

SQL> INSERT INTO emp12(empid, empname, phno, age, project) VALUES(117,'Rajesh', 200, 60,'x50');
INSERT INTO emp12(empid, empname, phno, age, project) VALUES(117,'Rajesh', 200, 60,'x50')
*
ERROR at line 1:
ORA-02291: integrity constraint (C21053264.SYS_C007139) violated - parent key not found


SQL> ALTER TABLE projectx ADD FOREIGN KEY (phead) REFERENCES emp12(empid);

Table altered.

SQL> SHOW CREATE TABLE emp12
SP2-0158: unknown SHOW option "CREATE"
SP2-0158: unknown SHOW option "TABLE"
SP2-0158: unknown SHOW option "emp12"
SQL> SELECT INFORMATION FROM INFORMATION_SCHEMA.TABLE_CONSTRAINTS WHERE TABLE_NAME='emp12';
SELECT INFORMATION FROM INFORMATION_SCHEMA.TABLE_CONSTRAINTS WHERE TABLE_NAME='emp12'
                                           *
ERROR at line 1:
ORA-00942: table or view does not exist

