# Smart Attendance System

A facial recognition-based attendance system built with Flask, OpenCV, and a KNN classifier. Captures student faces via webcam and automatically marks attendance in a MySQL database.

## Features

- Real-time face detection using OpenCV Haar Cascade
- Face recognition via a trained KNN classifier
- Faculty, student, and admin portals
- Attendance tracking per subject with percentage view
- CSV bulk-upload for student data
- Auto-enrollment of new students via webcam photo capture

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Backend | Python, Flask, SQLAlchemy |
| Face Detection | OpenCV (Haar Cascade) |
| Face Recognition | KNN Classifier (scikit-learn) |
| Database | MySQL |
| Frontend | HTML, Jinja2, CSS |

## Project Structure

```
smartattendance/
└── smart_student_attendance_system-master/
    ├── main.py                        # Flask app & all routes
    ├── camera.py                      # Webcam capture helpers
    ├── face_recognition_code/
    │   └── recognition.py             # KNN face recognition logic
    ├── haarcascade_frontalface_default.xml
    ├── trained_knn_model.clf          # Pre-trained KNN model
    ├── config.json                    # App configuration (paths, admin creds)
    ├── images/                        # Enrolled student face images
    ├── templates/                     # Jinja2 HTML templates
    └── attendance.csv                 # Attendance log
```

## Getting Started

### Prerequisites

- Python 3.8+
- MySQL server running locally
- Webcam

### 1. Install dependencies

```bash
pip install flask flask-sqlalchemy flask-mysqldb mysql-connector-python opencv-python scikit-learn numpy requests
```

### 2. Set up MySQL database

Create a database named `test` and run the app once to auto-create tables via SQLAlchemy.

### 3. Configure `config.json`

```json
{
  "params": {
    "admin_name": "your-admin-username",
    "admin_pass": "your-admin-password",
    "upload_location_student": "path/to/student/images",
    "upload_location_faculty": "path/to/faculty/images",
    "upload_location_student_data": "path/to/student/data"
  }
}
```

### 4. Run the app

```bash
cd smart_student_attendance_system-master
python main.py
```

Open `http://127.0.0.1:5000` in your browser.

## How It Works

1. **Admin** adds faculties, subjects, and maps them to classes
2. **Faculty** enrolls students by capturing their photo via webcam
3. **Faculty** starts an attendance session for a subject
4. The system captures live video, detects faces, matches against enrolled images using KNN, and marks attendance
5. Attendance is saved to MySQL and viewable per student/subject

## Final Year Project

Built as a final-year project at Dharamsinh Desai University (2021).
