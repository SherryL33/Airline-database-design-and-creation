# Airline-database-design-and-creation
## Table of Content
- [Project Overview](#Project-Overview)
- [Tools Used](#Tools-Used)
- [User Requirements](#User-Requirements)
- [Entities and Attributes](#Entities-and-Attributes)
- [Database Analyst User Requirement Interpretation](#Database-Analyst-User-Requirement-Interpretation)
- [Database ER Model Diagram](#Database-ER-Model-Diagram )
- [Creation of the Database](#Creation-of-the-Database)
- [Creation of the Database Entities Attributes and Values](#Creation-of-the-Database-Entities-Attributes-and-Values)
- [Coding SQL Statement to Generate reports](#Coding-SQL-Statement-to-Generate-reports)

### Project Overview
SkyHigh Airways is a commercial airline that operates domestic and international flights. The airline serves a wide variety of passengers and offers multiple flight classes, including economy, business, and first class. SkyHigh Airways aims to provide an efficient and comfortable travel experience, supported by a team of dedicated crew members, airport staff, and a customer service team. To streamline operations and manage customer interactions, the airline needs a comprehensive database to track flights, reservations, aircraft, and other key aspects of its business.

### Tools Used
- The DBMS used is MariaDB Server.
- The user interface used is HeidiSQL.
- Used Draw.io for the ER diagram model.

### User Requirements 
The requirement-gathering process was conducted with SkyHigh Airways staff to determine their expectations from the database. The airline operations manager started by explaining the operating environment of SkyHigh Airways as follows:
1. Each passenger is assigned a unique passenger ID and may have multiple reservations across different flights.
2. Reservations are made through the airline's reservation system and are identified by a unique reservation ID, with statuses such as confirmed, pending, or canceled.
3. A reservation belongs to a single passenger but can include one or more flights within the passenger’s itinerary.
4. The airline owns a fleet of aircraft, each with a unique aircraft ID, model, seating capacity, and maintenance schedule.
5. Each flight is assigned a single aircraft, while an aircraft may operate multiple flights over time.
6. Crew members, identified by a unique employee ID, are assigned to flights based on their roles, and each flight has multiple crew members assigned.
7. Each reservation generates a ticket with a unique ticket number, specifying the flight class and fare. A ticket is associated with only one passenger and one reservation.
8. The airline offers a frequent flyer program, where each frequent flyer account has a unique account ID, a status level (silver, gold, platinum), and accumulated miles.
9. A passenger may have a frequent flyer account, but each frequent flyer account is linked to only one passenger.

#### Major Reports Required:
##### Daily Flight Operations Report:
At the end of each day, airline staff must submit a report detailing all completed flights, including flight numbers, departure and arrival times, assigned aircraft, and the names and IDs of assigned crew members.

##### Monthly Passenger Reservation Report:
A comprehensive report is generated at the end of each month, summarizing all passenger reservations, including reservation IDs, booking statuses, and the number of flights per reservation.

##### Yearly Frequent Flyer Summary:
An annual report is compiled at the end of the year, providing an overview of frequent flyer members, including their account IDs, status levels, and total miles accumulated or redeemed.

##### Aircraft Maintenance Schedule:
Aircraft are systematically monitored based on their maintenance schedules, ensuring that each aircraft undergoes inspections and servicing at the designated intervals.

### Entities and Attributes 
#### PASSENGER
- Passenger ID
- First Name
- Last Name
- Date of Birth
- Email
#### FREQUENT FLYER ACCOUNT
- Account ID
- Status Level
- Accumulated Miles
- Passenger ID (FK)
#### RESERVATION
- Reservation ID
- Booking Date
- Status
- Passenger ID (FK)
#### TICKET
- Ticket ID
- Flight Class
- Fare
- Reservation ID (FK)
- Passenger ID (FK)
#### RESERVATION FLIGHT
- Reservation Flight ID
- Reservation ID (FK)
- Flight ID (FK)
#### FLIGHT
- Flight ID
- Flight Number
- Departure Time
- Arrival Time
- Route
#### AIRCRAFT
- Aircraft ID
- Model
- Capacity
- Maintenance Schedule
#### CREW ASSIGNMENT
- Assignment ID
- Flight ID (FK)
- Employee ID (FK)
#### CREWMEMBERS
- Employee ID
- First Name
- Last Name
- Position

### Database Analyst User Requirement Interpretation
1. A passenger can have multiple reservations, but each reservation is associated with exactly one passenger (One-to-Many relationship).
2. A reservation can include multiple flights, and a flight can be part of multiple reservations (Many-to-Many relationship).
3. Each flight is assigned exactly one aircraft, but an aircraft can operate multiple flights over time (One-to-Many relationship).
4. A flight can have multiple crew members assigned, and each crew member can be assigned to multiple flights (Many-to-Many relationship).
5. A passenger can have at most one frequent flyer account, and each frequent flyer account is linked to exactly one passenger (One-to-One relationship).
6. Each ticket is associated with exactly one reservation and one passenger (One-to-One relationship).

### Database ER Model Diagram 
###### The construction of the database using Draw.io Workbench Model Editor
![f158348e02c073c83a6b57e79af93cc](https://github.com/user-attachments/assets/bc97d82a-4aec-4bfd-b6d6-c408e296de3b)


### Creation of the Database

