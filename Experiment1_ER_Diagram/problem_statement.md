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

<img width="772" height="942" alt="image" src="https://github.com/user-attachments/assets/75db56e4-6613-49c4-822c-4a8f2dc3480d" />

### Entities and Attributes

| Entity       | Attributes (PK, FK)                                | Notes                            |
| ------------ | -------------------------------------------------- | -------------------------------- |
| Member       | **Member_ID (PK)**, Member_Name, Phone_no          | Phone_no is multivalued          |
| Loan         | **Loan_ID (PK)**, Loan_Date, Return_Date           | Loan transaction details         |
| Book         | **Book_ID (PK)**, Book_Title, Author               | Book details                     |
| Event        | **Event_ID (PK)**, Event_Name, Duration            | Library event details            |
| Room         | **Room_no (PK)**, Room_Name, Capacity              | Room details                     |
| Speaker      | **Speaker_ID (PK)**, Speaker_Name, Speech_Duration | Speaker details                  |
| Overdue_Fine | —                                                  | Fine associated with late return |


### Relationships and Constraints

| Relationship                    | Cardinality | Participation                      | Notes                              |
| ------------------------------- | ----------- | ---------------------------------- | ---------------------------------- |
| Take (Member–Loan)              | 1 : N       | Member – Partial, Loan – Total     | A member can take multiple loans   |
| Borrow (Loan–Book)              | N : 1       | Loan – Total, Book – Partial       | A loan is associated with a book   |
| Late_Return (Book–Overdue_Fine) | 1 : 1       | Partial                            | Fine is applicable for late return |
| Register (Member–Event)         | N : M       | Partial                            | Members can register for events    |
| Have (Event–Speaker)            | N : M       | Event – Partial, Speaker – Partial | Events can have multiple speakers  |
| Booked (Event–Room)             | N : 1       | Event – Total, Room – Partial      | An event is booked in a room       |


### Assumptions
- A member can borrow multiple books through separate loan transactions.
- A member can register for multiple library events.
- An event may have one or more speakers and is conducted in a booked room.

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

<img width="842" height="852" alt="image" src="https://github.com/user-attachments/assets/a567220f-ece3-4c67-821c-30504a63caa6" />


### Entities and Attributes

| Entity      | Attributes (PK, FK)                                    | Notes                               |
| ----------- | ------------------------------------------------------ | ----------------------------------- |
| Customer    | **Customer_ID (PK)**, Customer_Name, Phone_no          | Phone_no is multivalued             |
| Reservation | Date, Time, No_of_Guests                               | Reservation details                 |
| Food_Order  | **Order_ID (PK)**, **Reservation_ID (FK)**, Order_Time | Food order placed for a reservation |
| Table       | **Table_ID (PK)**, Table_Name, Capacity                | Restaurant table details            |
| Bills       | Payment_Method, Service_Charge, Food_Charge            | Bill generated for food order       |
| Waiters     | **Waiter_ID (PK)**, Name, Phone_no                     | Phone_no is multivalued             |
| Dishes      | Starter, Main_Dish, Dessert                            | Dishes available in restaurant      |


### Relationships and Constraints

| Relationship                   | Cardinality | Participation                             | Notes                                       |
| ------------------------------ | ----------- | ----------------------------------------- | ------------------------------------------- |
| Book (Customer–Reservation)    | 1 : N       | Customer – Partial, Reservation – Total   | One customer can make multiple reservations |
| Place (Reservation–Food_Order) | 1 : N       | Reservation – Partial, Food_Order – Total | A reservation can have multiple food orders |
| Assign (Reservation–Table)     | N : 1       | Reservation – Total, Table – Partial      | A reservation is assigned to a table        |
| Generate (Food_Order–Bills)    | 1 : 1       | Total                                     | Each food order generates a bill            |
| Serve (Food_Order–Waiters)     | N : 1       | Food_Order – Total, Waiter – Partial      | A waiter serves food orders                 |
| Per_Order (Food_Order–Dishes)  | N : M       | Partial                                   | An order can contain multiple dishes        |


### Assumptions
- A customer can make one or more reservations.
- Each reservation is assigned to a table and can have food orders.
- Each food order generates a bill and contains one or more dishes.

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
