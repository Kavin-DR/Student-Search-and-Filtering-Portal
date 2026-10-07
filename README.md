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

```

**Backend Files**

**server.js**  
Contains the Express server, API routes, authentication wiring, CORS configuration, static frontend serving, and server startup.

**auth.js**  
Handles JWT generation, token verification, authentication middleware, and role-based access control.

**db.js**  
Handles the SQLite database connection, table creation, student data seeding, and user account initialization.

**package.json**  
Contains the Node.js project configuration, scripts, Node.js engine requirement, and project dependencies.

**students.db**  
SQLite database file created locally when the application is run.


**Frontend Files**

**login.html**  
Provides the login interface for accessing the student portal, including username and password fields with a password visibility toggle.

**login.js**  
Handles the login process, authentication request, token storage, and redirection to the student portal.

**index.html**  
Contains the main student portal interface.

**script.js**  
Handles authentication checks, student search, filtering, sorting, pagination, and administrator CRUD operations.

**style.css**  
Contains the visual styling for the login page and student portal.


**Local Setup**

Clone the repository:

```bash
git clone https://github.com/Kavin-DR/Student-Search-and-Filtering-Portal.git
