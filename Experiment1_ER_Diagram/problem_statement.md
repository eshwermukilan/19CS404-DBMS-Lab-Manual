# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

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
<img width="1102" height="935" alt="ER" src="https://github.com/user-attachments/assets/656f5aaa-7bcf-4adf-b81d-54272fe17253" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
| Member |MemberID (PK), Name, Email, Phone|Each member can borrow books and register for events.|
| Book   |BookID (PK), Title, Author|Represents books available in the library.|
| Loan   |LoanID (PK), LoanDate, ReturnDate, FineAmount, MemberID (FK), BookID (FK)|Associative entity between Member and Book for borrowing.|
| Event  |EventID (PK), EventName, EventDate, Description|Represents events organized by the library.|
| Speaker|SpeakerID (PK), Name, Profession|A speaker can be associated with multiple events.|
| Room   |RoomID (PK), RoomName, Capacity|Represents the physical rooms where events are held.|
| Registration|MemberID (FK), EventID (FK), RegistrationDate (optional)|Associative entity between Member and Event.|

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|  Loan        |   M:N      |  Partial      | Each loan record tracks borrow/return dates and fines.|
| Registration |   M:N      |  Optional     | Members register for events.|
| Event–Speaker|   M:N      |  Optional     | Events can have multiple speakers; a speaker can speak at multiple events.|
| Event–Room   |   M:1      |  Total        | A room can host multiple events (at different times).|

### Assumptions
1.Each Book has a unique BookID. A book may be borrowed multiple times but only one loan record exists per borrowing transaction.

2.Loan entity includes fine calculation (stored as FineAmount).

3.A Member may or may not borrow books or attend events.

4.An Event must be associated with at least one room, but it may or may not have a speaker.

5.A Speaker may present at multiple events, but some events may not have a speaker.

6.Each Registration links one member to one event; duplicate registrations are not allowed.

7.Room capacity is used for managing event participant limits, but it is not enforced directly in the ER model.

---
