# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:  
<img width="717" height="588" alt="Screenshot 2025-09-22 132923" src="https://github.com/user-attachments/assets/73881bb6-b333-4f08-a9cb-6206fe4db490" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
| Member       |         Member_ID (PK), Name, MembershipType, StartDate           |    Stores details of gym members   |
| Program       |         Trainer_ID (PK), Name           |    Each trainer conducts programs   |
| Attendance       |      Attendance_ID (PK, FK Member_ID, FK Trainer_ID)              |   Records which member attended which program    |
| Payment       |   Payment_ID (PK, FK Member_ID), MembershipFee, SessionFee                 | Tracks payment details for each member      |


### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|  Joins (Member–Program)            |  1:N (Member to Program), N:M overall          |  Member must join at least one Program             | Many members can join many programs      |
|  Conducts (Program–Attendance)            | 1:M (Program to Attendance)           |   Mandatory            | Each program has multiple attendance records      |
|  Is Booked By (Attendance–Member)            |  1:N          |    Mandatory           |   Each attendance is linked to a member    |
| Tracked For (Attendance–Payment)             |   1:N         |    Optional           | Payments are tracked per attendance      |
| Is Recording (Attendance–Payment)             |   1:N         |    Optional           |  Payment details are recorded for attendance     |

### Assumptions
A member can join multiple programs (e.g., Yoga, Zumba, Weight Training).

A trainer can conduct multiple programs, but each program is managed by one trainer.

Attendance is uniquely identified by Attendance_ID and linked to both Member and Program.

Payments are made either for membership or for individual sessions.


# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_library.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_restaurant.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
