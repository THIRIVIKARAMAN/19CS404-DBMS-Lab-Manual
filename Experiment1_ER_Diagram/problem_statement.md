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
*Paste or attach your diagram here*  
<img width="3840" height="599" alt="Untitled diagram _ Mermaid Chart-2025-09-01-022128" src="https://github.com/user-attachments/assets/391ee2f0-454d-4375-87a3-fc4111c79535" />

![ER Diagram](er_diagram_fitness.png)

### Entities and Attributes

| Entity | Attributes (PK, FK)|             Notes                      |
|--------|--------------------|----------------------------------------|
|Member  | MemberID (PK)      | Members registered in gym              |
|Program | ProgramID (PK)     | Fitness programs like Yoga, Zumba      |
|Trainer | TrainerID (PK)     | Trainers assigned to programs          |
|Session | SessionID (PK)     | Personal training / attendance session |
|Payment | PaymentID (PK)     | Tracks membership & session payments   |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|Member – Program       |M:N            |Optional               |A member can join many programs, and a program can have many members       |
|Program – Trainer              | M:N           |Mandatory               |A program may have multiple trainers, and trainers can handle multiple programs       |
|Member – Session              |1:N            |Optional               |A member can book many sessions       |
|Trainer – Session|1:N|Mandatory|A trainer conducts many sessions|
|Member – Payment|1:N|Mandatory|A member can make many payments|
### Assumptions
- A program must have at least one trainer.

- A session is always linked to a trainer.

- Payments cover memberships or personal sessions. 

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

| Entity       | Attributes (PK, FK)                           | Notes                                 |
|--------------|-----------------------------------------------|---------------------------------------|
| Member       | MemberID (PK)                                | Library members                       |
| Book         | BookID (PK)                                  | Each book copy tracked individually   |
| Loan         | LoanID (PK), BookID (FK), MemberID (FK)      | Tracks book borrow/return             |
| Event        | EventID (PK)                                 | Cultural/library events                |
| Speaker      | SpeakerID (PK)                               | Guest speakers/authors                 |
| Room         | RoomID (PK)                                  | Rooms for events/study                |
| Registration | RegID (PK), EventID (FK), MemberID (FK)      | Members registering for events        |

### Relationships and Constraints

| Relationship        | Cardinality | Participation | Notes                                               |
|---------------------|-------------|---------------|-----------------------------------------------------|
| Member – Loan – Book| M:N via Loan| Mandatory     | Members borrow books, tracked by Loan table         |
| Member – Event      | M:N via Registration | Optional | Members can register for events                     |
| Event – Speaker     | M:N         | Mandatory     | Events may have multiple speakers                   |
| Event – Room        | 1:1         | Mandatory     | Each event is assigned one room                     |
| Loan – Fine         | 1:1         | Optional      | Fine applied if book returned late                  |

### Assumptions
- Each book copy has a unique BookID.  
- Events cannot be held without a room allocation.  
- Fines are stored in the Loan table.  
  
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

| Entity       | Attributes (PK, FK)                          | Notes                                 |
|--------------|----------------------------------------------|---------------------------------------|
| Customer     | CustomerID (PK)                             | Restaurant customers                  |
| Reservation  | ReservationID (PK), CustomerID (FK), TableID (FK) | Table booking details           |
| Table        | TableID (PK)                                | Dining tables                         |
| Order        | OrderID (PK), ReservationID (FK)            | Food order per reservation            |
| Dish         | DishID (PK)                                 | Food items (starter, main, dessert)   |
| OrderDetail  | OrderDetailID (PK), OrderID (FK), DishID (FK)| Junction table for orders and dishes  |
| Bill         | BillID (PK), ReservationID (FK)             | Final billing for reservation         |
| Waiter       | WaiterID (PK)                               | Assigned waiters                      |

### Relationships and Constraints

| Relationship         | Cardinality | Participation | Notes                                         |
|----------------------|-------------|---------------|-----------------------------------------------|
| Customer – Reservation | 1:N       | Optional      | A customer can make multiple reservations     |
| Reservation – Table    | 1:1       | Mandatory     | Each reservation is tied to one table         |
| Reservation – Order    | 1:N       | Mandatory     | One reservation can include many orders       |
| Order – Dish           | M:N via OrderDetail | Mandatory | An order can include many dishes              |
| Reservation – Bill     | 1:1       | Mandatory     | One bill generated per reservation            |
| Reservation – Waiter   | 1:N       | Optional      | A waiter serves one or more reservations      |

### Assumptions
- One reservation corresponds to exactly one table.  
- Bills are generated per reservation, not per order.  
- One waiter usually serves one reservation, but may serve many across the shift.  

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
