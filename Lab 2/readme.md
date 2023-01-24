# INSERT ALL ROWS AT A TIME:

INSERT INTO emp VALUES('&empname',&empno);


# If you want to reorder the columns, use

SELECT dno, dname, location FROM dept;

# NOTE: this only reorders while displaying, the actual table is not reordered.


# use `commit;` to save the data in sql