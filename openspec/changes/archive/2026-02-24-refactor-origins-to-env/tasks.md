# Tasks: Refactor Origins to Environment Variables

## 1. Setup

- [x]  Extract `CORS_ALLOWED_ORIGINS` from `project/settings.py` to environment variables in `.env`.
- [x]  Update `project/settings.py` to use `os.getenv("CORS_ALLOWED_ORIGINS")`.
- [x]  Update `.env.dev` and `.env.prod` with `CORS_ALLOWED_ORIGINS`.
- [x]  Update `Dockerfile` to include `ARG` and `ENV` for `CORS_ALLOWED_ORIGINS`.

## 2. Validation

- [x]  Verify that `project/settings.py` correctly parses the environment variable.
- [x]  Check that `CORS_ALLOWED_ORIGINS` is not empty when defined in `.env`.
- [x]  Verify that `CSRF_TRUSTED_ORIGINS` is correctly assigned to `CORS_ALLOWED_ORIGINS`.
- [x]  Check that the Dockerfile builds correctly with the new environment variable.
