# E-Commerce-SQL-Project

Question 1
Create a Users table and insert user details into the table.

SQL Query
CREATE TABLE Users (
    user_id INT PRIMARY KEY,
    full_name VARCHAR(100),
    email VARCHAR(100),
    phone VARCHAR(20)
);

INSERT INTO Users VALUES
(1, 'Rohan Sharma', 'rohan@gmail.com', '9999999991'),
(2, 'Priya Singh', 'priya@gmail.com', '9999999992'),
(3, 'Aman Kumar', 'aman@gmail.com', '9999999993');

Verification Query
SELECT * FROM Users;

Output
| user_id | full_name    | email                                     | phone      |
| ------- | ------------ | ----------------------------------------- | ---------- |
| 1       | Rohan Sharma | [rohan@gmail.com](mailto:rohan@gmail.com) | 9999999991 |
| 2       | Priya Singh  | [priya@gmail.com](mailto:priya@gmail.com) | 9999999992 |
| 3       | Aman Kumar   | [aman@gmail.com](mailto:aman@gmail.com)   | 9999999993 |
