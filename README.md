# Task-6-SQL
subqueries amd correlated queries using differnt operators  like IN, Exists, >, = operators

select * from scott.emp;

select * from scott.DEPT;

// sub queries

// fetch the empno, ename, job and hiredate of empolyess which salary is same to empno 7782

select EMPNO, ename, job, HIREDATE,sal 
from scott.emp 
where sal=(select sal from scott.emp where empno=7782);

<img width="1920" height="1080" alt="Screenshot (49)" src="https://github.com/user-attachments/assets/f09fb3eb-321d-4fef-958a-ca0aa6321a53" />



// to fetch the emp details which fetched employee of manager which salary is 3000

select * from scott.emp where MGR in
(select empno from scott.emp where sal=3000);

<img width="1920" height="1080" alt="Screenshot (50)" src="https://github.com/user-attachments/assets/5ff6f285-b8b8-4f12-9d0c-c1d2b5d8bfd1" />


// using from clause

select count(*) from 
(select * from scott.emp where deptno = 10); 

<img width="1920" height="1080" alt="Screenshot (51)" src="https://github.com/user-attachments/assets/83efd7c5-4472-451e-92ca-5b4da57c6132" />



// fetch the emp details of whose empno less than empno which salary is 3000 

select * from scott.emp 
where empno < any (select empno from scott.emp where sal = 3000); 

<img width="1920" height="1080" alt="Screenshot (53)" src="https://github.com/user-attachments/assets/c0d86d4a-61e5-49ea-ae9f-b619dcf3b922" />



//using all operator

select * from scott.emp 
where empno < all (select empno from scott.emp where sal = 3000); 

<img width="1920" height="1080" alt="Screenshot (57)" src="https://github.com/user-attachments/assets/aef9fc3a-15d2-4511-afd9-49cc26bd6d67" />


// correlated subqueries

select * from scott.emp where
 sal > (select avg(sal) from scott.emp where deptno = 20) and deptno = 20; 

<img width="1920" height="1080" alt="Screenshot (54)" src="https://github.com/user-attachments/assets/6910cf71-7cf9-4ae7-a283-db67760a8bab" />


// using exist operator

 select * from scott.emp a where exists (select 'x' from scott.emp b where b.mgr = a.empno); 

 <img width="1920" height="1080" alt="Screenshot (55)" src="https://github.com/user-attachments/assets/784a96d4-4dfa-44ca-97f6-8c2507445f1d" />
