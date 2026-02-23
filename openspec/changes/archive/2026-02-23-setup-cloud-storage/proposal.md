# Change: Setup Cloud Storage (AWS & DigitalOcean)

## Why
The project needs a robust and flexible way to handle media and static files in production environments. Supporting both AWS S3 and DigitalOcean Spaces allows for provider flexibility and cost optimization, while subfolder isolation enables sharing a single bucket across multiple environments (staging, production).

## What Changes
- Update `requirements.txt` to recommended versions of `django-storages` and `boto3`.
- Update `project/storage_backends.py` to support dynamic locations from settings.
- Enhance `project/settings.py` to support DigitalOcean Spaces endpoints, custom domains, and project folder isolation.
- Update `utils/media.py` to correctly identify DigitalOcean Spaces URLs.

## Impact
- Affected specs: `storage-management` (New)
- Affected code:
  - `requirements.txt`
  - `project/settings.py`
  - `project/storage_backends.py`
  - `utils/media.py`
