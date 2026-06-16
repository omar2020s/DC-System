# Cement Plant Document Control System - Persistent Version

Flask web application similar to a simple Aconex-style Document Control system for a cement plant construction project.

## Features

- Login system
- User roles: `admin`, `dc`, `reviewer`, `viewer`
- Document Register with upload files
- Revision and status control
- Workflow approval actions
- Transmittal Log
- Print Transmittal PDF
- MAR Log
- RFI Log
- NCR Log
- Excel export
- Dashboard counters and charts
- PostgreSQL database support for permanent records on Render
- Permanent uploaded files using Render Disk

## Default Users

| Username | Password | Role |
|---|---|---|
| admin | admin123 | admin |
| dc | dc123 | document controller |
| reviewer | review123 | reviewer |

If the users already exist and passwords do not work, set this environment variable once:

```text
RESET_DEFAULT_USERS=true
```

Deploy once, log in, then remove it or change it back to:

```text
RESET_DEFAULT_USERS=false
```

## Local Run

```bash
pip install -r requirements.txt
python app.py
```

Open:

```text
http://127.0.0.1:5000
```

## Render Deployment - Permanent Database + Permanent Files

### 1. Upload project to GitHub

Upload all project files to your GitHub repository.

### 2. Create PostgreSQL database on Render

In Render:

```text
New +  >  PostgreSQL
```

After creation, copy the **Internal Database URL**.

### 3. Create Web Service

In Render:

```text
New +  >  Web Service  >  Connect GitHub Repo
```

Use:

```text
Build Command: pip install -r requirements.txt
Start Command: gunicorn app:app
```

### 4. Add Environment Variables

In the Web Service settings add:

```text
SECRET_KEY=write-any-long-random-secret
DATABASE_URL=your-render-postgresql-internal-database-url
UPLOAD_FOLDER=/var/data/uploads
RESET_DEFAULT_USERS=false
```

### 5. Add Render Disk for permanent uploaded files

In the same Web Service, add a Disk:

```text
Name: uploads
Mount Path: /var/data
Size: 1GB or more
```

Uploaded files will be saved here:

```text
/var/data/uploads
```

## Important

- PostgreSQL keeps database records permanently.
- Render Disk keeps uploaded PDF, DWG, DOCX, Excel files permanently.
- Without Render Disk, uploaded files may disappear after redeploy or restart.
- Without PostgreSQL, SQLite may be lost unless stored on `/var/data` with a Render Disk.

## Check storage after deployment

Login as admin, then open:

```text
/storage-status
```

It will show the database type and upload folder path.
