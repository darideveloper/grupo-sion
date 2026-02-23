# Capability: Payroll Processing

## Purpose
The system SHALL automate the weekly payroll calculation for employees, incorporating attendance data, bonuses, penalties, and loan repayment deductions.

## Requirements

### Requirement: Weekly Payroll Calculation
The system SHALL calculate the weekly payroll for each employee based on their attendance and service agreement.

#### Scenario: Calculating weekly payroll subtotal
- **WHEN** a payroll record is generated for an employee for a specific week
- **THEN** it calculates the subtotal by adding:
    - Weekly rate
    - Bonuses and other extra payments
    - Extra unpaid hours amount
- **AND** subtracting:
    - No attendance penalty
    - Other penalties

#### Scenario: Deducting loan payments from payroll
- **WHEN** an employee has a loan balance and a payroll is generated
- **THEN** the system applies a discount for loan repayment
- **AND** the final amount is updated to reflect this deduction

### Requirement: Payroll Reporting
The system SHALL generate reports for payroll management.

#### Scenario: Generating payroll data list
- **WHEN** an administrator requests the data list for a payroll record
- **THEN** the system provides a comprehensive list of values including service, employee name, rates, attendance markers, and totals
