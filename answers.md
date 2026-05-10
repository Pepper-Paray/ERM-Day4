Case Study 1: Event Management System
Entities and attributes
EVENT

EventID (PK)

Name

Description

Date

VenueID (FK → VENUE.VenueID)

VENUE

VenueID (PK)

Name

Address

MaxCapacity

ATTENDEE

AttendeeID (PK)

Name

Email

Phone

STAFF

StaffID (PK)

Name

Role

Email

EVENT_ATTENDEE (registration for events)

EventAttendeeID (PK)

EventID (FK → EVENT.EventID)

AttendeeID (FK → ATTENDEE.AttendeeID)

RegistrationDate

EVENT_STAFF (staff assignments)

EventStaffID (PK)

EventID (FK → EVENT.EventID)

StaffID (FK → STAFF.StaffID)

Relationships (cardinality)
EVENT–VENUE:

Each event is held at one venue.

A venue can host many events.

VENUE 1 ───< EVENT

EVENT–ATTENDEE (via EVENT_ATTENDEE):

An event has many attendees; an attendee can attend many events.

Many‑to‑many resolved by EVENT_ATTENDEE.

EVENT 1 ───< EVENT_ATTENDEE >───1 ATTENDEE

EVENT–STAFF (via EVENT_STAFF):

An event can have many staff; a staff member can work many events.

Many‑to‑many resolved by EVENT_STAFF.

EVENT 1 ───< EVENT_STAFF >───1 STAFF

ERD sketch (text)
text
VENUE 1 ───< EVENT >───1 EVENT_ATTENDEE >───1 ATTENDEE
              |
              >───1 EVENT_STAFF >───1 STAFF
Case Study 2: Online Learning Platform
Entities and attributes
STUDENT

StudentID (PK)

Name

Email

RegistrationDate

INSTRUCTOR

InstructorID (PK)

Name

Email

Department

COURSE

CourseID (PK)

Title

Description

CreditValue

InstructorID (FK → INSTRUCTOR.InstructorID)

ENROLLMENT (students in courses)

EnrollmentID (PK)

StudentID (FK → STUDENT.StudentID)

CourseID (FK → COURSE.CourseID)

ASSIGNMENT

AssignmentID (PK)

CourseID (FK → COURSE.CourseID)

Title

DueDate

MaxScore

SUBMISSION (student assignment submissions)

SubmissionID (PK)

AssignmentID (FK → ASSIGNMENT.AssignmentID)

StudentID (FK → STUDENT.StudentID)

SubmissionDate

Score

Relationships (cardinality)
COURSE–INSTRUCTOR:

Each course is taught by one instructor.

An instructor can teach many courses.

INSTRUCTOR 1 ───< COURSE

STUDENT–COURSE (via ENROLLMENT):

A student can enroll in many courses; a course can have many students.

Many‑to‑many resolved by ENROLLMENT.

STUDENT 1 ───< ENROLLMENT >───1 COURSE

COURSE–ASSIGNMENT:

A course can have many assignments.

Each assignment belongs to one course.

COURSE 1 ───< ASSIGNMENT

ASSIGNMENT–STUDENT (via SUBMISSION):

An assignment can be submitted by many students; a student can submit many assignments.

Many‑to‑many resolved by SUBMISSION.

ASSIGNMENT 1 ───< SUBMISSION >───1 STUDENT

ERD sketch (text)
text
INSTRUCTOR 1 ───< COURSE 1 ───< ASSIGNMENT 1 ───< SUBMISSION >───1 STUDENT
                      ^
                      >───< ENROLLMENT >───1 STUDENT
Case Study 3: Hotel Reservation System
Entities and attributes
GUEST

GuestID (PK)

Name

Email

Phone

ROOM

RoomID (PK)

RoomNumber

Type

PricePerNight

RESERVATION

ReservationID (PK)

GuestID (FK → GUEST.GuestID)

RoomID (FK → ROOM.RoomID)

CheckInDate

CheckOutDate

PaymentDate

PaymentAmount

PaymentMethod

SERVICE

ServiceID (PK)

Name

Description

RESERVATION_SERVICE (services used in a reservation)

ReservationServiceID (PK)

ReservationID (FK → RESERVATION.ReservationID)

ServiceID (FK → SERVICE.ServiceID)

Quantity

Relationships (cardinality)
GUEST–RESERVATION:

A guest can make many reservations.

Each reservation belongs to one guest.

GUEST 1 ───< RESERVATION

ROOM–RESERVATION:

A room can be reserved many times (different dates).

Each reservation is for one room.

ROOM 1 ───< RESERVATION

RESERVATION–SERVICE (via RESERVATION_SERVICE):

A reservation can include many services; a service can appear in many reservations.

Many‑to‑many resolved by RESERVATION_SERVICE.

RESERVATION 1 ───< RESERVATION_SERVICE >───1 SERVICE

ERD sketch (text)
text
GUEST 1 ───< RESERVATION >───1 ROOM
              |
              1 ───< RESERVATION_SERVICE >───1 SERVICE