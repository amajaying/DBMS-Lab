1. SELECT dept, AVG(salary) FROM employ GROUP BY dept;
2. SELECT job_type, AVG(salary) FROM employ GROUP BY job_type;
3. SELECT dept, AVG(salary) as avg_salary FROM employ GROUP BY dept HAVING AVG(salary) > 40000;
4. SELECT dept FROM employ GROUP BY dept HAVING MAX(salary) > 55000;
5. SELECT dept, AVG(salary) as avg_salary FROM employ WHERE dept IN (SELECT dept FROM employ GROUP BY dept HAVING MAX(salary) > 55000) GROUP BY dept;
6. SELECT job_type, SUM(salary) as total_salary FROM employ GROUP BY job_type HAVING SUM(salary) > 100000;
7. SELECT job_type, SUM(salary) as total_salary FROM employ GROUP BY job_type HAVING SUM(salary) > 100000 AND job_type!='engineer';
8. SELECT job_type, SUM(salary) AS total_salary FROM employ WHERE job_type != 'engineer' GROUP BY job_type HAVING SUM(salary) > 60000 ORDER BY SUM(salary) ASC;
9. SELECT job_type, SUM(salary) AS total_salary FROM employ WHERE job_type != 'engineer' GROUP BY job_type HAVING SUM(salary) > 50000 ORDER BY SUM(salary) DESC;