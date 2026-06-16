# Cement Plant Document Control System

A Flask Aconex-like MVP for document control in cement plant construction projects.

## Features
- Login and user roles: admin, document controller, reviewer, viewer
- Document Register
- Revision/status/workflow tracking
- Transmittal Log
- Printable Transmittal PDF
- MAR Log
- RFI Log
- NCR Log
- Excel Export
- Dashboard Charts
- File uploads

## Local Run
```bash
pip install -r requirements.txt
python app.py
```

Open: http://127.0.0.1:5000

## Default Users
- admin / admin123
- dc / dc123
- reviewer / review123

## Render
- Build command: `pip install -r requirements.txt`
- Start command: `gunicorn app:app`
