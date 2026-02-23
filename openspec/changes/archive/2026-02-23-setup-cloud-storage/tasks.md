## 1. Setup & Dependencies
- [x] 1.1 Update `requirements.txt` with `django-storages==1.14.4` and `boto3==1.34.162`.
- [x] 1.2 Verify `pip install -r requirements.txt` succeeds (dry run/mock).

## 2. Implementation
- [x] 2.1 Update `project/storage_backends.py` to use `settings.STATIC_LOCATION`, `settings.PUBLIC_MEDIA_LOCATION`, and `settings.PRIVATE_MEDIA_LOCATION`.
- [x] 2.2 Update `project/settings.py` with enhanced cloud storage configuration (S3/DO, isolation, endpoint, etc.).
- [x] 2.3 Update `utils/media.py` to correctly identify `digitaloceanspaces` in URLs.

## 3. Validation
- [x] 3.1 Verify `STORAGE_AWS=False` still works (local storage).
- [x] 3.2 Verify `STORAGE_AWS=True` logic correctly builds URLs (manual inspection/unit tests).
- [x] 3.3 Verify `get_media_url` returns correct absolute URLs for both AWS and DigitalOcean patterns.
