# Capability: Employee Management

## Purpose
The system SHALL maintain and track all information related to security guards, including personal details, status history, and financial loans.

## Requirements

### Requirement: Employee Records
The system SHALL maintain comprehensive records for each employee.

#### Scenario: Registering a new employee
- **WHEN** a new employee is registered with name, CURP, RFC, birthdate, and contact info
- **THEN** a unique 6-character employee code is generated
- **AND** a QR code is generated for the employee
- **AND** an initial status history entry is created

#### Scenario: Status change tracking
- **WHEN** an employee's status is changed (e.g., from Active to Inactive)
- **THEN** the system logs the change in the status history including the date, old status, and new status

### Requirement: Loan Management
The system SHALL track loans and payments for each employee.

#### Scenario: Recording a new loan
- **WHEN** a loan is recorded for an employee
- **THEN** the employee's current balance is updated accordingly
- **AND** the transaction is logged with the amount and details
