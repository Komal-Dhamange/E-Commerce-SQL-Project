# E-Commerce-SQL-Project

# E-Commerce SQL Project

## Question 1
**Create a Users table and insert user details into the table.**

### SQL Query

```sql
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
```

### Verification Query

```sql
SELECT * FROM Users;
```

### Output

| user_id | full_name     | email            | phone      |
|----------|--------------|------------------|------------|
| 1 | Rohan Sharma | rohan@gmail.com | 9999999991 |
| 2 | Priya Singh | priya@gmail.com | 9999999992 |
| 3 | Aman Kumar | aman@gmail.com | 9999999993 |


## Question 2
**Create a Categories table and insert category details into the table.**

### SQL Query

```sql
CREATE TABLE Categories (
    category_id INT PRIMARY KEY,
    category_name VARCHAR(100)
);

INSERT INTO Categories VALUES
(1, 'Mobiles'),
(2, 'Laptops'),
(3, 'Fashion');
```

### Verification Query

```sql
SELECT * FROM Categories;
```

### Output

| category_id | category_name |
|-------------|--------------|
| 1 | Mobiles |
| 2 | Laptops |
| 3 | Fashion |


## Question 3
**Create a Products table and insert product details along with their category information.**

### SQL Query

```sql
CREATE TABLE Products (
    product_id INT PRIMARY KEY,
    product_name VARCHAR(100),
    price INT,
    category_id INT,
    FOREIGN KEY (category_id) REFERENCES Categories(category_id)
);

INSERT INTO Products VALUES
(101, 'iPhone 14', 70000, 1),
(102, 'Samsung S23', 65000, 1),
(103, 'Dell Inspiron', 55000, 2),
(104, 'Men T-Shirt', 1200, 3);
```

### Verification Query

```sql
SELECT * FROM Products;
```

### Output

| product_id | product_name   | price | category_id |
|------------|---------------|-------|-------------|
| 101 | iPhone 14     | 70000 | 1 |
| 102 | Samsung S23   | 65000 | 1 |
| 103 | Dell Inspiron | 55000 | 2 |
| 104 | Men T-Shirt   | 1200  | 3 |
