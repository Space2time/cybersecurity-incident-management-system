# Cybersecurity Incident Management System

# 1. Customer Statement of Requirements

## Project Vision

Our project is a web-based Cybersecurity Incident Management System that gives an organization one place to report and keep track of cybersecurity incidents.

The main purpose of the application is to make it easier for employees to report security problems and for cybersecurity analysts and administrators to keep track of what happens after an incident is reported. Examples of incidents that could be entered into the system include phishing attacks, malware infections, unauthorized access, suspicious login activity, and data breaches.

An employee will be able to submit an incident report with information such as the type of incident, description, date, severity, and affected system. After the report is submitted, authorized cybersecurity analysts and administrators will be able to view the incident, search for specific reports, filter incidents, review the details, and update the status as the incident is investigated and resolved.

The application will also have different user roles so that everyone does not have the same level of access. Regular employees will mainly be responsible for submitting and viewing their own reports, while analysts and administrators will have additional access to manage incidents.

For the first version of the project, we are focusing on getting the main incident reporting and tracking process working. This includes user accounts, different user roles, submitting incidents, storing the information, viewing reports, searching and filtering incidents, updating incident statuses, and validating information entered by users.

The application will use HTML and CSS for the frontend, JavaScript for interactive features and form validation, Python with Flask for the backend, and SQLite for the database. GitHub will be used to manage the project's source code and documentation.

---

# 2. Requirements Specification

## 2.1 Functional Requirements

### FR-01: User Registration

Users should be able to create an account before using the system.

The registration process should collect the information needed to create the account and should make sure the information entered is valid.

### FR-02: User Login

Registered users should be able to log into the application using their username and password.

The system should check the login information before allowing the user to access protected parts of the application.

### FR-03: User Roles

The application will have three main types of users:

- Employee
- Cybersecurity Analyst
- Administrator

Each role will have different permissions based on what the user needs to do.

Employees will mainly submit and view their own reports. Analysts and administrators will have access to additional incident management features.

### FR-04: Submit an Incident

Employees should be able to submit a cybersecurity incident through a web form.

The form will include:

- Incident type
- Description
- Date
- Severity
- Affected system

The application should check that the required information has been entered before saving the report.

### FR-05: Save Incident Information

Once an incident is submitted, the information should be saved in the SQLite database.

Each incident should have its own ID so that it can be easily identified and retrieved later.

### FR-06: View Incidents

Users should be able to view incident reports based on their role.

Employees should be able to see the incidents they submitted.

Cybersecurity analysts and administrators should be able to view the incidents they are authorized to manage.

### FR-07: Search for Incidents

Cybersecurity analysts and administrators should be able to search through incident reports.

The search feature will make it easier to find a specific incident without having to manually look through every report.

### FR-08: Filter Incidents

Users with the appropriate permissions should be able to filter incidents based on information such as:

- Incident type
- Severity
- Status
- Date

This will help users narrow down the incidents they need to review.

### FR-09: View Incident Details

Users should be able to select an incident and see its full details.

The details should include the incident type, description, date, severity, affected system, and current status.

### FR-10: Update Incident Status

Cybersecurity analysts and administrators should be able to update the status of an incident as it moves through the investigation process.

The main statuses will be:

- Open
- Investigating
- Resolved

### FR-11: Validate Information

The application should check information entered into forms before it is saved.

For example, required fields should not be left empty and invalid information should not be accepted.

JavaScript can handle some validation on the frontend, while Flask will also validate information on the backend.

### FR-12: Connect the Application to the Database

The Flask backend will handle communication between the website and the SQLite database.

It will be responsible for receiving information from the frontend, processing requests, saving information, retrieving information, and sending the appropriate results back to the user.

### FR-13: Logout

Users should be able to log out of their account.

After logging out, the user should have to log in again before accessing protected parts of the application.

### FR-14: Control User Access

The application should prevent users from accessing features that are not available to their role.

For example, a regular employee should not be able to access administrator functions or change the status of incidents they are not authorized to manage.

---

## 2.2 Non-Functional Requirements

### NFR-01: Easy to Use

The application should have a simple interface that is easy to understand and navigate.

Users should be able to report and manage incidents through the website without needing to use command-line tools.

### NFR-02: Security

Because this is a cybersecurity application, security needs to be considered throughout the project.

Users should have to authenticate before accessing protected features. The application should also use role-based access so users only have access to the functions they need.

Passwords should not be stored as plain text.

### NFR-03: Performance

The application should respond to normal user actions within a reasonable amount of time.

Searching and retrieving incident information from the database should not take an excessive amount of time for the expected size of the project.

### NFR-04: Reliability

Information that has been successfully submitted should remain stored in the database and should still be available when the application is restarted.

### NFR-05: Maintainability

The frontend, backend, and database portions of the application should be kept organized and separated.

This will make it easier for the team to work on different parts of the project and make changes later.

### NFR-06: Browser Compatibility

The application should work through a modern web browser so users can access the system without needing special software.

### NFR-07: Ability to Expand

The project should be structured so that additional features can be added later.

For example, future versions could include more incident types, additional user roles, or additional incident management features.

### NFR-08: Version Control

GitHub will be used to store the project's source code and documentation.

The team will use GitHub to keep track of changes made during development.

---

# 3. Data and Storage Blueprint

## 3.1 Data Input

The main way information will enter the system is through manual entry on the website.

Employees will use an incident reporting form to enter information about a cybersecurity incident.

The form will collect:

- Incident type
- Description
- Date
- Severity
- Affected system

Users will also enter information when creating an account and logging into the application.

JavaScript will be used for some of the interactive features and frontend validation. Flask will process the information on the backend and make sure the data is valid before it is saved.

For the first version of the project, we are not planning to use an outside dataset or pull incident information from another website. The information will mainly come from users entering incident reports themselves.

---

## 3.2 Database and Storage

We will use SQLite to store the application's information.

SQLite fits this project because it is lightweight, does not require a separate database server, and works well with Python and Flask.

The database will store information about:

- Users
- User roles
- Incident reports
- Incident types
- Severity levels
- Incident dates
- Incident descriptions
- Affected systems
- Incident statuses

The database will allow the application to save information permanently and retrieve it when users need to view or manage incidents.

---

## 3.3 Proposed Database Structure

### Users Table

| Field | Description |
|---|---|
| user_id | Unique ID for each user |
| username | Username used to log in |
| password | Protected user password |
| role | Employee, Cybersecurity Analyst, or Administrator |

### Incidents Table

| Field | Description |
|---|---|
| incident_id | Unique ID for each incident |
| user_id | ID of the user who submitted the incident |
| incident_type | Type of cybersecurity incident |
| description | Explanation of what happened |
| incident_date | Date of the incident |
| severity | Severity level of the incident |
| affected_system | System affected by the incident |
| status | Current status of the incident |

The `user_id` in the Incidents table will connect each incident to the user who submitted it. This will allow the application to identify who reported an incident and determine which reports an employee should be able to view.
