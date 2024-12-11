# CHAT_APP
# Installation Guide

## Prerequisites
Before you begin, ensure you have the following installed on your system:
- Python 3.8 or higher
- Docker (for Redis)
- Git
- pip (Python package installer)

## Installation Steps

### 1. Project Setup
First, clone the repository and set up your local environment:

```sh
# Clone the repository
git clone <repository-url>
cd <project-directory>

# Create and activate a virtual environment
python3 -m venv venv

# On Unix/macOS:
source venv/bin/activate

# On Windows:
.\venv\Scripts\activate
```

### 2. Dependencies Installation
Install all required packages:

```sh
# Make sure you're in your virtual environment - (venv) should be visible in your terminal
pip install -r requirements.txt

# Verify installation
pip list  # Should show all installed packages
```

### 3. Database Configuration
Set up the database and create necessary tables:

```sh
# Apply database migrations
python manage.py migrate

# Verify migrations
python manage.py showmigrations  # All migrations should be checked
```

### 4. Redis Setup
The application requires Redis for real-time chat functionality:

```sh
# Start Redis using Docker
docker run -p 6379:6379 -d redis:5

# Verify Redis is running
docker ps  # Should show running Redis container
```

### 5. User Authentication Setup
Create an administrative user for testing:

```sh
# Create a superuser
python manage.py createsuperuser

# Follow the prompts to set:
# - Username
# - Email (optional)
# - Password (must be secure)
```

### 6. Running the Application
Start the development server:

```sh
python manage.py runserver

# The server will start at http://localhost:8000
```

### 7. Accessing the Application
1. Open your web browser and go to http://localhost:8000/admin/
2. Log in with your superuser credentials
3. Navigate to http://localhost:8000/chat/ to access the chat interface
