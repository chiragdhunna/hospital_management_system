# Hospital Management System

This repository is a practice project for learning FastAPI by building the backend for a hospital management system.

The goal is to design a clean, maintainable API that can support the core workflows of a hospital, including patient registration, doctor management, appointments, admissions, medical records, and billing. The project is intentionally structured like a real backend service so it can be used to practice API design, database modeling, validation, authentication, and scalable Python application patterns.

## Project Goals

- Learn FastAPI by building a realistic backend application.
- Practice writing REST APIs with validation, dependency injection, and layered architecture.
- Model common hospital workflows in a way that is easy to extend.
- Keep the codebase organized so future features can be added without rewriting the core structure.

## What This Backend Covers

This system is planned to manage the main operational parts of a hospital:

- Patient registration and profile management
- Doctor and staff records
- Department and specialization data
- Appointment scheduling and status tracking
- Inpatient admission and discharge flow
- Medical history and clinical notes
- Prescription and treatment records
- Billing, invoices, and payment tracking
- Authentication and role-based access control

## Planned Tech Stack

- FastAPI for the API framework
- Pydantic for request and response validation
- SQLAlchemy or SQLModel for persistence
- Alembic for database migrations
- PostgreSQL for the database
- Uvicorn as the ASGI server
- JWT-based authentication for protected endpoints

## Suggested Project Structure

The codebase will follow a modular layout so each business area stays separate:

- `app/main.py` for application startup and route registration
- `app/core/` for configuration, security, and shared utilities
- `app/models/` for database models
- `app/schemas/` for request and response schemas
- `app/api/` for route handlers
- `app/services/` for business logic
- `app/crud/` for database operations
- `app/db/` for session and engine setup
- `app/tests/` for automated tests

## Core API Modules

### Authentication

This module will handle user login and access control for staff members such as admins, doctors, and receptionists.

Planned endpoints:

- `POST /auth/register` to create a new user account
- `POST /auth/login` to issue access tokens
- `GET /auth/me` to return the current logged-in user
- `POST /auth/logout` to invalidate the current session if token revocation is implemented

### Patients

This module stores patient demographics, contact information, emergency contacts, and basic medical details.

Planned endpoints:

- `POST /patients` to create a patient record
- `GET /patients` to list patients
- `GET /patients/{patient_id}` to fetch a single patient
- `PUT /patients/{patient_id}` to update a patient record
- `DELETE /patients/{patient_id}` to remove or deactivate a patient

### Doctors

This module manages doctor profiles, departments, qualifications, and consultation availability.

Planned endpoints:

- `POST /doctors` to create a doctor profile
- `GET /doctors` to list doctors
- `GET /doctors/{doctor_id}` to fetch doctor details
- `PUT /doctors/{doctor_id}` to update doctor information
- `DELETE /doctors/{doctor_id}` to remove or deactivate a doctor

### Departments

This module organizes the hospital into functional units such as cardiology, pediatrics, and orthopedics.

Planned endpoints:

- `POST /departments` to create a department
- `GET /departments` to list departments
- `GET /departments/{department_id}` to fetch department details
- `PUT /departments/{department_id}` to update a department
- `DELETE /departments/{department_id}` to remove a department

### Appointments

This module manages patient bookings with doctors and supports scheduling workflows.

Planned endpoints:

- `POST /appointments` to book an appointment
- `GET /appointments` to list appointments
- `GET /appointments/{appointment_id}` to fetch one appointment
- `PUT /appointments/{appointment_id}` to reschedule or update status
- `DELETE /appointments/{appointment_id}` to cancel an appointment

Common appointment fields will include:

- Patient
- Doctor
- Appointment date and time
- Visit reason
- Status such as booked, completed, cancelled, or missed

### Admissions

This module handles inpatient admission, ward assignment, and discharge flow.

Planned endpoints:

- `POST /admissions` to admit a patient
- `GET /admissions` to list admissions
- `GET /admissions/{admission_id}` to fetch admission details
- `PUT /admissions/{admission_id}` to update admission information
- `POST /admissions/{admission_id}/discharge` to discharge a patient

### Medical Records

This module stores clinical notes, diagnoses, treatment plans, and patient history.

Planned endpoints:

- `POST /medical-records` to create a medical record entry
- `GET /medical-records` to list records
- `GET /medical-records/{record_id}` to fetch a record
- `PUT /medical-records/{record_id}` to update a record
- `DELETE /medical-records/{record_id}` to delete a record if allowed

### Prescriptions

This module tracks medicines prescribed during consultations or admissions.

Planned endpoints:

- `POST /prescriptions` to create a prescription
- `GET /prescriptions` to list prescriptions
- `GET /prescriptions/{prescription_id}` to fetch prescription details
- `PUT /prescriptions/{prescription_id}` to update a prescription
- `DELETE /prescriptions/{prescription_id}` to remove a prescription

### Billing

This module manages invoices, charges, and payment status for patient services.

Planned endpoints:

- `POST /bills` to create a bill or invoice
- `GET /bills` to list bills
- `GET /bills/{bill_id}` to fetch bill details
- `PUT /bills/{bill_id}` to update bill information
- `POST /bills/{bill_id}/payment` to record a payment

## API Design Principles

- Use consistent REST naming conventions.
- Return clear response models for every endpoint.
- Validate all incoming data using Pydantic schemas.
- Keep business logic out of route handlers.
- Separate database access from service logic.
- Use proper HTTP status codes and meaningful error responses.

## Security Considerations

Since this is a hospital-related system, security is important even in a practice project.

- Protect sensitive endpoints with authentication.
- Restrict actions by role, such as admin, doctor, nurse, or receptionist.
- Avoid exposing private patient data unnecessarily.
- Store passwords securely using hashing.
- Use environment variables for secrets and database credentials.

## Development Roadmap

1. Set up the FastAPI project structure.
2. Configure the database and migrations.
3. Build authentication and user roles.
4. Implement patient, doctor, and department APIs.
5. Add appointment and admission workflows.
6. Add medical record, prescription, and billing features.
7. Write tests and improve validation.

## Notes

This repository is still in an early learning stage, so the API surface may expand as the project grows. The current intent is to build a realistic backend that demonstrates how a production-style hospital management service could be organized with FastAPI.
