# Hospital Management System

A C# console application for managing doctors, patients and appointments in a hospital. It uses an n-tier architecture, stores data in SQL Server through ADO.NET, and logs every add and delete operation using object serialization.

## Features

- Add, update, delete and display **patients**
- Add, update, delete and display **doctors** (with availability)
- **Book** and **cancel** appointments (booking only works if the doctor is available)
- Find the **most consulted doctor** (the one with the most appointments)
- Menu-driven interface for the Admin with 11 options
- Input validation and exception handling in every function

## Architecture

The project follows an **n-tier architecture**, with each class in its own file:

| Layer | Responsibility |
|---|---|
| Presentation | Console menu that shows options and reads input |
| Business Logic | `HospitalSystem` class that holds the rules (for example, a doctor must be available to book) |
| Models | `Doctor`, `Patient` and `Appointment` classes |
| Data Access | ADO.NET code that talks to SQL Server |

## Concepts Used

- **Object-oriented programming:** encapsulation (private fields with properties), constructors, and overriding `ToString()` from the base `object` class
- **ADO.NET:** database operations on SQL Server
- **Parameterized queries:** all user input is passed as parameters, which prevents SQL injection
- **Serialization:** each add or delete is saved to a text file with an `Added:` or `Deleted:` prefix
- **Exception handling and validation:** inputs are checked before they reach the database

## Database Tables

| Table | Columns |
|---|---|
| Doctor | DoctorID (PK), Name, Specialization, IsAvailable |
| Patient | PatientID (PK, auto increment), Name, CNIC (unique) |
| Appointment | AppointmentID (PK), DoctorID (FK), PatientCNIC (FK), AppointmentDate |

## Activity Logs

Changes are recorded in these files:

- `Patient.txt`
- `Doctor.txt`
- `Appointment.txt`

## How to Run

1. Install Visual Studio and SQL Server.
2. Create the database and the three tables above.
3. Update the connection string in the code to match your SQL Server.
4. Open the solution in Visual Studio and press **F5** to run.

## Built With

- C#
- .NET
- SQL Server
- ADO.NET

## About

Made for the Web Technologies course (SEF23), Homework 03, at the University of the Punjab.
