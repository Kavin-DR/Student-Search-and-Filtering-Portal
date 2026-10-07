Registrar — Student Search & Filtering Portal
==============================================

A full-stack web application for searching, filtering, sorting, and managing
college student records, with authentication and role-based access control.

Live Application
----------------

https://student-portal-api-t3qy.onrender.com

The application is deployed on Render and serves both the frontend and backend
from the same web service.

Project Overview
----------------

The Registrar — Student Search & Filtering Portal is a college-level
student record management system designed to provide a secure and organized
way to search, filter, view, and manage student information.

The application includes:

- Secure login
- Role-based access control
- Student search
- Multiple filtering options
- Sorting
- Pagination
- Student record creation
- Student record editing
- Student record deletion
- SQLite database storage
- JWT-based authentication
- Password hashing
- Cloud deployment using Render

Tech Stack
----------

- Backend: Node.js + Express
- Database: SQLite using Node.js built-in `node:sqlite` module
- Authentication: JWT using `jsonwebtoken`
- Password Hashing: `bcryptjs`
- Frontend: Vanilla HTML, CSS, and JavaScript
- Version Control: Git + GitHub
- Deployment: Render

Node.js Requirement
-------------------

The project requires Node.js 22.5 or later because it uses the built-in
`node:sqlite` module.

Node.js 24+ is recommended.

Features
--------

Authentication
~~~~~~~~~~~~~~

- Login page for registered users
- Username and password authentication
- Password hashing using bcrypt
- JWT-based authentication
- Protected student-management API routes
- Session verification
- Automatic redirection when authentication is missing or invalid
- Password visibility toggle on the login page

User Access
~~~~~~~~~~~

The portal can only be accessed using the two registered username/password
combinations configured in the application.

There are two user roles:

- Admin
  - Search students
  - Filter students
  - Sort students
  - View student records
  - Add student records
  - Edit student records
  - Delete student records

- Student
  - Search students
  - Filter students
  - Sort students
  - View student records
  - No create, edit, or delete permissions

No other username/password combination can successfully open the portal.

The Student Email ID stored in a student record is student information only.
It is not used as a login credential.

The actual usernames and passwords are intentionally not included in this
README.

Student Search and Filtering
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The portal supports:

- Student name search
- Register number search
- Department filtering
- Degree/course filtering
- Year of study filtering
- Semester filtering
- Section filtering
- Gender filtering
- Residential status filtering
- Admission category filtering
- Student status filtering
- Sorting
- Pagination

Student Information
-------------------

Each student record contains the following 20 fields:

1. Register Number
2. First Name
3. Last Name
4. Gender
5. Date of Birth
6. Degree / Course
7. Department / Major
8. Year of Study
9. Semester
10. Section
11. Attendance Percentage
12. Residential Status
13. Student Email ID
14. Student Phone Number
15. Parent / Guardian Name
16. Parent Contact Number
17. Permanent Address
18. Blood Group
19. Admission Category / Quota
20. Status

Project Structure
-----------------

