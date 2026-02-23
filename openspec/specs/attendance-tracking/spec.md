# Capability: Attendance Tracking

## Purpose
The system SHALL track and aggregate daily and weekly attendance for employees assigned to service locations, including extra hours and associated payments.

## Requirements

### Requirement: Daily Attendance
The system SHALL track daily attendance for each employee assigned to a service.

#### Scenario: Marking attendance
- **WHEN** an administrator marks an employee as present for a specific date
- **THEN** the daily assistance record is updated
- **AND** the corresponding weekly assistance record is automatically updated for that day

#### Scenario: Recording extra hours
- **WHEN** extra paid or unpaid hours are recorded for a daily attendance
- **THEN** the weekly totals for extra hours are updated

### Requirement: Weekly Aggregation
The system SHALL aggregate attendance data on a weekly basis.

#### Scenario: Weekly cycle calculation
- **WHEN** a weekly assistance record is created
- **THEN** the system automatically calculates the week number, start date, and end date
- **AND** it summarizes worked days and absences based on daily records

### Requirement: Extra Payments
The system SHALL allow recording additional payments or deductions linked to attendance.

#### Scenario: Adding a bonus to a shift
- **WHEN** an extra payment of type "Bono" is added to a daily attendance
- **THEN** it is included in the payroll calculations for that week
