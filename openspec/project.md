# Project Context

## Purpose
Elite Guard Services Management System is a comprehensive platform for managing security guard services. It handles employee records, service agreements with client companies, employee scheduling and attendance tracking, loan management, and weekly payroll processing.

## Tech Stack
- **Framework**: Django 4.2.7
- **Database**: PostgreSQL (psycopg3)
- **Deployment/Infrastructure**: 
  - Gunicorn (WSGI Server)
  - Whitenoise (Static File Management)
  - Django Storages + Boto3 (AWS S3 for media/QR codes)
- **Utilities**:
  - Pillow (Image Processing)
  - Openpyxl (Excel Report Generation)
  - Qrcode (Employee ID/QR generation)
  - Selenium & BeautifulSoup4 (Automation/Scraping)
- **Admin UI**: Jazzmin (Customized Django Admin)

## Project Conventions

### Code Style
- Follow PEP 8 for Python code.
- Use Spanish for model `verbose_name`, `help_text`, and string representations (user-facing strings).
- Use English for code (class names, variable names, method names).
- docstrings in English preferred.

### Architecture Patterns
- Standard Django MVT (Model-View-Template) architecture.
- Heavy use of model `properties` and `methods` for business logic (e.g., payroll calculations).
- Decoupled apps: `accounting`, `assistance`, `core`, `employees`, `inventory`, `services`.
- Use of proxy models for different admin views (e.g., `PayrollSummary`).

### Testing Strategy
- Tests are located in `[app]/tests.py` or `[app]/test/` directory.
- Use Django's `TestCase`.

### Git Workflow
- Kebab-case for branch names.
- Conventional commits preferred (feat, fix, refactor, etc.).

## Domain Context
- **Employee**: The core entity representing a security guard. Includes personal details, status history, and loan balances.
- **Agreement (Contrato)**: A contract with a client company specifying service requirements and suggested rates.
- **Service (Servicio)**: The assignment of an Employee to an Agreement at a specific Location with a Schedule.
- **Assistance (Asistencia)**: Daily tracking of whether an employee showed up for their assigned Service.
- **Weekly Assistance (Asistencia Semanal)**: Aggregated attendance for a week (Thursday to Wednesday cycle).
- **Payroll (Nómina)**: Weekly salary calculation based on attendance, extra hours, bonuses, penalties, and loan deductions.

## Important Constraints
- Payroll calculations are performed weekly.
- Attendance cycle is fixed (starts Thursday).
- Multi-currency support is not currently explicit (assumed local currency, likely MXN given field names and Spanish context).

## External Dependencies
- AWS S3 for media storage.
- PostgreSQL database.
