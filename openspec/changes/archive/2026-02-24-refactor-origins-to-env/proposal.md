# Refactor Origins to Environment Variables

## Why
Currently, `CORS_ALLOWED_ORIGINS` and `CSRF_TRUSTED_ORIGINS` are hardcoded in `project/settings.py`. This makes the application less flexible for different deployment environments and exposes internal URLs in the codebase.

## What Changes
Move these settings to environment variables.
- Update `project/settings.py` to use `CORS_ALLOWED_ORIGINS` from the environment.
- Use a comma-separated string in environment variables.
- Update all `.env` files (`.env`, `.env.dev`, `.env.prod`) with the current values.
- Update `Dockerfile` to include these as `ARG` and `ENV`.

## User-Visible Progress
1.  Ability to configure CORS and CSRF origins via environment variables.
2.  Consistent configuration across different environments.
