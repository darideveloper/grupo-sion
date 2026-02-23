## Context
The current implementation has basic AWS S3 support but lacks flexibility for DigitalOcean Spaces (S3-compatible API) and subfolder isolation.

## Goals
- Support S3-compatible APIs (DigitalOcean Spaces).
- Allow multiple projects/environments to share a bucket via `AWS_PROJECT_FOLDER`.
- Ensure consistent URL generation across local and cloud storage.

## Decisions
- **Decision**: Use `AWS_S3_ENDPOINT_URL` in settings.
  - **Rationale**: DigitalOcean Spaces requires a specific endpoint URL (e.g., `https://region.digitaloceanspaces.com`).
- **Decision**: Use `AWS_PROJECT_FOLDER` to prefix all storage locations.
  - **Rationale**: Simplifies bucket management and enables multi-tenant usage of a single bucket.
- **Decision**: Update `utils/media.py` to check for `digitaloceanspaces` in URLs.
  - **Rationale**: Current check only looks for `s3.amazonaws.com`, which would break absolute URL resolution for DO.

## Risks / Trade-offs
- **Risk**: Incorrect environment variable configuration could break static/media delivery.
  - **Mitigation**: Fallback to local storage if `STORAGE_AWS` is False. Provide clear documentation for `.env` variables.

## Migration Plan
1. Update dependencies.
2. Refactor storage backend classes.
3. Update settings logic.
4. Update utility helper.
5. Verify with local vs mock-cloud settings.
