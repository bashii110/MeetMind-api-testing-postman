# MeetMind AI — API Testing Project

Manual API testing project for the **MeetMind AI REST API** using **Postman**.

## Environment

* **Base URL:** `http://192.168.0.104:8000/api/v1`
* **Tool:** Postman
* **Testing Type:** Manual API Testing
* **Environment:** Local Development
* **API Architecture:** REST API
* **Authentication:** Laravel Sanctum Bearer Token
* **Backend:** Laravel 12
* **Database:** MySQL

## Testing Coverage

The API testing covers key application areas, including:

* Authentication & authorization
* User registration and login
* Email verification
* Password reset
* Workspace management
* Workspace members and roles
* Departments
* Meetings
* Tasks
* Notifications
* Analytics
* Admin endpoints
* Validation and negative test scenarios
* Authentication and authorization checks
* HTTP status code and response validation

## Project Structure

```text
MeetMind-AI-API-Testing/
│
├── 01-Test-Plan/
│   └── API-Test-Plan.md
│
├── 02-Test-Cases/
│   └── API-Test-Cases.md
│
├── 03-Test-Execution/
│   └── Test-Execution-Report.md
│
├── 04-Bug-Reports/
│   └── Bug-Report-Template.md
│
└── 05-Evidence/
    └── README.md
```

## Testing Approach

The APIs are tested manually in Postman using:

* Positive test scenarios
* Negative test scenarios
* Boundary and validation testing
* Authentication testing
* Authorization testing
* Invalid and missing parameters
* Invalid Bearer tokens
* HTTP status code verification
* Response body validation
* Error message validation
* CRUD operation testing

## Test Documentation

| Document                  | Description                                                        |
| ------------------------- | ------------------------------------------------------------------ |
| **Test Plan**             | Defines API testing scope, objectives, approach, and test strategy |
| **Test Cases**            | Contains detailed API test scenarios and expected results          |
| **Test Execution Report** | Records executed tests, actual results, and pass/fail status       |
| **Bug Reports**           | Template for documenting identified API defects                    |
| **Evidence**              | Contains references/screenshots related to test execution          |

## Tools & Technologies

* **Postman** — API testing
* **Laravel 12** — Backend framework
* **Laravel Sanctum** — API authentication
* **MySQL** — Database
* **Git & GitHub** — Version control and project documentation

## Project Objective

The objective of this project is to demonstrate practical **Manual API Testing** skills by designing test cases, executing REST API requests, validating responses, testing authentication and authorization, identifying defects, and documenting test results using Postman.

## Author

**Bashir Ahmed**

Software Engineering Graduate | Junior Software Engineer | Flutter Developer | QA/SQA Enthusiast

GitHub: `https://github.com/bashii110`
