# Event-Ticketing-System-using-Sql
Event Ticketing System is a SQL-based database project to manage events, customers, tickets, reservations, and sales. It demonstrates advanced SQL concepts like joins, views, triggers, stored procedures, and analytical queries to track revenue, ticket status, and customer behavior efficiently

![image alt](https://github.com/Srivishnuu/Event-Ticketing-System-using-Sql/blob/00087cc8a7d6071534e924c0ada8d0b8c6e4abd2/Project%20Logo.jpg)

# Project Overview
The Event Ticketing System is a comprehensive database-driven application designed to manage events, customers, tickets, reservations, and sales efficiently. This project demonstrates practical use of SQL concepts such as joins, views, triggers, stored procedures, aggregate functions, window functions, and conditional queries.It is ideal for learning and showcasing skills in SQL database design, analytical queries, and transaction management.

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

# Database Schema - Tables Used
**Events**: Stores event details.

**Customers**: Stores customer details.

**Tickets**: Stores ticket details and status.

**Reservations**: Stores ticket reservations by customers.

**Sales**: Stores transaction details.

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
