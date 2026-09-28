# API Test Plan

## 1. Objective

Verify the major functional areas of the MeetMind AI REST API, including authentication, authorization, workspaces, meetings, tasks, validation, and negative scenarios.

## 2. Scope

### In Scope
- HTTP methods and endpoints
- Authentication and authorization
- Request validation
- HTTP status codes
- JSON response structure
- Major CRUD functionality
- Invalid-resource handling
- Evidence capture

### Out of Scope
- Load/stress testing
- Penetration testing
- Automated API testing
- Full coverage of every application route
- Third-party provider testing

## 3. Environment

| Item | Value |
|---|---|
| Application | MeetMind AI |
| API | Laravel REST API |
| Base URL | `http://192.168.0.104:8000/api/v1` |
| Client | Postman |
| Authentication | Bearer Token |
| Tester | Bashir Ahmed |

## 4. Test Approach

1. Start the Laravel backend.
2. Verify API availability.
3. Login with a test account.
4. Save the access token in Postman.
5. Execute protected endpoints.
6. Verify status codes and JSON responses.
7. Execute negative tests.
8. Capture evidence for important cases.
9. Record PASS/FAIL results.
10. Document confirmed defects.

## 5. Entry Criteria

- Backend is running.
- API is reachable.
- Test account exists.
- Database is available.
- Required test data can be created.

## 6. Exit Criteria

- Selected test cases are executed.
- Actual results are recorded.
- Important evidence is captured.
- Confirmed defects are documented.
- Execution report is completed.

## 7. Evidence Strategy

Evidence is not mandatory for every request.

Prioritize screenshots for:
- Successful login
- Authenticated request
- Workspace creation
- Meeting creation/retrieval
- Task creation
- Important negative tests
- Validation errors
- Confirmed bugs


