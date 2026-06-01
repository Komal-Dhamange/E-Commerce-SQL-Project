# E-Commerce-SQL-Project

## Project Overview
This project demonstrates the implementation of an E-Commerce Database using SQL. It includes tables such as Users, Categories, Products, Addresses, Orders, OrderItems, and Payments. Various SQL queries are used to manage and retrieve data efficiently.

## Database Schema
- Users
- Categories
- Products
- Addresses
- Orders
- OrderItems
- Payments

---

# Database Creation and Data Insertion

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


## Question 4
**Create an Addresses table and insert address details of users.**

### SQL Query

```sql
CREATE TABLE Addresses (
    address_id INT PRIMARY KEY,
    user_id INT,
    address VARCHAR(200),
    city VARCHAR(50),
    FOREIGN KEY (user_id) REFERENCES Users(user_id)
);

INSERT INTO Addresses VALUES
(1, 1, 'Street 10, Pune', 'Pune'),
(2, 2, 'Sector 5, Mumbai', 'Mumbai'),
(3, 3, 'Connaught Place', 'Delhi');
```

### Verification Query

```sql
SELECT * FROM Addresses;
```

### Output

| address_id | user_id | address            | city    |
|------------|---------|--------------------|---------|
| 1 | 1 | Street 10, Pune     | Pune    |
| 2 | 2 | Sector 5, Mumbai    | Mumbai  |
| 3 | 3 | Connaught Place     | Delhi   |


## Question 5
**Create an Orders table and insert order details placed by users.**

### SQL Query

```sql
CREATE TABLE Orders (
    order_id INT PRIMARY KEY,
    user_id INT,
    order_date DATE,
    address_id INT,
    FOREIGN KEY (user_id) REFERENCES Users(user_id),
    FOREIGN KEY (address_id) REFERENCES Addresses(address_id)
);

INSERT INTO Orders VALUES
(5001, 1, '2024-05-10', 1),
(5002, 2, '2024-05-11', 2);
```

### Verification Query

```sql
SELECT * FROM Orders;
```

### Output

| order_id | user_id | order_date | address_id |
|----------|---------|------------|------------|
| 5001 | 1 | 2024-05-10 | 1 |
| 5002 | 2 | 2024-05-11 | 2 |

## Question 6
**Create an OrderItems table and insert details of products included in each order.**

### SQL Query

```sql
CREATE TABLE OrderItems (
    order_item_id INT PRIMARY KEY,
    order_id INT,
    product_id INT,
    quantity INT,
    FOREIGN KEY (order_id) REFERENCES Orders(order_id),
    FOREIGN KEY (product_id) REFERENCES Products(product_id)
);

INSERT INTO OrderItems VALUES
(1, 5001, 101, 1),
(2, 5001, 104, 2),
(3, 5002, 103, 1);
```

### Verification Query

```sql
SELECT * FROM OrderItems;
```

### Output

| order_item_id | order_id | product_id | quantity |
|----------------|----------|------------|----------|
| 1 | 5001 | 101 | 1 |
| 2 | 5001 | 104 | 2 |
| 3 | 5002 | 103 | 1 |


## Question 7
**Create a Payments table and insert payment details for customer orders.**

### SQL Query

```sql
CREATE TABLE Payments (
    payment_id INT PRIMARY KEY,
    order_id INT,
    amount INT,
    mode VARCHAR(50),
    status VARCHAR(50),
    FOREIGN KEY (order_id) REFERENCES Orders(order_id)
);

INSERT INTO Payments VALUES
(9001, 5001, 72400, 'UPI', 'Success'),
(9002, 5002, 55000, 'CARD', 'Success');
```

### Verification Query

```sql
SELECT * FROM Payments;
```

### Output

| payment_id | order_id | amount | mode | status |
|------------|----------|--------|------|---------|
| 9001 | 5001 | 72400 | UPI | Success |
| 9002 | 5002 | 55000 | CARD | Success |


## Question 8
**Display all users.**

### SQL Query

```sql
SELECT * FROM Users;
```

### Output

