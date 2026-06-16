# Cement DC System - Render Ready

A Flask Document Control system for a cement plant construction project.

## Features
- Document Register
- Transmittals + PDF print
- MAR Log
- RFI Log
- NCR Log
- Workflow approval actions
- Excel export
- Dashboard counters/charts
- User roles
- Permanent PostgreSQL data storage
- Permanent file storage inside PostgreSQL database, so Render Free does not need Persistent Disk

## Render Settings

Build Command:
```bash
pip install -r requirements.txt
```

Start Command:
```bash
gunicorn app:app
```

Environment Variables:
```text
DATABASE_URL=<Internal Database URL from Render PostgreSQL>
SECRET_KEY=change_this_to_any_long_secret
RESET_DEFAULT_USERS=true
```

After first successful login, set:
```text
RESET_DEFAULT_USERS=false
```

Default users:
```text
admin / admin123
dc / dc123
reviewer / review123
```

## Important
Do not set `UPLOAD_FOLDER=/var/data/uploads` on Render Free. Files are saved inside PostgreSQL by this version.