```text
student-portal/
│
├── backend/
│   ├── server.js
│   ├── auth.js
│   ├── db.js
│   ├── package.json
│   └── students.db
│
├── frontend/
│   ├── login.html
│   ├── login.js
│   ├── index.html
│   ├── script.js
│   └── style.css
│
└── README.md

Backend Files
-------------

server.js

Contains the Express server, API routes, authentication wiring, CORS
configuration, static frontend serving, and server startup.

auth.js

Handles JWT generation, token verification, authentication middleware, and
role-based access control.

db.js

Handles the SQLite database connection, table creation, student data seeding,
and user account initialization.

package.json

Contains the Node.js project configuration, scripts, Node.js engine
requirement, and project dependencies.

students.db

SQLite database file created locally when the application is run.

Frontend Files
--------------

login.html

Provides the login interface for accessing the student portal. It includes
the username and password fields along with a password visibility toggle.

login.js

Handles the login process, authentication request, token storage, and
redirection to the student portal.

index.html

Contains the main student portal interface.

script.js

Handles authentication checks, student search, filtering, sorting, pagination,
and admin CRUD operations.

style.css

Contains the visual styling for the login page and student portal.

Local Setup
-----------

Clone the repository:

git clone https://github.com/RathiVarshiniR/Student-Search-and-Filtering-Portal.git

Move into the project directory:

cd Student-Search-and-Filtering-Portal

Move into the backend directory:

cd backend

Install the required dependencies:

npm install

Start the application:

npm start

The local application runs at:

http://localhost:4000

Open the URL in a browser and sign in using one of the two registered
accounts.

Environment Variables
---------------------

The application supports the following environment variables.

PORT

The server uses the PORT environment variable when provided by the hosting
platform.

For local development, the default port is:

4000

DB_PATH

The SQLite database path can be configured using the DB_PATH environment
variable.

If DB_PATH is not provided, the application uses:

backend/students.db

JWT_SECRET

A custom JWT secret can be provided using:

JWT_SECRET=your-long-random-secret

For Windows PowerShell:

$env:JWT_SECRET="your-long-random-secret"
npm start

For macOS/Linux:

JWT_SECRET=your-long-random-secret npm start

For deployment, secrets should be stored as environment variables rather than
being committed to source control.

Authentication Flow
-------------------

The login process follows this flow:

User
  |
  v
Login Page
  |
  v
POST /api/auth/login
  |
  v
Credentials Verified
  |
  v
JWT Generated
  |
  v
Token Stored in Session
  |
  v
Protected Student Portal

The frontend verifies the user's session before loading student records.

If the session is missing or invalid, the user is redirected to the login
page.

Role-Based Access Control
-------------------------

Admin Access

The admin account has permission to:

- Search students
- Filter students
- Sort students
- View student records
- Add new students
- Edit existing students
- Delete student records

Student Access

The student account has permission to:

- Search students
- Filter students
- Sort students
- View student records

The student account cannot create, edit, or delete student records.

API Endpoints
-------------

| Method | Endpoint | Authentication | Description |
|--------|----------|----------------|-------------|
| POST | /api/auth/login | No | Authenticate user and return JWT |
| GET | /api/auth/me | Yes | Verify current session |
| GET | /api/students | Yes | Search, filter, sort, and paginate students |
| GET | /api/students/filters | Yes | Return available filter values |
| GET | /api/students/:id | Yes | Retrieve one student |
| POST | /api/students | Admin | Create a student |
| PUT | /api/students/:id | Admin | Update a student |
| DELETE | /api/students/:id | Admin | Delete a student |

Student Search Query Parameters
-------------------------------

The GET /api/students endpoint supports query parameters for searching,
filtering, sorting, and pagination.

Supported parameters include:

q
class
section
grade
gender
status
sortBy
sortDir
page
pageSize

Example:

/api/students?q=Arjun&page=1&pageSize=10

Database
--------

The application uses SQLite through Node.js's built-in node:sqlite module.

No external SQLite database driver is required.

The database automatically creates two main tables.

Users Table

Stores:

- User ID
- Username
- Password hash
- Role
- Display name

Students Table

Stores the complete 20-field student information listed in the
Student Information section.

When an empty database is initialized, the application automatically
generates sample college student records.

Deployment
----------

The application is deployed using Render.

The same Render web service serves:

- Express backend
- Static frontend

No separate frontend hosting service is required.

Render Configuration
~~~~~~~~~~~~~~~~~~~~

Runtime:

Node

Branch:

main

Build Command:

cd backend && npm install

Start Command:

cd backend && node server.js

Live Application
~~~~~~~~~~~~~~~~

https://student-portal-api-t3qy.onrender.com

GitHub Repository
-----------------

The project source code is hosted on GitHub:

https://github.com/RathiVarshiniR/Student-Search-and-Filtering-Portal

Git Workflow
------------

After making changes locally, save the files and run:

git add .
git commit -m "Describe your changes"
git push

The GitHub repository is connected to Render.

When changes are pushed to the main branch, Render automatically detects the
new commit and starts a new deployment.

Deployment Flow
---------------

Local Project
     |
     v
Git Add
     |
     v
Git Commit
     |
     v
Git Push
     |
     v
GitHub
     |
     v
Render
     |
     v
Automatic Deployment
     |
     v
Live Application

SQLite Deployment Note
----------------------

The application currently uses SQLite as a file-based database.

On Render's Free plan, the filesystem is ephemeral. This means data stored in
the local SQLite database can be lost when the service is restarted,
redeployed, or otherwise reset.

Therefore, the current deployment is primarily suitable for:

- College projects
- Academic demonstrations
- Prototypes
- Presentations
- Development and testing

For a production application requiring permanent data storage, a persistent
database such as PostgreSQL should be used.

Security Notes
--------------

This project is designed as a college-level full-stack application and is
not intended to be a hardened production system.

For production use, consider:

- Using strong, unique passwords
- Keeping passwords out of source control
- Storing JWT_SECRET securely as an environment variable
- Using HTTPS
- Adding rate limiting to the login endpoint
- Adding token expiration and refresh-token handling
- Validating and sanitizing user input
- Using a persistent production database
- Implementing stronger account-management functionality

Authentication tokens are stored in sessionStorage. This means the session
is cleared when the browser tab or session is closed.

Resetting the Local Database
----------------------------

To reset the local database during development:

1. Stop the server.
2. Delete:

backend/students.db

3. Start the server again:

cd backend
npm start

The database tables and sample student records will be recreated.

Do not delete the deployed database simply to update login credentials.

Project Purpose
---------------

The Registrar — Student Search & Filtering Portal demonstrates how a
full-stack web application can combine:

- Authentication
- Role-based authorization
- SQLite database management
- REST APIs
- Search and filtering
- Sorting and pagination
- CRUD operations
- Frontend development
- Git/GitHub version control
- Cloud deployment

The project provides an access-controlled environment for managing college
student records through a simple and organized web interface.

The system has two registered user roles:

- Administrator — full student record management access
- Student — read-only student record access

The project demonstrates the integration of frontend, backend, database,
authentication, authorization, and cloud deployment technologies in a single
college-level application.
