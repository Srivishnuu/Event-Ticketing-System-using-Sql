# Event-Ticketing-System-using-Sql
Event Ticketing System is a SQL-based database project to manage events, customers, tickets, reservations, and sales. It demonstrates advanced SQL concepts like joins, views, triggers, stored procedures, and analytical queries to track revenue, ticket status, and customer behavior efficiently

![image alt](https://github.com/Srivishnuu/Event-Ticketing-System-using-Sql/blob/00087cc8a7d6071534e924c0ada8d0b8c6e4abd2/Project%20Logo.jpg)

**Project Overview**

The Event Ticketing System is a comprehensive database-driven application designed to manage events, customers, tickets, reservations, and sales efficiently. This project demonstrates practical use of SQL concepts such as joins, views, triggers, stored procedures, aggregate functions, window functions, and conditional queries.It is ideal for learning and showcasing skills in SQL database design, analytical queries, and transaction management.

**Features**
Event Management
1).Maintain a catalog of events including event name, date, location, and total tickets.
2).Supports multiple types of events such as concerts, exhibitions, marathons, expos, and festivals.

Customer Management
1).Store customer information including name, email, and phone number.
2).Ensures unique email addresses and valid contact details.

Ticket Management
1).Manage tickets for events, including seat numbers, prices, and availability status.
2).Automatically updates ticket status to ‘Booked’ when a reservation is made using a trigger.

Reservation Management
1).Keep track of customer reservations for events.
2).Links customers to tickets and events.

Sales Tracking
1).Records sale transactions, including sale amount and date.
2).Provides insights into revenue generated per event.

**Key Functionalities**
Aggregate & Analytical Queries: Total events, ticket sales, revenue per event, and customer spending analysis.
Conditional Queries: Categorize ticket prices as Premium, Standard, or Budget using CASE statements.
Views: Event_Sales_Summary provides average revenue per event.
Stored Procedures: GetEvent() procedure fetches total events, sales, and revenue.
Triggers: Automatically updates ticket status upon reservation.
Window Functions: Rank events based on revenue.
Date Functions: Calculate days left for upcoming events.
String Functions: Format customer names, extract event types, and manipulate text.
Math Functions: ROUND, CEIL, FLOOR, and ABS for ticket price analytics.

Database Schema
**Tables Used:**
Events: Stores event details.
Customers: Stores customer details.
Tickets: Stores ticket details and status.
Reservations: Stores ticket reservations by customers.
Sales: Stores transaction details.

**Relationships:**
Reservations links Customers, Events, and Tickets.
Sales links to Reservations.
Sample Queries Implemented
Total number of events.
Tickets sold details.
Average ticket price per event.
Total revenue per event.
Customers who spent more than 5000.
Customer details with event locations.
Sales summary view.
Events with above-average revenue.
Automatically update ticket status on reservation.
Stored procedure to get event and sales summary.
Highest revenue-generating event ranking.
Days left until upcoming events.
Categorize ticket prices.
Format customer names using UPPER/LOWER.
Extract event type using SUBSTRING.
Combine customer name and email using CONCAT.
Find the longest event name.
Correct event names using REPLACE.
Round ticket prices.
Apply CEIL and FLOOR on ticket prices.
Calculate absolute difference between ticket price and sale amount.

**Technologies Used**
SQL / MySQL: Database creation, management, and querying.
SQL Concepts: Joins, Views, Subqueries, Triggers, Stored Procedures, Aggregate Functions, Window Functions, Conditional Logic, String & Date Functions.

**Purpose & Use Case**
This project simulates a real-world event ticketing system, making it ideal for:
Managing events, tickets, reservations, and sales efficiently.
Learning advanced SQL techniques in a structured way.
Providing insights for event organizers regarding revenue, customer behavior, and ticket trends.
