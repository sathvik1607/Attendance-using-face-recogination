# Face Attendance System

Production-ready setup guide for running the project locally using Python 3.11.

---

# Tech Stack

## Backend

* FastAPI
* SQLAlchemy
* PostgreSQL
* DeepFace
* TensorFlow CPU
* JWT Authentication
* WebSockets

## Frontend

* React + Vite

---

# Recommended Environment

| Component  | Version |
| ---------- | ------- |
| Python     | 3.11.9  |
| PostgreSQL | 16      |
| Node.js    | 20+     |
| npm        | latest  |

---

# Important Notes Before Setup

This project uses:

* TensorFlow
* DeepFace
* OpenCV

These libraries are sensitive to Python version compatibility.

Use ONLY:

```text
Python 3.11.x
```

Do NOT use:

* Python 3.14
* Python 3.13

unless the ML ecosystem officially stabilizes there.

---

# Repository Structure

```text
project-root/
│
├── backend/
│   ├── main.py
│   ├── requirements.txt
│   ├── routes/
│   ├── uploads/
│   ├── database.py
│   └── ...
│
├── frontend/
│   ├── src/
│   ├── package.json
│   └── ...
│
└── README.md
```

---

# STEP 1 — Install Python 3.11

## Windows

Download Python 3.11 from:

[https://www.python.org/downloads/release/python-3119/](https://www.python.org/downloads/release/python-3119/)

IMPORTANT:
During installation:

✔ Check:

```text
Add Python to PATH
```

After installation verify:

```cmd
py -3.11 --version
```

Expected:

```text
Python 3.11.9
```

---

## macOS

Install using Homebrew:

```bash
brew install python@3.11
```

Verify:

```bash
python3.11 --version
```

---

# STEP 2 — Install PostgreSQL

## Windows

Download PostgreSQL 16:

[https://www.postgresql.org/download/windows/](https://www.postgresql.org/download/windows/)

During installation:

Remember:

* username
* password
* port

Recommended:

```text
Port: 5433
```

Install pgAdmin when prompted.

---

## macOS

```bash
brew install postgresql@16
brew services start postgresql@16
```

---

# STEP 3 — Clone Repository

```bash
git clone <YOUR_REPO_URL>
```

```bash
cd <REPO_FOLDER>
```

---

# STEP 4 — Setup Backend

Move into backend folder:

## Windows

```cmd
cd backend
```

## macOS

```bash
cd backend
```

---

# STEP 5 — Create Python Virtual Environment

## Windows

```cmd
py -3.11 -m venv myenv
```

Activate:

```cmd
myenv\Scripts\activate
```

---

## macOS

```bash
python3.11 -m venv myenv
```

Activate:

```bash
source myenv/bin/activate
```

---

# STEP 6 — Install Backend Dependencies

Install locked dependencies:

## Windows

```cmd
pip install -r requirements.txt
```

## macOS

```bash
pip install -r requirements.txt
```

This may take several minutes because TensorFlow and DeepFace are large packages.

---

# STEP 7 — Configure Environment Variables

Inside backend folder create:

```text
.env
```

Add:

```env
DATABASE_URL=postgresql://postgres:YOUR_PASSWORD@localhost:5433/face_auth
CONFIDENCE_THRESHOLD=0.40
MATCH_THRESHOLD=0.55
LIVENESS_CHECK=False
ADMIN_EMAIL=admin@gmail.com
ADMIN_PASSWORD=admin123
```

Replace:

```text
YOUR_PASSWORD
```

with your PostgreSQL password.

---

# STEP 8 — Create PostgreSQL Database

Open pgAdmin or psql.

Create database:

```sql
CREATE DATABASE face_auth;
```

---

# STEP 9 — Run Backend

## Windows

```cmd
uvicorn main:app --reload
```

## macOS

```bash
uvicorn main:app --reload
```

Expected:

```text
Application startup complete
```

API docs:

```text
http://127.0.0.1:8000/docs
```

---

# STEP 10 — Setup Frontend

Open new terminal.

Move into frontend folder:

## Windows

```cmd
cd frontend
```

## macOS

```bash
cd frontend
```

---

# STEP 11 — Install Frontend Dependencies

```bash
npm install
```

---

# STEP 12 — Run Frontend

```bash
npm run dev
```

Expected:

```text
http://localhost:5173
```

---

# Running the Project

Currently the project requires:

## Backend

YES — required.

## Frontend

YES — required for full UI experience.

The backend alone is enough only for:

* API testing
* Swagger docs
* backend development
* database testing

The frontend is required for:

* actual user interaction
* attendance UI
* event management UI
* image uploads from browser

---

# Useful Commands

## Check Python Version

```bash
python --version
```

---

## Check Installed Packages

```bash
pip list
```

---

## Freeze Current Environment

```bash
pip freeze > requirements.txt
```

---

## PostgreSQL Commands

Open psql:

```bash
psql -U postgres -p 5433
```

Switch DB:

```sql
\c face_auth
```

List tables:

```sql
\dt
```

Show users:

```sql
SELECT * FROM users;
```

---

# Common Issues

## TensorFlow Warnings

Example:

```text
oneDNN custom operations are on
```

This is NOT an error.

TensorFlow prints informational startup logs.

---

## PostgreSQL Connection Error

Check:

* PostgreSQL service running
* correct password
* correct port
* database exists

---

## Port Already In Use

Change backend port:

```bash
uvicorn main:app --reload --port 8001
```

---

## Missing Dependencies

Always activate virtual environment before running project.

---

# Recommended Production Architecture (Future)

Current setup is good for development.

Future production architecture should separate:

```text
Frontend → CDN / Vercel
Backend → FastAPI + Gunicorn
Database → PostgreSQL
Reverse Proxy → nginx
```

---

# Team Notes

* Use Python 3.11 only.
* Always activate virtual environment before development.
* Do not manually modify TensorFlow dependencies unless necessary.
* Keep requirements.txt locked for reproducibility.

---

# Current Status

The backend architecture currently includes:

* FastAPI backend
* PostgreSQL database
* DeepFace integration
* TensorFlow inference
* WebSocket support
* JWT authentication
* React frontend integration
* Automatic admin bootstrap
* Uploads handling
* Attendance/event management

---

# API Docs

Swagger UI:

```text
http://127.0.0.1:8000/docs
```

---

# End