| user_id | full_name     | email            | phone        |
|----------|--------------|------------------|--------------|
| 1 | Rohan Sharma | rohan@gmail.com | 9999999991 |
| 2 | Priya Singh   | priya@gmail.com | 9999999992 |
| 3 | Aman Kumar    | aman@gmail.com  | 9999999993 |


## Question 9
**Display all products with their category names.**

### SQL Query

```sql
SELECT p.product_name, p.price, c.category_name
FROM Products p
JOIN Categories c
ON p.category_id = c.category_id;
```

### Output

| product_name   | price | category_name |
|----------------|-------|---------------|
| iPhone 14      | 70000 | Mobiles       |
| Samsung S23    | 65000 | Mobiles       |
| Dell Inspiron  | 55000 | Laptops       |
| Men T-Shirt    | 1200  | Fashion       |


## Question 10
**Display all orders with customer names.**

### SQL Query

```sql
SELECT o.order_id, u.full_name, o.order_date
FROM Orders o
JOIN Users u
ON o.user_id = u.user_id;
```

### Output

| order_id | full_name     | order_date |
|----------|--------------|------------|
| 5001 | Rohan Sharma | 2024-05-10 |
| 5002 | Priya Singh   | 2024-05-11 |


## Question 11
**Find the total number of products.**

### SQL Query

```sql
SELECT COUNT(*) AS Total_Products
FROM Products;
```

### Output

| Total_Products |
|----------------|
| 4 |


## Question 12
**Find the highest-priced product.**

### SQL Query

```sql
SELECT *
FROM Products
ORDER BY price DESC
LIMIT 1;
```

### Output

| product_id | product_name | price | category_id |
|------------|-------------|-------|-------------|
| 101 | iPhone 14 | 70000 | 1 |


## Question 13
**Calculate the total payment amount received.**

### SQL Query

```sql
SELECT SUM(amount) AS Total_Revenue
FROM Payments;
```

### Output

| Total_Revenue |
|---------------|
| 127400 |


## Question 14
**Display all successful payments.**

### SQL Query

```sql
SELECT *
FROM Payments
WHERE status='Success';
```

### Output

| payment_id | order_id | amount | mode | status |
|------------|----------|--------|------|---------|
| 9001 | 5001 | 72400 | UPI | Success |
| 9002 | 5002 | 55000 | CARD | Success |


## Question 15
**Display products ordered by customers.**

### SQL Query

```sql
SELECT u.full_name, p.product_name, oi.quantity
FROM Users u
JOIN Orders o ON u.user_id = o.user_id
JOIN OrderItems oi ON o.order_id = oi.order_id
JOIN Products p ON oi.product_id = p.product_id;
```

### Output

| full_name     | product_name   | quantity |
|--------------|---------------|----------|
| Rohan Sharma | iPhone 14     | 1 |
| Rohan Sharma | Men T-Shirt   | 2 |
| Priya Singh  | Dell Inspiron | 1 |


## Question 16
**Count the total number of orders placed.**

### SQL Query

```sql
SELECT COUNT(*) AS Total_Orders
FROM Orders;
```

### Output

| Total_Orders |
|--------------|
| 2 |


## Question 17
**Display customers and their cities.**

### SQL Query

```sql
SELECT u.full_name, a.city
FROM Users u
JOIN Addresses a
ON u.user_id = a.user_id;
```

### Output

| full_name     | city   |
|--------------|--------|
| Rohan Sharma | Pune   |
| Priya Singh  | Mumbai |
| Aman Kumar   | Delhi  |


## Question 18
**Find products costing more than ₹50,000.**

### SQL Query

```sql
SELECT *
FROM Products
WHERE price > 50000;
```

### Output

| product_id | product_name   | price |
|------------|---------------|-------|
| 101 | iPhone 14     | 70000 |
| 102 | Samsung S23   | 65000 |
| 103 | Dell Inspiron | 55000 |


## Conclusion

This project successfully demonstrates the design and implementation of an E-Commerce Database using SQL. The database manages users, products, categories, orders, addresses, and payments efficiently. Various SQL queries such as SELECT, JOIN, COUNT, SUM, and filtering operations were performed to retrieve meaningful information from the database.

## Technologies Used

- SQL
- MySQL

## Author

Komal Dhamange
