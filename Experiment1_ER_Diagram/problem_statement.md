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
<img width="732" height="805" alt="image" src="https://github.com/user-attachments/assets/5327ea13-0a2c-4cf6-af86-837c3e5b5f4e" />

### Entities and Attributes
<img width="1142" height="277" alt="image" src="https://github.com/user-attachments/assets/525666d7-62b1-4c99-ae6d-f45145255b5f" />
      
### Relationships and Constraints
<img width="1261" height="348" alt="image" src="https://github.com/user-attachments/assets/eae79a77-e7ff-4958-a3d0-67d7cf07282d" />


### Assumptions
```
-Role-Based Access: Users have different roles (e.g., admin, trainer, member), with permissions assigned based on their role.
-Trainer-Managed Programs: Trainers manage fitness programs, and members can join multiple fitness types, each guided by a trainer.
-Flexible Member Participation: Members can participate in multiple fitness programs, with flexibility in the types and number of programs they join.
```
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

<img width="1261" height="280" alt="image" src="https://github.com/user-attachments/assets/07602180-5858-439f-87c0-cf3900c49558" />


### Relationships and Constraints

<img width="1267" height="352" alt="image" src="https://github.com/user-attachments/assets/64f402ae-457d-4d03-8684-4df5075baf45" />

### Assumptions
```
-Member-Book Loan System: A Member can borrow multiple Books with a Loan representing each borrowing transaction, which includes the loan and return dates.
-Event Participation: Members can register for multiple Events, and each Event can have multiple Members attending, with optional speakers.
-Speaker-Event Association: Events may feature one or more Speakers, and a Speaker can be involved in multiple Events.
```

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

<img width="1021" height="416" alt="image" src="https://github.com/user-attachments/assets/a84bb5dc-5846-4e81-b6a4-903c61768b9f" />


### Relationships and Constraints

<img width="915" height="322" alt="image" src="https://github.com/user-attachments/assets/93c1c974-748c-4f49-bd20-67228a44ece9" />


### Assumptions
```
-Each reservation occupies one table only.
-Bills always generated per reservation.
-Service charges fixed percentage (not modeled).
```
---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
