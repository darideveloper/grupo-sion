# storage-management Specification

## Purpose
TBD - created by archiving change setup-cloud-storage. Update Purpose after archive.
## Requirements
### Requirement: Cloud Storage Integration
The system SHALL support AWS S3 and DigitalOcean Spaces for static and media file storage, toggled by the `STORAGE_AWS` setting.

#### Scenario: Use AWS S3 when no custom endpoint provided
- **WHEN** `STORAGE_AWS` is `True`
- **AND** `AWS_S3_ENDPOINT_URL` is empty or default AWS URL
- **THEN** system SHALL use standard AWS S3 storage classes

#### Scenario: Use DigitalOcean Spaces when endpoint provided
- **WHEN** `STORAGE_AWS` is `True`
- **AND** `AWS_S3_ENDPOINT_URL` contains `digitaloceanspaces.com`
- **THEN** system SHALL use DigitalOcean Spaces for file storage

### Requirement: Environment Isolation
The system SHALL support isolating files within a single bucket using a project folder prefix.

#### Scenario: Files are uploaded with project folder prefix
- **WHEN** `AWS_PROJECT_FOLDER` is set to `my-project`
- **AND** a file is uploaded to `media`
- **THEN** it SHALL be stored in `bucket/my-project/media/`

### Requirement: Absolute URL Resolution
The system SHALL provide a utility to resolve absolute URLs for media files, regardless of whether storage is local or cloud-based.

#### Scenario: Local media path resolution
- **WHEN** `STORAGE_AWS` is `False`
- **AND** `get_media_url` is called with a local path `/media/img.png`
- **THEN** it SHALL return `HOST + /media/img.png`

#### Scenario: Cloud media path resolution
- **WHEN** `STORAGE_AWS` is `True`
- **AND** `get_media_url` is called with a cloud URL (S3 or DO)
- **THEN** it SHALL return the cloud URL directly

