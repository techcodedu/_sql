```markdown
# SQL Schema and Exercises for kiosk_app

## Database Schema
```sql
CREATE DATABASE IF NOT EXISTS kiosk_app;
USE kiosk_app;

-- Creating table `order`
CREATE TABLE `order` (
  `OrderID` int(11) NOT NULL,
  `CustomerMobileNumber` varchar(15) DEFAULT NULL,
  `TotalCost` decimal(10,2) DEFAULT NULL,
  PRIMARY KEY (`OrderID`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- Creating table `orderdetails`
CREATE TABLE `orderdetails` (
  `OrderDetailsID` int(11) NOT NULL,
  `OrderID` int(11) DEFAULT NULL,
  `ProductID` int(11) DEFAULT NULL,
  `Quantity` decimal(10,2) DEFAULT NULL,
  PRIMARY KEY (`OrderDetailsID`),
  KEY `OrderID` (`OrderID`),
  KEY `ProductID` (`ProductID`),
  CONSTRAINT `orderdetails_ibfk_1` FOREIGN KEY (`OrderID`) REFERENCES `order` (`OrderID`),
  CONSTRAINT `orderdetails_ibfk_2` FOREIGN KEY (`ProductID`) REFERENCES `product` (`ProductID`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- Creating table `product`
CREATE TABLE `product` (
  `ProductID` int(11) NOT NULL,
  `ProductName` varchar(255) DEFAULT NULL,
  `Price` decimal(10,2) DEFAULT NULL,
  `Unit` varchar(50) DEFAULT NULL,
  `PhotoURL` varchar(255) DEFAULT NULL,
  PRIMARY KEY (`ProductID`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- Inserting initial data into `product`
INSERT INTO `product` (`ProductID`, `ProductName`, `Price`, `Unit`, `PhotoURL`) VALUES
(1, 'Fresh Apples', 2.50, 'kg', 'images/apple.jpg'),
(2, 'Organic Tomatoes', 3.00, 'kg', '../images/orange.jpg'),
(3, 'Green Lettuce', 1.20, 'piece', '../assets/images/noche.jpg'),
(4, 'Whole Wheat Bread', 2.00, 'pack', '../assets/images/buffalo.jpg'),
(5, 'Free Range Eggs', 3.50, 'dozen', 'images/eggs.jpg');

-- Inserting sample data into `order`
INSERT INTO `order` (`OrderID`, `CustomerMobileNumber`, `TotalCost`) VALUES
(101, '1234567890', 15.70),
(102, '0987654321', 8.40),
(103, '5555555555', 22.50);

-- Inserting sample data into `orderdetails`
INSERT INTO `orderdetails` (`OrderDetailsID`, `OrderID`, `ProductID`, `Quantity`) VALUES
(1, 101, 1, 2),
(2, 101, 4, 1),
(3, 102, 3, 2),
(4, 103, 5, 3),
(5, 103, 2, 1);
```

## SQL Exercises

1. Select All Products: Write a SQL query to display all columns from the `product` table.
2. Filter Specific Products: Display all details from the `product` table where the price is greater than ₱2.00.
3. Count Products: How many products are listed in the `product` table?
4. Summarize Orders: Find the total cost of all orders in the `order` table.
5. List Orders with Customer Mobile Number: Display a list of all orders including the customer's mobile number.
6. Find Specific Order Details: Write a query to find all order details for `OrderID` 101.
7. Join Orders and Order Details: Display all order details along with order information by joining `order` and `orderdetails` tables.
8. Calculate Total Quantity Ordered: For each order, calculate the total quantity of items ordered.
9. Average Product Price: What is the average price of the products?
10. List Products with No Orders: Find all products that have not been ordered yet.
11. Order Total Calculation: For each order, calculate the total cost of all items in the order (you will need to join tables and calculate the sum).
12. Update Product Price: Increase the price of all products by 10%.
13. Delete an Order: Write a SQL command to delete order with `OrderID` 102.
14. Create a New Product: Insert a new product into the

 `product` table.
15. Find the Most Expensive Product: Identify the most expensive product in the `product` table.
16. List of Orders Below a Certain Cost: Display all orders with a total cost less than ₱10.00.
17. Group Products by Price Range: Group products into price ranges (e.g., ₱0-₱1, ₱1-₱2, etc.).
18. Find Orders with Multiple Items: Identify orders that contain more than one item.
19. Customer Order History: Display all orders made by a specific customer (choose any customer mobile number).
20. Most Popular Product: Identify the product that has been ordered the most in terms of quantity.
```
