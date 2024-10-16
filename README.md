# Task Management API

A simple and efficient API for managing tasks, built with Django and Django REST Framework. This API allows users to create, update, delete, and track tasks with features like priority levels and completion status.

## Table of Contents

- [Features](#features)
- [Technologies Used](#technologies-used)
- [API Endpoints](#api-endpoints)
- [Models](#models)
- [Installation](#installation)
- [Usage](#usage)

## Features

- User authentication and registration
- Create, read, update, and delete tasks
- Set task priority levels (Low, Medium, High)
- Mark tasks as completed or pending
- Filter tasks by status and priority
- Comprehensive error handling

## Technologies Used

- **Backend**: Django, Django REST Framework
- **Database**: SQLite (for development)
- **Authentication**: JWT (JSON Web Tokens) with `djangorestframework-simplejwt`
- **Testing**: Postman

## API Endpoints

| Endpoint                            | Method | Description                           |
|-------------------------------------|--------|---------------------------------------|
| `/api/users/`                      | POST   | Register a new user                   |
| `/api/users/{id}/`                 | GET    | Retrieve user details                 |
| `/api/users/{id}/`                 | PUT    | Update user details                   |
| `/api/users/{id}/`                 | DELETE | Delete a user                        |
| `/api/tasks/`                      | GET    | Retrieve all tasks for authenticated user |
| `/api/tasks/`                      | POST   | Create a new task                     |
| `/api/tasks/{id}/`                 | GET    | Retrieve a specific task              |
| `/api/tasks/{id}/`                 | PUT    | Update a specific task                |
| `/api/tasks/{id}/`                 | DELETE | Delete a specific task                |
| `/api/tasks/{id}/mark_complete/`   | POST   | Mark a task as completed              |
| `/api/tasks/{id}/mark_incomplete/` | POST   | Mark a task as pending                |
| `/api/token/`                      | POST   | Obtain JWT token for authentication   |
| `/api/token/refresh/`              | POST   | Refresh JWT token                     |

## Models

### User
- **username**: CharField (max_length=150)
- **email**: EmailField
- **password**: CharField (max_length=128)

### Task
- **owner**: ForeignKey (User)
- **title**: CharField (max_length=255)
- **description**: TextField (blank=True)
- **due_date**: DateTimeField
- **priority**: CharField (choices: Low, Medium, High)
- **status**: CharField (choices: Pending, Completed)
- **completed_at**: DateTimeField (null=True, blank=True)
- **created_at**: DateTimeField (auto_now_add=True)
- **updated_at**: DateTimeField (auto_now=True)

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/Asrat-Yehombawork/task_manager.git
   cd task_manager

2. Install the dependencies:
   ```bash
  pip install -r requirements.txt 

3. Apply migrations:
   ```bash
  python manage.py migrate

4. Run the server:
   ```bash
  python manage.py runserver

## Usage
Authenticate users using the /api/token/ endpoint to obtain a JWT token.
Use the token to access the task-related endpoints.
Create, retrieve, update, and delete tasks as needed.
