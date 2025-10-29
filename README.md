# Event-Ticketing-System-using-Sql
Event Ticketing System is a SQL-based database project to manage events, customers, tickets, reservations, and sales. It demonstrates advanced SQL concepts like joins, views, triggers, stored procedures, and analytical queries to track revenue, ticket status, and customer behavior efficiently

![image alt](https://github.com/Srivishnuu/Event-Ticketing-System-using-Sql/blob/00087cc8a7d6071534e924c0ada8d0b8c6e4abd2/Project%20Logo.jpg)

# Project Overview
The Event Ticketing System is a comprehensive database-driven application designed to manage events, customers, tickets, reservations, and sales efficiently. This project demonstrates practical use of SQL concepts such as joins, views, triggers, stored procedures, aggregate functions, window functions, and conditional queries.It is ideal for learning and showcasing skills in SQL database design, analytical queries, and transaction management.

# Tables Creation & Values Insertion
**Events**:Events details.
```sql
Table 1 : Events 
CREATE TABLE Events (
    event_id INT PRIMARY KEY,
    event_name VARCHAR(100),
    event_date DATE,
    location VARCHAR(100),
    total_tickets INT);
    
INSERT INTO Events (event_id, event_name, event_date, location, total_tickets) VALUES
(1000,'Music Concert', '2025-10-20', 'Chennai', 100),
(2000,'Miraj Cinemas', '2025-11-05', 'Bangalore', 150),
(3000,'Art Exhibition', '2025-10-25', 'Coimbatore', 80),
(4000,'Circus', '2025-12-31', 'Chennai', 500),
(5000,'Wonderla', '2025-02-04', 'Mumbai', 30),
(6000,'Tech Expo 2025', '2025-11-12', 'Hyderabad', 250),
(7000,'Food Carnival', '2025-12-05', 'Chennai', 300),
(8000,'Startup Summit', '2025-09-18', 'Bangalore', 180),
(9000,'Comedy Nights', '2025-11-22', 'Pune', 150),
(10000,'Auto Expo', '2025-12-10', 'Delhi', 400),
(11000,'Marathon 2025', '2025-10-28', 'Coimbatore', 200),
(12000,'Book Fair', '2025-11-15', 'Kolkata', 350),
(13000,'Dance Festival', '2025-12-20', 'Chennai', 280),
(14000,'Gaming Convention', '2025-11-09', 'Bangalore', 220),
(15000,'Science Exhibition', '2025-09-30', 'Mumbai', 180),
(16000,'Pet Show', '2025-10-14', 'Delhi', 120),
(17000,'Yoga Retreat', '2025-08-25', 'Rishikesh', 90),
(18000,'Film Festival', '2025-11-28', 'Hyderabad', 450),
(19000,'Craft Bazaar', '2025-10-19', 'Jaipur', 130),
(20000,'Coding Hackathon', '2025-11-02', 'Bangalore', 250),
(21000,'Fashion Week', '2025-12-25', 'Mumbai', 500),
(22000,'Charity Concert', '2025-10-29', 'Chennai', 400),
(23000,'Startup Networking', '2025-09-05', 'Pune', 100),
(24000,'Beach Music Festival', '2025-12-30', 'Goa', 600),
(25000,'Cultural Night', '2025-11-19', 'Coimbatore', 200);

```

**Customers**:Customers details.
```sql
Table 2 : Customers
CREATE TABLE Customers (
    customer_id INT PRIMARY KEY,
    customer_name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE,
    phone bigint);

INSERT INTO Customers (customer_id, customer_name, email, phone)VALUES
(1,'Vishnu', 'vishnu@gmail.com', 9876543210),
(2,'harini', 'harini@gmail.com', 8765432109),
(3,'Priya', 'priya@gmail.com', 7654321098),
(4,'Kavi', 'Kavi@gmail.com', 7634321698),
(5,'Virat', 'virat@gmail.com', 6783435213),
(6, 'Arjun', 'arjun@gmail.com', 7896541230),
(7, 'Divya', 'divya@gmail.com', 9876501234),
(8, 'Rahul', 'rahul@gmail.com', 8765123098),
(9, 'Sneha', 'sneha@gmail.com', 9988776655),
(10, 'Karthik', 'karthik@gmail.com', 9123456780),
(11, 'Aishwarya', 'aishwarya@gmail.com', 9345678123),
(12, 'Manoj', 'manoj@gmail.com', 9543216780),
(13, 'Sandhya', 'sandhya@gmail.com', 9008765432),
(14, 'Nithin', 'nithin@gmail.com', 9678901234),
(15, 'Meera', 'meera@gmail.com', 9821345670),
(16, 'Ajay', 'ajay@gmail.com', 9345612789),
(17, 'Varsha', 'varsha@gmail.com', 9123487560),
(18, 'Ravi', 'ravi@gmail.com', 9345621780),
(19, 'Swathi', 'swathi@gmail.com', 9786543210),
(20, 'Vikram', 'vikram@gmail.com', 9234567891),
(21, 'Ananya', 'ananya@gmail.com', 9765432108),
(22, 'Gokul', 'gokul@gmail.com', 9654321078),
(23, 'Lavanya', 'lavanya@gmail.com', 9678234509),
(24, 'Sanjay', 'sanjay@gmail.com', 9456123789),
(25, 'Preethi', 'preethi@gmail.com', 9356124780);


```

**Tickets**:Ticketing details and status.
```sql
Table 3: Tickets
CREATE TABLE Tickets (
    ticket_id INT PRIMARY KEY,
    event_id INT,
    price DECIMAL(10,2),
    seat_no VARCHAR(10),
    statuss VARCHAR(20),
    FOREIGN KEY (event_id) REFERENCES Events(event_id));
    
INSERT INTO Tickets (ticket_id, event_id, price, seat_no, statuss) VALUES
(101, 1000, 2000.00, 20, 'Booked'),
(102, 2000, 3000.00, 30, 'Booked'),
(103, 3000, 250.75, 44, 'Available'),
(104, 4000, 120.45, 35, 'Available'),
(105, 5000, 650.00, 90, 'Booked'),
(106, 1000, 350.00, 12, 'Booked'),
(107, 2000, 450.50, 28, 'Available'),
(108, 3000, 199.99, 42, 'Booked'),
(109, 4000, 120.00, 56, 'Available'),
(110, 5000, 899.00, 65, 'Booked'),
(111, 1000, 250.00, 18, 'Available'),
(112, 2000, 300.00, 31, 'Booked'),
(113, 3000, 499.50, 22, 'Booked'),
(114, 4000, 150.25, 73, 'Available'),
(115, 5000, 799.99, 47, 'Booked'),
(116, 1000, 200.00, 15, 'Booked'),
(117, 2000, 350.75, 19, 'Available'),
(118, 3000, 450.00, 24, 'Booked'),
(119, 4000, 500.25, 33, 'Available'),
(120, 5000, 999.00, 49, 'Booked'),
(121, 1000, 275.50, 10, 'Available'),
(122, 2000, 480.00, 17, 'Booked'),
(123, 3000, 320.00, 21, 'Available'),
(124, 4000, 150.00, 29, 'Booked'),
(125, 5000, 1050.00, 54, 'Available');
```

**Reservations**:Ticket Reservations by customers.
```sql
Table 4: Reservation Tickets
CREATE TABLE Reservations (
    reservation_id INT PRIMARY KEY,
    customer_id INT,
    event_id INT,
    ticket_id INT,
    reservation_date DATE,
    FOREIGN KEY (customer_id) REFERENCES Customers(customer_id),
    FOREIGN KEY (event_id) REFERENCES Events(event_id),
    FOREIGN KEY (ticket_id) REFERENCES Tickets(ticket_id));

INSERT INTO Reservations (reservation_id, customer_id, event_id, ticket_id, reservation_date) VALUES
(1111, 1, 1000, 101, '2025-09-08'),
(2222, 2, 2000, 102, '2025-08-08'),
(3333, 3, 3000, 103, '2025-06-07'),
(4444, 4, 4000, 104, '2025-04-17'),
(5555, 5, 5000, 105, '2025-03-08'),
(6660, 6, 6000, 106, '2025-09-15'),
(7777, 7, 7000, 107, '2025-08-20'),
(8888, 8, 8000, 108, '2025-06-18'),
(9999, 9, 9000, 109, '2025-04-25'),
(10101, 10, 10000, 110, '2025-03-12'),
(11111, 11, 11000, 111, '2025-07-19'),
(12121, 12, 12000, 112, '2025-08-09'),
(13131, 13, 13000, 113, '2025-05-17'),
(14141, 14, 14000, 114, '2025-04-30'),
(15151, 15, 15000, 115, '2025-03-22'),
(16161, 16, 16000, 116, '2025-10-01'),
(17171, 17, 17000, 117, '2025-09-10'),
(18181, 18, 18000, 118, '2025-07-05'),
(19191, 19, 19000, 119, '2025-05-10'),
(20202, 20, 20000, 120, '2025-02-18'),
(21212, 21, 21000, 121, '2025-09-22'),
(22222, 22, 22000, 122, '2025-08-28'),
(23232, 23, 23000, 123, '2025-06-16'),
(24242, 24, 24000, 124, '2025-04-05'),
(25252, 25, 25000, 125, '2025-03-02');

```


**Sales**:Sales & transaction details.
```sql
Table 5: Sales
CREATE TABLE Sales (
    sale_id INT PRIMARY KEY,
    reservation_id INT,
    sale_date DATE,
    amount DECIMAL(10,2),
    FOREIGN KEY (reservation_id) REFERENCES Reservations(reservation_id));

INSERT INTO Sales(sale_id, reservation_id, sale_date, amount)VALUES
(2001,1111,'2025-06-07', 1000.00),
(2002,2222,'2025-04-08', 4000.00),
(2003,3333,'2025-05-06', 6500.00),
(2004,4444,'2025-06-09', 7500.00),
(2005,5555,'2025-12-07', 8000.00),
(2006, 6660, '2025-09-16', 1500.00),
(2007, 7777, '2025-08-21', 2200.50),
(2008, 8888, '2025-06-19', 1800.75),
(2009, 9999, '2025-04-26', 1200.00),
(2010, 10101, '2025-03-13', 2500.00),
(2011, 11111, '2025-07-20', 1750.25),
(2012, 12121, '2025-08-10', 3000.50),
(2013, 13131, '2025-05-18', 2100.00),
(2014, 14141, '2025-05-01', 1450.75),
(2015, 15151, '2025-03-23', 2700.00),
(2016, 16161, '2025-10-02', 1900.50),
(2017, 17171, '2025-09-11', 2300.00),
(2018, 18181, '2025-07-06', 1600.25),
(2019, 19191, '2025-05-11', 2000.00),
(2020, 20202, '2025-02-19', 1400.50),
(2021, 21212, '2025-09-23', 2500.75),
(2022, 22222, '2025-08-29', 3100.00),
(2023, 23232, '2025-06-17', 2700.25),
(2024, 24242, '2025-04-06', 1800.00),
(2025, 25252, '2025-03-03', 2900.50);
```


# Features 
**Event Management:**
Maintain a catalog of events including event name, date, location, and total tickets.Supports multiple types of events such as concerts, exhibitions, marathons, expos, and festivals.

**Customer Management:**
Store customer information including name, email, and phone number.Ensures unique email addresses and valid contact details.

**Ticket Management:**
Manage tickets for events, including seat numbers, prices, and availability status.Automatically updates ticket status to ‘Booked’ when a reservation is made using a trigger.

**Reservation Management:**
Keep track of customer reservations for events.Links customers to tickets and events.

**Sales Tracking:**
Records sale transactions, including sale amount and date.Provides insights into revenue generated per event.

# Key Functionalities
**Aggregate & Analytical Queries**: Total events, ticket sales, revenue per event, and customer spending analysis.

**Conditional Queries**: Categorize ticket prices as Premium, Standard, or Budget using CASE statements.

**Views**: Event_Sales_Summary provides average revenue per event.

**Stored Procedures**: GetEvent() procedure fetches total events, sales, and revenue.

**Triggers**: Automatically updates ticket status upon reservation.

**Window Functions**: Rank events based on revenue.

**Date Functions**: Calculate days left for upcoming events.

**String Functions**: Format customer names, extract event types, and manipulate text.

**Math Functions**: ROUND, CEIL, FLOOR, and ABS for ticket price analytics.

# E-R Diagram

![image alt](https://github.com/Srivishnuu/Event-Ticketing-System-using-Sql/blob/fe9790a2842a0efcf8c3a1cda3e3f01b88ebce7d/ER-Diagram%20.jpg)




# Problem Statement
Q1.AGGREGATE - Total Number of Events
```sql
SELECT COUNT(event_name) as Total_Events from Events;
```
Q2.WHERE CONDITION - Find the Tickets Sold Details(Booked)
```sql
SELECT * from Tickets 
WHERE statuss = 'Booked';
```

Q3.LEFT JOIN - Average Ticket Price for all events Order By Descending Order; 
```sql
SELECT e.event_name, AVG(t.price) as Average_Price from Events  e Left Join Tickets t 
ON  e.event_id = t.event_id
GROUP BY event_name
ORDER BY price Desc;
```

Q4.JOIN - Total Revenue Per Event
```sql
SELECT e.event_name, SUM(s.amount) AS total_revenue 
FROM Sales s JOIN Reservations r 
ON s.reservation_id = r.reservation_id
JOIN Events e ON r.event_id = e.event_id
GROUP BY e.event_name;
```

Q5.HAVING CLAUSE - Give me the Customer name who spend amount is Greater 5000;
```sql
SELECT c.customer_name, SUM(s.amount) AS total_spent FROM Sales s
JOIN Reservations r ON s.reservation_id = r.reservation_id
JOIN Customers c ON r.customer_id = c.customer_id
GROUP BY c.customer_name
HAVING SUM(s.amount) > 5000;
```

Q6.JOIN MULTIPLE TABLES - Find all Customer details and each of them wants to Know the Exact Location of where the events happens
```sql
SELECT c.customer_name, c.email, c.phone, e.event_name, e.location AS event_location
FROM Customers c
JOIN Reservations r ON c.customer_id = r.customer_id
JOIN Events e ON r.event_id = e.event_id
ORDER BY c.customer_name;
```

Q7.VIEW - Create view for sales summary
```sql
CREATE VIEW Event_Sales_Summary AS
SELECT e.event_name,ROUND(AVG(s.amount),2) AS avg_revenue_per_sale
FROM Sales s
JOIN Reservations r ON s.reservation_id = r.reservation_id
JOIN Events e ON r.event_id = e.event_id
GROUP BY e.event_name;
Select * from Event_Sales_Summary;

```

Q8.SUBQUERY — Find Above Average Events by Revenue.
```sql
SELECT event_name, SUM(s.amount) AS total_revenue
FROM Sales s
JOIN Reservations r ON s.reservation_id = r.reservation_id
JOIN Events e ON r.event_id = e.event_id
GROUP BY e.event_name
HAVING total_revenue > (SELECT AVG(amount) FROM Sales);
```


Q9.TRIGGER — Automatically Update Ticket Status to ‘Booked’ When Reservation Made
```sql
DELIMITER $$
CREATE TRIGGER update_ticket_status
AFTER INSERT ON Reservations
FOR EACH ROW
BEGIN
    UPDATE Tickets
    SET statuss = 'Booked'
    WHERE ticket_id = NEW.ticket_id;
END $$
DELIMITER ;
```

Q10.STORED PROCEDURE — Get Event Count & Total Sales
```sql
DELIMITER $$
CREATE PROCEDURE GetEvent()
BEGIN
    SELECT 
        COUNT(DISTINCT e.event_id) AS total_events,
        COUNT(s.sale_id) AS total_sales,
        SUM(s.amount) AS total_revenue
    FROM Sales s
    JOIN Reservations r ON s.reservation_id = r.reservation_id           
    JOIN Events e ON r.event_id = e.event_id;
END $$
DELIMITER ;
CALL GetEvent();
```

Q11.WINDOW FUNCTION - Find the highest revenue-generating event and rank all events by total revenue
```sql
SELECT 
    e.event_name,
    SUM(s.amount) AS total_revenue,
    RANK() OVER (ORDER BY SUM(s.amount) DESC) AS revenue_rank
FROM Sales s
JOIN Reservations r ON s.reservation_id = r.reservation_id
JOIN Events e ON r.event_id = e.event_id
GROUP BY e.event_name;
```

Q12.DATE FUNCTION - Find the number of days left for each upcoming event.
```sql
SELECT 
    event_name,
    event_date,
    DATEDIFF(event_date, CURDATE()) AS days_until_event
FROM Events
WHERE event_date > CURDATE()
ORDER BY days_until_event;
```

Q13.CASE STATEMENT (Conditional Logic in Queries) - Categorize ticket prices as ‘Premium’, ‘Standard’, or ‘Budget’.
```sql
SELECT 
    t.ticket_id,
    e.event_name,
    t.price,
    CASE 
        WHEN t.price >= 3000 THEN 'Premium'
        WHEN t.price BETWEEN 1000 AND 2999 THEN 'Standard'
        ELSE 'Budget'
    END AS price_category
FROM Tickets t
JOIN Events e ON t.event_id = e.event_id;
```

Q14.UPPER / LOWER – Format Customer Names
```sql
SELECT 
    customer_id,
    UPPER(customer_name) AS formatted_name
FROM Customers;
```

Q15.SUBSTRING – Extract Event Type
```sql
SELECT 
    event_id,
    event_name,
    SUBSTRING(event_name, 1, LOCATE(' ', event_name) - 1) AS event_type
FROM Events
WHERE event_name LIKE '% %';
```

Q16.CONCAT – Combine Customer Name and Email
```sql
SELECT 
    CONCAT(customer_name, ' (', email, ')') AS contact_label
    FROM Customers;
```

Q17.LENGTH – Find Longest Event Name
```sql
SELECT 
    event_name, 
    LENGTH(event_name) AS name_length
FROM Events
ORDER BY name_length DESC
LIMIT 1;
```

Q18.REPLACE – Fix Event Name Spelling
```sql
UPDATE Events
SET event_name = REPLACE(event_name, 'Miraj', 'Mirage')
WHERE event_name LIKE '%Miraj%';
```

Q19.ROUND – Round Ticket Prices
```sql
SELECT 
    ticket_id, 
    price AS original_price, 
    ROUND(price) AS rounded_price
FROM Tickets;
```

Q20.CEIL & FLOOR – Ticket Pricing
```sql
SELECT 
    ticket_id, 
    price,
    CEIL(price) AS ceil_price,
    FLOOR(price) AS floor_price
FROM Tickets;
```

Q21.ABS – Difference Between Ticket Price and Sale Amount
```sql
SELECT 
    r.reservation_id,
    ABS(t.price - s.amount) AS price_difference
FROM Sales s
JOIN Reservations r ON s.reservation_id = r.reservation_id
JOIN Tickets t ON r.ticket_id = t.ticket_id;

```

# Technologies Used
**SQL / MySQL**: Database creation, management, and querying.

**SQL Concepts**: Joins, Views, Subqueries, Triggers, Stored Procedures, Aggregate Functions, Window Functions, Conditional Logic, String & Date Functions.

# Purpose & Use Case
**This project simulates a real-world event ticketing system, making it ideal for:**

* Managing events, tickets, reservations, and sales efficiently.

* Learning advanced SQL techniques in a structured way.

* Providing insights for event organizers regarding revenue, customer behavior, and ticket trends.
