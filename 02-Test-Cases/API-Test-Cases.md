# API Test Cases

**Project:** MeetMind AI
**Test Type:** REST API Functional Testing
**Environment:** Local Development API
**Base URL:** `http://192.168.0.104:8000/api/v1`
**Tool:** Postman
**Execution Date:** 2026-09-28

---

## Test Execution Summary

| Metric           | Result |
| ---------------- | -----: |
| Total Test Cases |     17 |
| Passed           |     16 |
| Failed           |      1 |
| Blocked          |      0 |
| Not Executed     |      0 |
| Pass Rate        | 94.12% |

**Overall Result:** `FAIL`

> One test case failed: `TC-MEET-005 — Meeting Summary`. The failure has been documented separately as `BUG-MEET-001`.

---

# 1. Authentication

## TC-AUTH-001 — API Health Check

**Method:** GET

**Endpoint:**

```text
/ping
```

**Expected Result:**
HTTP `200 OK` with a valid JSON response.

**Actual Result:**
HTTP `200 OK` with a valid API response.

**Status:** `PASS`

**Evidence:** Optional

---

## TC-AUTH-002 — Valid Login

**Method:** POST

**Endpoint:**

```text
/auth/login
```

**Test Data:**

```json
{
  "email": "sqatest001@example.com",
  "password": "TEST_PASSWORD"
}
```

**Expected Result:**
Successful authentication with HTTP `200 OK` and an `access_token` returned in `data.access_token`.

**Actual Result:**
Login was successful. The API returned the authenticated user information and an access token.

**Status:** `PASS`

**Evidence:** Recommended

> Credentials and access tokens are intentionally not included in this documentation.

---

## TC-AUTH-003 — Authenticated User

**Method:** GET

**Endpoint:**

```text
/auth/me
```

**Header:**

```http
Authorization: Bearer {{token}}
```

**Expected Result:**
HTTP `200 OK` with authenticated user information.

**Actual Result:**
HTTP `200 OK` with the authenticated user's profile information.

**Status:** `PASS`

**Evidence:** Recommended

---

## TC-AUTH-004 — Invalid Login

**Method:** POST

**Endpoint:**

```text
/auth/login
```

**Test Data:**

```json
{
  "email": "sqatest001@example.com",
  "password": "WRONG_PASSWORD"
}
```

**Expected Result:**
Authentication should be rejected with an appropriate HTTP `4xx` response.

**Actual Result:**
Invalid credentials were rejected by the API.

**Status:** `PASS`

**Evidence:** Recommended

---

## TC-AUTH-005 — Protected Endpoint Without Token

**Method:** GET

**Endpoint:**

```text
/auth/me
```

**Expected Result:**
Request should be rejected because authentication credentials are missing.

**Actual Result:**
The protected endpoint rejected the unauthenticated request.

**Status:** `PASS`

**Evidence:** Recommended

---

# 2. Workspaces

## TC-WS-001 — Get Workspaces

**Method:** GET

**Endpoint:**

```text
/workspaces
```

**Expected Result:**
HTTP `200 OK` and accessible workspaces should be returned.

**Actual Result:**
HTTP `200 OK` and the user's accessible workspaces were returned successfully.

**Status:** `PASS`

---

## TC-WS-002 — Create Workspace

**Method:** POST

**Endpoint:**

```text
/workspaces
```

**Request Body:**

```json
{
  "name": "SQA Test Workspace",
  "description": "Workspace created for API testing"
}
```

**Expected Result:**
A new workspace should be created successfully.

**Actual Result:**
Workspace was created successfully and the API returned the created workspace information.

**Status:** `PASS`

**Evidence:** Recommended

---

## TC-WS-003 — Workspace Analytics

**Method:** GET

**Endpoint:**

```text
/workspaces/{workspace}/analytics
```

**Expected Result:**
Workspace analytics should be returned successfully.

**Actual Result:**
Workspace analytics were returned successfully.

**Status:** `PASS`

---

# 3. Meetings

## TC-MEET-001 — Get Meetings

**Method:** GET

**Endpoint:**

```text
/meetings
```

**Expected Result:**
HTTP `200 OK` and accessible meetings should be returned.

**Actual Result:**
HTTP `200 OK` and accessible meetings were returned successfully.

**Status:** `PASS`

---

## TC-MEET-002 — Create Meeting

**Method:** POST

**Endpoint:**

```text
/meetings
```

**Expected Result:**
A meeting should be created successfully using a valid meeting payload.

**Actual Result:**
Meeting was created successfully and the API returned the created meeting information.

**Status:** `PASS`

**Evidence:** Recommended

---

## TC-MEET-003 — Get Meeting

**Method:** GET

