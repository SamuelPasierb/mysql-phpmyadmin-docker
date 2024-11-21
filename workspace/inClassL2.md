## In-Class Task 2: Working with Tables - Create Table

You are required to complete the following tasks in-class on the same day and push it to GitHub. (1 point)

1. **Create a Database**: Write a SQL statement to create a new database named fnameClass2 (replace fname with your first name).

mysql> CREATE DATABASE SamuelClass2;
Query OK, 1 row affected (0.25 sec)

2. **Use the Database**: Use the newly created database fnameClass2 for the following tasks.

mysql> USE SamuelClass2;
Database changed

    1. Create a table named **author** with the following columns:
        - aut_id (integer)
        - aut_fname (varchar, 50 characters)
        - country (varchar, 50 characters)
        - home_city (varchar, 50 characters)
        - created_at (timestamp)

    mysql> CREATE TABLE author(
    -> aut_id INT,
    -> aut_fname VARCHAR(50),
    -> country VARCHAR(50),
    -> home_city VARCHAR(50),
    -> created_at TIMESTAMP
    -> );
    Query OK, 0 rows affected (0.01 sec)

    2. Create a table named **student** with the following columns:
        - student_id (integer, primary key)
        - fname (varchar, 50 characters)
        - lname (varchar, 50 characters)
        - country (varchar, 50 characters)

    mysql> CREATE TABLE student(
    -> student_id INT PRIMARY KEY,
    -> fname VARCHAR(50),
    -> lname VARCHAR(50),
    -> country VARCHAR(50)
    -> );
    Query OK, 0 rows affected (0.01 sec)

    3. **Create a Duplicate Structure of a Table:** Create a table named **dup_student** with the same structure as the **student** table without copying the data. 

    mysql> CREATE TABLE dup_student LIKE student;
    Query OK, 0 rows affected (0.02 sec)

    4. **Copy Table with Data**: Create a new table **students_copy** that duplicates the structure and data of the **student** table.

    mysql> CREATE TABLE students_copy AS SELECT * FROM student;
    Query OK, 0 rows affected (0.02 sec)
    Records: 0  Duplicates: 0  Warnings: 0

    5. Create a table named **author1** with the same structure as author but ensure **aut_id** is a primary key. 
    mysql> CREATE TABLE author1( aut_id INT NOT NULL AUTO_INCREMENT, PRIMARY KEY(aut_id)) SELECT * FROM author;
    Query OK, 0 rows affected (0.02 sec)
    Records: 0  Duplicates: 0  Warnings: 0

    6. **Add Primary Key Using ALTER TABLE**:
    Add a primary key constraint to the **aut_id** column in the author table.
    mysql> ALTER TABLE author 
    -> ADD PRIMARY KEY(aut_id);
    Query OK, 0 rows affected (0.02 sec)
    Records: 0  Duplicates: 0  Warnings: 0

    7. **Remove Primary Key Constraint**:
    Remove the primary key constraint from the **aut_id** column in the author1 table.
    mysql> ALTER TABLE author1 MODIFY aut_id INT NOT NULL;
    Query OK, 0 rows affected (0.02 sec)
    Records: 0  Duplicates: 0  Warnings: 0

    mysql> ALTER TABLE author1 DROP PRIMARY KEY;
    Query OK, 0 rows affected (0.03 sec)
    Records: 0  Duplicates: 0  Warnings: 0

    8. **Create a Table with a Composite Key** : Create a table named **orders** with columns order_id, product_id, quantity, and set order_id and product_id as a composite primary key.
    mysql> CREATE TABLE orders(
    -> order_id INT,
    -> product_id INT,
    -> quantity INT,
    -> PRIMARY KEY(order_id, product_id)
    -> );
    Query OK, 0 rows affected (0.01 sec)

    10. **Create a Temporary Table**
    Create a temporary table named temp_students with the same structure as the **student** table.
    mysql> CREATE TEMPORARY TABLE temp_students LIKE student;
    Query OK, 0 rows affected (0.00 sec)

    11. **Create a Table with a NOT NULL Constraint**: Create a table named books with columns book_id, title, and author, and ensure that title cannot be null.
    mysql> CREATE TABLE books(
    -> book_id INT PRIMARY KEY,
    -> title VARCHAR(50) NOT NULL,
    -> author VARCHAR(50)
    -> );
    Query OK, 0 rows affected (0.01 sec)

    12. **Create a Table with a CHECK Constraint**:  Create a table named employees with columns emp_id, emp_name, salary, and add a CHECK constraint to ensure salary is greater than zero.
    mysql> CREATE TABLE employees (
    -> emp_id INT PRIMARY KEY,
    -> emp_name VARCHAR(50),
    -> salary INT CHECK(salary > 0)
    -> );
    Query OK, 0 rows affected (0.01 sec)

    13. **Create a Table with a DEFAULT Constraint** : Create a table orders with a status column having a default value of ‘Pending’.
    mysql> ALTER TABLE orders
    -> ADD status VARCHAR(20) DEFAULT 'Pending';
    Query OK, 0 rows affected (0.01 sec)
    Records: 0  Duplicates: 0  Warnings: 0

    14. **Create a Table with a UNIQUE Constraint** Create a table users with a user_id as primary key and an email column with a UNIQUE constraint.
    mysql> CREATE TABLE users(
    -> user_id INT PRIMARY KEY,
    -> email VARCHAR(50) UNIQUE
    -> );
    Query OK, 0 rows affected (0.01 sec)

    15. **Describe the Table**: Use the DESCRIBE statement to view the structure of the student table
    mysql> DESCRIBE student;
    +------------+-------------+------+-----+---------+-------+
    | Field      | Type        | Null | Key | Default | Extra |
    +------------+-------------+------+-----+---------+-------+
    | student_id | int         | NO   | PRI | NULL    |       |
    | fname      | varchar(50) | YES  |     | NULL    |       |
    | lname      | varchar(50) | YES  |     | NULL    |       |
    | country    | varchar(50) | YES  |     | NULL    |       |
    +------------+-------------+------+-----+---------+-------+
    4 rows in set (0.00 sec)

    16. **Drop a Table**: Drop the students table from the database.
    mysql> DROP TABLE student;
    Query OK, 0 rows affected (0.00 sec)

    17. **Truncate a Table** : Remove all rows from the dup_students table without deleting the table itself.
    mysql> TRUNCATE TABLE dup_student;
    Query OK, 0 rows affected (0.02 sec)
