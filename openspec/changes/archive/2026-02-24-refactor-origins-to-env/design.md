# Design: Refactor Origins to Environment Variables

## Architecture
Moving sensitive and environment-specific configuration to environment variables is a best practice. This change involves extracting hardcoded URLs from `project/settings.py` and making them configurable via environment variables.

### Environment Variable Format
- **Name:** `CORS_ALLOWED_ORIGINS`
- **Format:** Comma-separated list of URLs (e.g., `http://localhost:8000,http://127.0.0.1:8000`).
- **Processing:** In `project/settings.py`, we'll use `os.getenv("CORS_ALLOWED_ORIGINS", "").split(",")`. We'll also filter out empty strings to avoid issues with trailing commas or empty variables.

### Affected Components
- `project/settings.py`: Implementation of `os.getenv` and list processing.
- `.env`, `.env.dev`, `.env.prod`: Storage of environment-specific origins.
- `Dockerfile`: Configuration of build arguments and environment variables for containerized deployments.

### Implementation Details
We'll update `CSRF_TRUSTED_ORIGINS` to point to `CORS_ALLOWED_ORIGINS` as it currently does, but after it's been processed from the environment variable.

Example logic in `settings.py`:
```python
CORS_ALLOWED_ORIGINS = [origin for origin in os.getenv("CORS_ALLOWED_ORIGINS", "").split(",") if origin]
CSRF_TRUSTED_ORIGINS = CORS_ALLOWED_ORIGINS
```