**Endpoint:**

```text
/meetings/{meeting}
```

**Expected Result:**
Details of the selected meeting should be returned.

**Actual Result:**
The selected meeting details were returned successfully.

**Status:** `PASS`

**Evidence:** Recommended

---

## TC-MEET-004 — Update Meeting Status

**Method:** PATCH

**Endpoint:**

```text
/meetings/{meeting}/status
```

**Expected Result:**
Meeting status should be updated successfully.

**Actual Result:**
Meeting status was updated successfully and the API returned the updated meeting information.

**Status:** `PASS`

---

## TC-MEET-005 — Meeting Summary

**Method:** GET

**Endpoint:**

```text
/meetings/{meeting}/summary
```

**Precondition:**

* Meeting exists.
* Meeting transcript has been processed.
* AI processing has completed.

**Expected Result:**
HTTP `200 OK` with the generated meeting summary.

**Actual Result:**
The endpoint returned HTTP `404 Not Found` instead of the generated meeting summary.

**Status:** `FAIL`

**Bug:** `BUG-MEET-001`

**Severity:** `High`

**Priority:** `P1`

**Evidence:** Required

---

# 4. Tasks

## TC-TASK-001 — Get Tasks

**Method:** GET

**Endpoint:**

```text
/tasks
```

**Expected Result:**
HTTP `200 OK` and accessible tasks should be returned.

**Actual Result:**
HTTP `200 OK` and accessible tasks were returned successfully.

**Status:** `PASS`

---

## TC-TASK-002 — Create Task

**Method:** POST

**Endpoint:**

```text
/tasks
```

**Expected Result:**
A task should be created successfully using a valid task payload.

**Actual Result:**
Task was created successfully and the API returned the created task information.

**Status:** `PASS`

**Evidence:** Recommended

---

# 5. Negative Testing

## TC-NEG-001 — Invalid Meeting ID

**Method:** GET

**Endpoint:**

```text
/meetings/999999999
```

**Expected Result:**
The API should return an appropriate `4xx` not-found response and should not produce an unhandled server error.

**Actual Result:**
The API correctly handled the invalid meeting ID with an appropriate error response.

**Status:** `PASS`

**Evidence:** Recommended

---

## TC-NEG-002 — Missing Required Login Field

**Method:** POST

**Endpoint:**

```text
/auth/login
```

**Request Body:**

```json
{
  "email": "sqatest001@example.com"
}
```

**Expected Result:**
The API should return a validation error with an appropriate HTTP `4xx` response.

**Actual Result:**
The API correctly rejected the request because the required password field was missing and returned a validation error.

**Status:** `PASS`

**Evidence:** Recommended

---

# Test Case Summary

| Test Case   | Description                      | Status   |
| ----------- | -------------------------------- | -------- |
| TC-AUTH-001 | API Health Check                 | PASS     |
| TC-AUTH-002 | Valid Login                      | PASS     |
| TC-AUTH-003 | Authenticated User               | PASS     |
| TC-AUTH-004 | Invalid Login                    | PASS     |
| TC-AUTH-005 | Protected Endpoint Without Token | PASS     |
| TC-WS-001   | Get Workspaces                   | PASS     |
| TC-WS-002   | Create Workspace                 | PASS     |
| TC-WS-003   | Workspace Analytics              | PASS     |
| TC-MEET-001 | Get Meetings                     | PASS     |
| TC-MEET-002 | Create Meeting                   | PASS     |
| TC-MEET-003 | Get Meeting                      | PASS     |
| TC-MEET-004 | Update Meeting Status            | PASS     |
| TC-MEET-005 | Meeting Summary                  | **FAIL** |
| TC-TASK-001 | Get Tasks                        | PASS     |
| TC-TASK-002 | Create Task                      | PASS     |
| TC-NEG-001  | Invalid Meeting ID               | PASS     |
| TC-NEG-002  | Missing Required Login Field     | PASS     |

---

# Defect Summary

| Bug ID       | Test Case   | Issue                                           | Severity | Priority | Status |
| ------------ | ----------- | ----------------------------------------------- | -------- | -------- | ------ |
| BUG-MEET-001 | TC-MEET-005 | Meeting Summary returns 404 after AI processing | High     | P1       | Open   |

---

# Final Test Result

**Total Test Cases:** 17

**Passed:** 16

**Failed:** 1

**Blocked:** 0

**Pass Rate:** 94.12%

**Overall Status:** `FAIL`

The API demonstrated successful functionality across authentication, workspace management, meeting management, task management, and negative validation scenarios. However, the Meeting Summary endpoint failed to return the generated summary after AI processing completed. This defect is documented as `BUG-MEET-001` and requires resolution and subsequent retesting.
