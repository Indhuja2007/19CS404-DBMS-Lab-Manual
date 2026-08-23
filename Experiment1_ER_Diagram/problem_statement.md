# ER Diagram Workshop – Submission Template
# NAME : INDHUJA.K
# Register no : 212225040133
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

<img width="822" height="922" alt="image" src="https://github.com/user-attachments/assets/17350024-2579-4a34-a45b-a876fe14f6de" />

### Entities and Attributes

| Entity     | Attributes (PK, FK)                       | Notes                      |
| ---------- | ----------------------------------------- | -------------------------- |
| Members    | Name, Membership_Type, Start_Date         | Member details             |
| Programs   | Yoga, Zumba, Weight_Training              | Available fitness programs |
| Session    | Session_Date, Session_Time, Duration      | Session details            |
| Trainers   | **Trainer_ID (PK)**, Name, Phone_no       | Phone_no is multivalued    |
| Payment    | **Payment_ID (PK)**, Payment_Type, Amount | Payment details            |
| Attendance | —                                         | Records attendance         |


### Relationships and Constraints

| Relationship                | Cardinality | Participation                      | Notes                                      |
| --------------------------- | ----------- | ---------------------------------- | ------------------------------------------ |
| Register (Members–Programs) | N : M       | Partial                            | Members can register for multiple programs |
| Assign (Programs–Trainers)  | N : M       | Partial                            | Trainers can be assigned to programs       |
| Book (Session–Trainers)     | N : 1       | Session – Total, Trainer – Partial | A session is conducted by a trainer        |
| Fees (Session–Payment)      | 1 : 1       | Total                              | Payment is associated with a session       |
| Record (Session–Attendance) | 1 : 1       | Total                              | Attendance is recorded for a session       |

### Assumptions
- A member can register for multiple fitness programs.
- A program can have multiple trainers.
- Each session has a scheduled date, time and duration.
- Payment is recorded for the session.

---

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
