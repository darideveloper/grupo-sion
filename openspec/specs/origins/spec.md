# origins Specification

## Purpose
TBD - created by archiving change refactor-origins-to-env. Update Purpose after archive.
## Requirements
### Requirement: CORS_ALLOWED_ORIGINS Extraction
The application SHALL extract `CORS_ALLOWED_ORIGINS` from hardcoded values in `project/settings.py` to environment variables.

#### Scenario: Using environment variables for CORS_ALLOWED_ORIGINS
- **Given** I am in the `project/settings.py` file.
- **When** I replace the hardcoded `CORS_ALLOWED_ORIGINS` with `os.getenv("CORS_ALLOWED_ORIGINS", "").split(",")`.
- **Then** the value of `CORS_ALLOWED_ORIGINS` should be a list of strings derived from the environment variable.

### Requirement: CSRF_TRUSTED_ORIGINS Reference
The application SHALL ensure `CSRF_TRUSTED_ORIGINS` is updated correctly to use the new `CORS_ALLOWED_ORIGINS`.

#### Scenario: Updating CSRF_TRUSTED_ORIGINS
- **Given** I am in the `project/settings.py` file.
- **When** `CORS_ALLOWED_ORIGINS` is updated to use an environment variable.
- **Then** `CSRF_TRUSTED_ORIGINS` should still reference `CORS_ALLOWED_ORIGINS`.

### Requirement: Environment and Docker Consistency
The deployment configuration MUST ensure all environment files and Docker configuration are updated with the new environment variable.

#### Scenario: Updating .env and Dockerfile
- **Given** I have `.env`, `.env.dev`, `.env.prod`, and `Dockerfile`.
- **When** I add `CORS_ALLOWED_ORIGINS` as an environment variable in all of them.
- **Then** the application should use these values correctly when started in those environments or containers.

