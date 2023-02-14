1. SELECT dept, AVG(salary) FROM employ GROUP BY dept;
2. SELECT job_type, AVG(salary) FROM employ GROUP BY job_type;
3. SELECT dept, AVG(salary) as avg_salary FROM employ GROUP BY dept HAVING AVG(salary) > 40000;
4. 