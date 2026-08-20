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
<img width="752" height="832" alt="DBMS-ERD(CF)1 drawio" src="https://github.com/user-attachments/assets/667b506d-0dc0-46d9-93e4-553746f8959b" />

### Entities and Attributes

1. Member -  Member ID(PK), Name, Gender, Join Date, Phone(Multivalued), Age(Derived)
2. Fitness Program -  Program ID (PK)  , Program Name, Fee, Duration
3. Trainer -  Trainer ID (PK), Name, Phone(Multivalued), Specialization, Experience
4. Training Session -  Session ID (PK), Member ID (FK), Trainer ID (FK), Date, Time, Type
5. Attendance -  Attendance ID (PK), Session ID (FK), Attendance Date, Status, Remarks
6.  Payment -  Payment ID (PK)  , Member ID (FK), Amount, Payment Date, Payment Mode
   
   
### Relationships and Constraints
    Relationship                |  Cardinality |   Participation              Notes
1. Member – Fitness Program     |   M : N      |Partial on both sides      |Members can enroll in multiple fitness programs, and each program can have multiple members.
2. Fitness Program – Trainer    |   M : N      | Partial                   |Trainers can be assigned to multiple fitness programs.
3. Member – Training Session    |   1 : M      | Total on Training Session | Each training session must be associated with a member.
4. Trainer – Training Session   |   1 : M      | Total on Training Session |Each training session must be conducted by a trainer.
5. Training Session – Attendance|   1 : M      |  Total on Attendance      | Attendance records are maintained for training sessions.
6. Member – Payment             |   1 : M      | Total on Payment          | Each payment must be associated with a member.

### Assumptions

 A member can enroll in multiple fitness programs. 
 
 A trainer can conduct multiple fitness programs. 
 
 Every training session is associated with one member and one trainer. 
 
 Attendance is recorded for each training session. 
 
 Members can make multiple payments for memberships or training sessions. 
 
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
<img width="742" height="832" alt="DBMS-ERD(CL) drawio" src="https://github.com/user-attachments/assets/59e0500b-21df-4f03-9b9d-80de0385d2f5" />

### Entities and Attributes

1. Member -  Member ID (PK)  , Name, Email, Phone (Multivalued)
2. Book   -  Book ID (PK)  , Title, Author, Category
3. Loan   -  Loan ID (PK)  , Member ID (FK), Book ID (FK), Loan Date, Return Date, Fine Amount, Days Overdue  (Derived)
4. Event  -  Event ID (PK)  , Room ID (FK), Name, Date, Time
5. Speaker-  Speaker ID (PK)  , Event ID (FK), Name, Contact  (Multivalued)  , Expertise
6.  Room  -  Room ID (PK)  , Room Name, Capacity, Purpose

### Relationships and Constraints
    Relationship   | Cardinality| Participation     |  Notes
1. Member – Loan   |  1 : M    | Total on Loan      | Each loan must belong to one member.
2. Book – Loan     |  1 : M    | Total on Loan      | Each loan must refer to one book.
3. Member – Event  |  M : N    | Partial            | Members can register for multiple library events.
4. Event – Speaker |  1 : M    | Total on Speaker   | Each speaker is associated with an event.
5. Room – Event    |  1 : M    | Total on Event     | Each event must be assigned to a room.
6. Member – Book   |  M : N    | Total on both sides| Members can borrow many books, and books can be borrowed by many members over time through loans.

### Assumptions
 A member can borrow multiple books. 
 
 Each loan record is associated with one member and one book.
 
 Members can register for multiple events. 
 
 Every event is conducted in one room. 
 
 Fine amount is maintained for overdue book returns.

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
<img width="762" height="802" alt="DBMS-ERD(RES) drawio" src="https://github.com/user-attachments/assets/b207243c-d481-4b63-ab13-5b7f0a48d2cb" />

### Entities and Attributes

1.  Customer  -  Customer ID(PK), Name, Email, Phone(Multivalued)
2.  Reservation -  Reservation ID(PK), Customer ID(FK), Waiter ID(FK), Date, Time, Number of guests
3.  Dish       -  Dish ID(PK) , Dish Name, Category, Price
4.  Order      -  Order ID (PK)  , Dish ID (FK), Reservation ID(FK), Time, Total Items(Derived)
5.  Waiter     -  Waiter ID(PK)  , Name, Phone(Multivalued) , Shift
6.  Bill       -  Bill (PK), Reservation ID (FK), Payment Details / Attributes

### Relationships and Constraints
   Relationship            Cardinality  Participation          Notes
1. Customer – Reservation  | 1 : M  | Total on Reservation  | Each reservation must be linked to a customer.
2. Reservation – Order     | 1 : M  | Partial               | A reservation may have multiple food orders.
3. Order – Dish            | M : N  | Total on Order        | An order can contain multiple dishes, and dishes can appear in multiple orders.
4. Waiter – Reservation    | 1 : M  | Total on Reservation  | A waiter can serve multiple reservations.
5. Reservation – Bill      | 1 : 1  | Total on Bill         | Every reservation generates exactly one bill.
6. Customer – Bill         | 1 : M  | Partial               | A customer can have multiple bills for different reservations.

### Assumptions
 Customers can reserve tables in advance or walk in. 
 
 A reservation may contain multiple food orders. 
 
 Each order can include multiple dishes. 
 
 One waiter can serve multiple reservations during a shift. 
 
 Each reservation generates exactly one bill. 
 
 Total amount is calculated using food and service charges.

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
