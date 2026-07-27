# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.



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
<img width="1111" height="747" alt="Screenshot 2026-07-27 113923" src="https://github.com/user-attachments/assets/ead9fe41-77e2-40f2-968b-583c0e3d49bc" />

### Entities and Attributes

| Entity              | Attributes (PK, FK)                                         | Notes                                                            |
| ------------------- | ----------------------------------------------------------- | ---------------------------------------------------------------- |
| **MEMBER**          | **MemberID (PK)**, Name, MembershipType                     | Stores information about gym members.                            |
| **PROGRAM**         | **ProgramID (PK)**, ProgramName, Schedule                   | Stores details of fitness programs.                              |
| **SESSION**         | **SessionID (PK)**, SessionDate, Time, TrainerID (FK)       | Represents individual training sessions.                         |
| **TRAINER**         | **TrainerID (PK)**, TrainerName, Phone                      | Stores trainer information.                                      |
| **PAYMENT**         | **PaymentID (PK)**, PaymentDate, Amount, MemberID (FK)      | Records payments made by members.                                |
| **MEMBER_PROGRAM**  | **MemberID (PK, FK)**, **ProgramID (PK, FK)**, JoinDate     | Associative entity representing member enrolment in programs.    |
| **TRAINER_PROGRAM** | **TrainerID (PK, FK)**, **ProgramID (PK, FK)**, ProgramDate | Associative entity representing trainer assignments to programs. |


### Relationships and Constraints

| Relationship                                       | Cardinality | Participation                              | Notes                                                                                |
| -------------------------------------------------- | ----------- | ------------------------------------------ | ------------------------------------------------------------------------------------ |
| **Joins (MEMBER – MEMBER_PROGRAM)**                | 1 : M       | MEMBER – Partial, MEMBER_PROGRAM – Total   | A member can join multiple programs; each enrolment belongs to one member.           |
| **Program Enrolment (PROGRAM – MEMBER_PROGRAM)**   | 1 : M       | PROGRAM – Partial, MEMBER_PROGRAM – Total  | A program can have many enrolled members.                                            |
| **Books (MEMBER – SESSION)**                       | M : N       | Partial – Partial                          | Members can book multiple sessions, and a session can be booked by multiple members. |
| **Makes (MEMBER – PAYMENT)**                       | 1 : M       | MEMBER – Partial, PAYMENT – Total          | A member can make multiple payments; each payment belongs to one member.             |
| **Assigned (PROGRAM – TRAINER_PROGRAM)**           | 1 : M       | PROGRAM – Partial, TRAINER_PROGRAM – Total | A program can be assigned to multiple trainers over time.                            |
| **Trainer Assignment (TRAINER – TRAINER_PROGRAM)** | 1 : M       | TRAINER – Partial, TRAINER_PROGRAM – Total | A trainer can be assigned to multiple programs.                                      |
| **Conducts (TRAINER – SESSION)**                   | 1 : M       | TRAINER – Partial, SESSION – Total         | One trainer conducts many sessions; each session is conducted by one trainer.        |


### Assumptions
A member may enrol in multiple fitness programs, and each program may have multiple members.
Each session is conducted by only one trainer, but a trainer can conduct many sessions.
Payments are made only by registered members.
Trainer assignments to programs are maintained using the TRAINER_PROGRAM associative entity.
The MEMBER_PROGRAM entity stores the date on which a member joined a program.

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
*Paste or attach your diagram here*  <img width="1115" height="782" alt="Screenshot 2026-07-27 113934" src="https://github.com/user-attachments/assets/309fb511-3e96-41c2-ae62-995fe6e9d129" />


### Entities and Attributes

| Entity        | Attributes (PK, FK)                                               | Notes                                                    |
| ------------- | ----------------------------------------------------------------- | -------------------------------------------------------- |
| **MEMBER**    | **MemberID (PK)**, Name, Email                                    | Stores details of library members.                       |
| **BOOK**      | **BookID (PK)**, Title, Author                                    | Stores information about books available in the library. |
| **BOOK_LOAN** | **LoanID (PK)**, LoanDate, ReturnDate, MemberID (FK), BookID (FK) | Records book borrowing transactions.                     |
| **EVENT**     | **EventID (PK)**, EventName, EventDate                            | Stores details of library events.                        |
| **SPEAKER**   | **SpeakerID (PK)**, SpeakerName, Role                             | Stores information about event speakers.                 |
| **ROOM**      | **RoomID (PK)**, RoomName, RoomType                               | Stores details of rooms used for events.                 |


