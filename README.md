# ⚽ Football Ticket Booking System Database Assignment

## 📖 Project Overview

The Football Ticket Booking System is a relational database project designed to manage football match ticket sales. The system allows football fans to purchase tickets for upcoming matches while enabling ticket managers to oversee bookings and match information.

This project demonstrates database design concepts, table relationships, and SQL query operations using PostgreSQL.

---

# 🗄️ Database Tables

## 1️⃣ Users Table

Stores information about customers and administrative staff.

| Column Name  | Description                     |
| ------------ | ------------------------------- |
| user_id      | Unique identifier for each user |
| full_name    | Full name of the user           |
| email        | User email address              |
| role         | Football Fan or Ticket Manager  |
| phone_number | Contact number                  |

---

## 2️⃣ Matches Table

Stores information about football matches.

| Column Name         | Description                                  |
| ------------------- | -------------------------------------------- |
| match_id            | Unique identifier for each match             |
| fixture             | Competing teams                              |
| tournament_category | Tournament or league name                    |
| base_ticket_price   | Standard ticket price                        |
| match_status        | Available, Selling Fast, Sold Out, Postponed |

---

## 3️⃣ Bookings Table

Stores ticket booking transactions.

| Column Name    | Description                             |
| -------------- | --------------------------------------- |
| booking_id     | Unique booking identifier               |
| user_id        | References Users table                  |
| match_id       | References Matches table                |
| seat_number    | Assigned stadium seat                   |
| payment_status | Pending, Confirmed, Cancelled, Refunded |
| total_cost     | Total booking cost                      |

---

# 🔗 Database Relationships

### Users → Bookings

* One User can create multiple Bookings.
* Relationship: **One-to-Many (1:M)**

### Matches → Bookings

* One Match can have multiple Bookings.
* Relationship: **One-to-Many (1:M)**

### Users ↔ Matches

* A User can book multiple Matches.
* A Match can be booked by multiple Users.
* Relationship: **Many-to-Many (M:N)** through the Bookings table.

---

# 📊 ERD Structure

```text
Users
------
PK user_id

        1
        |
        |
        ∞
Bookings
---------
PK booking_id
FK user_id
FK match_id

        ∞
        |
        |
        1

Matches
--------
PK match_id
```

---

# 🛡️ Foreign Key Constraints

```sql
FOREIGN KEY (user_id)
REFERENCES Users(user_id);

FOREIGN KEY (match_id)
REFERENCES Matches(match_id);
```

### Benefits

* Prevents invalid bookings.
* Ensures every booking belongs to a valid user.
* Ensures every booking references an existing match.
* Maintains referential integrity.
* Prevents orphan records.

---

# 📝 SQL Queries Implemented

## Query 1

Retrieve all available Champions League matches.

### Concepts

* SELECT
* WHERE

---

## Query 2

Find users whose names start with "Tanvir" or contain "Haque".

### Concepts

* LIKE
* ILIKE

---

## Query 3

Retrieve bookings with missing payment status and replace NULL values with "Action Required".

### Concepts

* IS NULL
* COALESCE

---

## Query 4

Retrieve booking information with user names and match fixtures.

### Concepts

* INNER JOIN

---

## Query 5

Display all users and their booking IDs, including users without bookings.

### Concepts

* LEFT JOIN

---

## Query 6

Find bookings whose total cost is greater than the average booking cost.

### Concepts

* AVG()
* Subquery

---

# 🚀 Technologies Used

* PostgreSQL
* SQL
* Relational Database Design
* ERD (Entity Relationship Diagram)

---

# 🎯 Learning Outcomes

This assignment demonstrates:

* Database Schema Design
* Primary Keys
* Foreign Keys
* One-to-Many Relationships
* Many-to-Many Relationships
* SQL Filtering
* JOIN Operations
* Aggregate Functions
* Subqueries
* Data Integrity & Constraints

---

