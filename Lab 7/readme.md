ASSIGNMENT BASED ON DUAL TABLE

1.	Calculate 10*10.
    > SELECT 10 * 10 FROM dual;
2.	Display system date.
    > SELECT SYSDATE FROM dual;
3.	Calculate the absolute value  of -20.
    > SELECT ABS(-20) FROM DUAL;
4.	Calculate 10^10.
    > SELECT POWER(10,10) FROM DUAL;
5.	Calculate square root of 25.
    > SELECT SQRT(25) FROM DUAL;
6.	Round the value 23.565 to one places of decimal.
    > SELECT ROUND(23.565,1) FROM DUAL; 
7.	Display ‘TRIDENT’ in lowercase
    > SELECT LOWER('TRIDENT') FROM DUAL;
8.	Display ‘trident’ in uppercase.
    > SELECT UPPER('trident') FROM DUAL;
9.	Display the first letter of your name in uppercase.
    > SELECT INITCAP(SUBSTR('ajay',1,1)) FROM DUAL;
10.	Calculate the length of your name.
    > SELECT LENGTH('ajay') FROM DUAL;
11.	Write a query that would return a string like “ORA” , if the string inputted is ‘ORACLE’.
    > SELECT SUBSTR('ORACLE',1,3) FROM DUAL;
12.	Find the character position of ‘C’ in the string ‘ORACLE’.
    > SELECT INSTR('ORACLE','C') FROM DUAL;
13.	Delete the extra spaces from the strings ‘     ORACLE’ and ‘ORACLE   ‘     
    > SELECT TRIM('     ORACLE') AS first, SELECT TRIM('ORACLE   ') AS second FROM DUAL;
14.	Write a query that would display **ORACLE, if the string inputted is ORACLE.
    > SELECT CONCAT('**', 'ORACLE') as concatenated_string FROM dual;
15.	Same as question  14 but the output is   ORACLE**.
    > SELECT CONCAT('ORACLE','**') as concatenated_string FROM dual;
16.	Retrieve the last month specified in system date.
    > SELECT TO_CHAR(ADD_MONTHS(SYSDATE, -1), 'Month') as last_month FROM dual;
17.	Retrieve number of months between 01-01-07 to 01-05-07.
    > SELECT MONTHS_BETWEEN(TO_DATE('01-05-07', 'DD-MM-YY'), TO_DATE('01-01-07', 'DD-MM-YY')) as months FROM dual;
18.	Round 56.23 using negative numbers(e.g.-1,-2, and-3)
    > SELECT ROUND(56.23,-1) as rounded_value FROM dual;
    > SELECT ROUND(56.23,-2) as rounded_value FROM dual;
    > SELECT ROUND(56.23,-3) as rounded_value FROM dual;
19.	Find out the remainder of the division 1600/300.
    > SELECT MOD(1600, 300) AS remainder FROM dual;
20.	Find the maximum and minimum number from a list of numbers.
    > CREATE TABLE numbers (value NUMBER);
    > INSERT INTO numbers VALUES (100);
    > INSERT INTO numbers VALUES (50);
    > INSERT INTO numbers VALUES (99);
    > INSERT INTO numbers VALUES (16);
    > SELECT MAX(value) AS max_value FROM numbers;
    > SELECT MIN(value) AS min_value FROM numbers;