### Relationships and Constraints

| Relationship                     | Cardinality | Participation                       | Notes                                                                                           |
| -------------------------------- | ----------- | ----------------------------------- | ----------------------------------------------------------------------------------------------- |
| **Borrows (MEMBER – BOOK_LOAN)** | 1 : M       | MEMBER – Partial, BOOK_LOAN – Total | A member can borrow multiple books; each loan belongs to one member.                            |
| **Lend (BOOK – BOOK_LOAN)**      | 1 : M       | BOOK – Partial, BOOK_LOAN – Total   | A book can be loaned multiple times over time; each loan refers to one book.                    |
| **Register (MEMBER – EVENT)**    | M : N       | Partial – Partial                   | Members can register for multiple events, and each event can have multiple registered members.  |
| **Has (EVENT – SPEAKER)**        | M : N       | Partial – Partial                   | An event can have multiple speakers, and a speaker can participate in multiple events.          |
| **Booked In (SPEAKER – ROOM)**   | M : 1       | SPEAKER – Total, ROOM – Partial     | Multiple speakers may be assigned to the same room, while each speaker is assigned to one room. |


### Assumptions
A member may borrow multiple books, but each loan record is associated with only one member and one book.
Books can be borrowed multiple times on different loan transactions.
Members may register for multiple library events, and each event can have many registered members.
An event can feature multiple speakers, and speakers may participate in multiple events.
Each speaker is assigned to one room for an event, while a room may accommodate multiple speakers.

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
<img width="1077" height="693" alt="Screenshot 2026-07-27 113948" src="https://github.com/user-attachments/assets/ba3a8097-0ac0-42ae-8daf-ba72816cb1ee" />


### Entities and Attributes
| Entity          | Attributes (PK, FK)                                                | Notes                                            |
| --------------- | ------------------------------------------------------------------ | ------------------------------------------------ |
| **CUSTOMER**    | **CustomerID (PK)**, Name, Phone                                   | Stores customer information.                     |
| **RESERVATION** | **ReservationID (PK)**, Date, Time, CustomerID (FK), WaiterID (FK) | Stores table reservation details.                |
| **WAITER**      | **WaiterID (PK)**, Name, Phone                                     | Stores waiter information.                       |
| **ORDER**       | **OrderID (PK)**, OrderTime, Status, ReservationID (FK)            | Stores customer food orders.                     |
| **DISH**        | **DishID (PK)**, DishName, Category                                | Stores menu items offered by the restaurant.     |
| **BILL**        | **BillID (PK)**, BillDate, Amount, OrderID (FK)                    | Stores billing information generated for orders. |


### Relationships and Constraints

| Relationship                           | Cardinality | Participation                           | Notes                                                                                  |
| -------------------------------------- | ----------- | --------------------------------------- | -------------------------------------------------------------------------------------- |
| **Makes (CUSTOMER – RESERVATION)**     | 1 : M       | CUSTOMER – Partial, RESERVATION – Total | A customer can make multiple reservations; each reservation belongs to one customer.   |
| **Assigned To (WAITER – RESERVATION)** | 1 : M       | WAITER – Partial, RESERVATION – Total   | A waiter can handle multiple reservations; each reservation is assigned to one waiter. |
| **Places (RESERVATION – ORDER)**       | 1 : M       | RESERVATION – Partial, ORDER – Total    | A reservation can have multiple orders; each order belongs to one reservation.         |
| **Contains (ORDER – DISH)**            | M : N       | Partial – Partial                       | An order may contain multiple dishes, and a dish can appear in multiple orders.        |
| **Generates (ORDER – BILL)**           | 1 : 1       | Total – Total                           | Each order generates one bill, and each bill corresponds to one order.                 |


### Assumptions
A customer may make multiple reservations, but each reservation is made by only one customer.
Every reservation is assigned to exactly one waiter, while a waiter can manage multiple reservations.
Each reservation can include multiple food orders.
An order can contain multiple dishes, and the same dish can appear in many different orders.
Every completed order generates exactly one bill, and each bill belongs to only one order.

---

## RESULT

The experiment has been executed successfully and the ER diagrams were designed for all the given scenarios. The entities, attributes, relationships, and constraints were identified correctly. Thus, the database models were created successfully for the real-world applications
